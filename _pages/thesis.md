---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis (book reader)
---

<style>
  #bookWrap{
    width: 100%;
    max-width: 980px;
    margin: 0 auto;
    padding: 10px 0 30px 0;
  }
  #book{
    width: 100%;
    height: min(78vh, 720px);
    border-radius: 16px;
    overflow: hidden;
    background: rgba(255,255,255,0.75);
    border: 1px solid rgba(0,0,0,0.08);
    box-shadow: 0 12px 40px rgba(0,0,0,0.10);
  }
  .bookbar{
    display:flex;
    gap:10px;
    align-items:center;
    justify-content: space-between;
    margin: 10px 0 12px 0;
    flex-wrap: wrap;
  }
  .bookbtn{
    display:inline-flex;
    align-items:center;
    justify-content:center;
    gap:8px;
    padding: 9px 12px;
    border-radius: 12px;
    border: 1px solid rgba(0,0,0,0.12);
    background: rgba(255,255,255,0.85);
    color: rgba(0,0,0,0.82);
    text-decoration:none;
    font-weight: 700;
    cursor:pointer;
    user-select:none;
  }
  .bookbtn:hover{
    transform: translateY(-1px);
    box-shadow: 0 10px 22px rgba(0,0,0,0.10);
  }
  .hint{
    font-size: 13px;
    color: rgba(0,0,0,0.55);
  }
  #book canvas { user-select:none; -webkit-user-select:none; }
</style>

<h1>PhD Thesis (Book View)</h1>
<p class="hint">Flip pages like a book. Use zoom if text looks small.</p>

<div id="bookWrap">
  <div class="bookbar">
    <div style="display:flex; gap:10px; align-items:center; flex-wrap:wrap;">
      <button class="bookbtn" id="prevBtn">← Prev</button>
      <button class="bookbtn" id="nextBtn">Next →</button>
      <button class="bookbtn" id="zoomIn">＋ Zoom</button>
      <button class="bookbtn" id="zoomOut">－ Zoom</button>
    </div>

    <div class="hint" id="status">Loading…</div>
  </div>

  <div id="book"></div>

  <p class="hint" style="margin-top:10px;">
    Tip: drag a page corner to flip.
  </p>

  <p class="hint">
    <a href="{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}" target="_blank" rel="noopener">
      Open the original PDF
    </a>
  </p>
</div>


<script src="https://cdn.jsdelivr.net/npm/page-flip@2.0.7/dist/js/page-flip.browser.min.js"></script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script>
  const PDF_URL = "{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}";

  const pdfjsLib = window['pdfjs-dist/build/pdf'];
  pdfjsLib.GlobalWorkerOptions.workerSrc =
    "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

  const statusEl = document.getElementById("status");
  const bookEl = document.getElementById("book");

  let pdfDoc = null;
  let currentScale = 1.25;
  let leftPage = 1; // left page number (odd usually)
  const cache = new Map(); // pageNumber -> dataURL
  let busy = false;

  function setStatus(txt){ statusEl.textContent = txt; }

  function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }

  async function renderPageToDataURL(pageNumber, scale){
    const key = `${pageNumber}@${scale}`;
    if (cache.has(key)) return cache.get(key);

    const page = await pdfDoc.getPage(pageNumber);
    const viewport = page.getViewport({ scale });

    const canvas = document.createElement("canvas");
    const ctx = canvas.getContext("2d", { alpha: false });

    canvas.width = Math.floor(viewport.width);
    canvas.height = Math.floor(viewport.height);

    await page.render({ canvasContext: ctx, viewport }).promise;

    const url = canvas.toDataURL("image/jpeg", 0.90);
    cache.set(key, url);
    return url;
  }

  function makeSpreadShell(){
    bookEl.innerHTML = `
      <div style="
        height:100%;
        display:grid;
        grid-template-columns:1fr 1fr;
        gap:0;
        align-items:stretch;
        background: rgba(255,255,255,0.75);
      ">
        <div id="L" style="border-right:1px solid rgba(0,0,0,0.06); display:flex; align-items:center; justify-content:center;"></div>
        <div id="R" style="display:flex; align-items:center; justify-content:center;"></div>
      </div>
    `;
  }

  function spinner(){
    return `<div style="opacity:.55; font-weight:700;">Loading…</div>`;
  }

  async function showSpread(){
    if (busy) return;
    busy = true;

    leftPage = clamp(leftPage, 1, pdfDoc.numPages);
    const rightPage = clamp(leftPage + 1, 1, pdfDoc.numPages);

    makeSpreadShell();
    const L = document.getElementById("L");
    const R = document.getElementById("R");

    L.innerHTML = spinner();
    R.innerHTML = spinner();

    setStatus(`Loading pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

    try{
      // render left then right (fast perceived)
      const leftUrl = await renderPageToDataURL(leftPage, currentScale);
      L.innerHTML = `<img alt="p${leftPage}" src="${leftUrl}" style="max-width:100%; max-height:100%; display:block; border-radius:8px;"/>`;

      if (rightPage !== leftPage){
        const rightUrl = await renderPageToDataURL(rightPage, currentScale);
        R.innerHTML = `<img alt="p${rightPage}" src="${rightUrl}" style="max-width:100%; max-height:100%; display:block; border-radius:8px;"/>`;
      } else {
        R.innerHTML = "";
      }

      setStatus(`Ready • pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

      // prefetch next spread in background
      const nextL = leftPage + 2;
      const nextR = leftPage + 3;
      if (nextL <= pdfDoc.numPages) renderPageToDataURL(nextL, currentScale).catch(()=>{});
      if (nextR <= pdfDoc.numPages) renderPageToDataURL(nextR, currentScale).catch(()=>{});

    } catch(e){
      console.error(e);
      setStatus("Error rendering pages.");
      L.innerHTML = `<div style="color:#b00020; font-weight:700;">Render error</div>`;
      R.innerHTML = "";
    } finally {
      busy = false;
    }
  }

  async function init(){
    setStatus("Loading PDF…");
    pdfDoc = await pdfjsLib.getDocument(PDF_URL).promise;

    // start at 1 (left) so spread is 1-2
    leftPage = 1;
    cache.clear();

    // wire buttons
    document.getElementById("prevBtn").onclick = async () => {
      leftPage = clamp(leftPage - 2, 1, pdfDoc.numPages);
      await showSpread();
    };
    document.getElementById("nextBtn").onclick = async () => {
      leftPage = clamp(leftPage + 2, 1, pdfDoc.numPages);
      await showSpread();
    };
    document.getElementById("zoomIn").onclick = async () => {
      currentScale = clamp(currentScale + 0.15, 0.9, 2.0);
      cache.clear();
      await showSpread();
    };
    document.getElementById("zoomOut").onclick = async () => {
      currentScale = clamp(currentScale - 0.15, 0.9, 2.0);
      cache.clear();
      await showSpread();
    };

    await showSpread();
  }

  init().catch(err => {
    console.error(err);
    setStatus("Error loading PDF.");
  });
</script>
