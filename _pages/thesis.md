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

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/page-flip@2.0.7/dist/js/page-flip.browser.min.js"></script>

<script>
  const PDF_URL = "{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}";

  const pdfjsLib = window['pdfjs-dist/build/pdf'];
  pdfjsLib.GlobalWorkerOptions.workerSrc =
    "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

  const statusEl = document.getElementById("status");
  const bookEl = document.getElementById("book");

  let flip = null;
  let currentScale = 1.15;
  let pdfDoc = null;

  function setStatus(txt){ statusEl.textContent = txt; }

  async function renderAllPagesToImages(pdf, scale){
    const images = [];
    for (let p = 1; p <= pdf.numPages; p++){
      setStatus(`Rendering: ${p}/${pdf.numPages}`);
      const page = await pdf.getPage(p);
      const viewport = page.getViewport({ scale });

      const canvas = document.createElement("canvas");
      const ctx = canvas.getContext("2d");
      canvas.width = Math.floor(viewport.width);
      canvas.height = Math.floor(viewport.height);

      await page.render({ canvasContext: ctx, viewport }).promise;

      const img = document.createElement("img");
      img.src = canvas.toDataURL("image/jpeg", 0.92);
      img.style.width = "100%";
      img.style.height = "100%";
      img.draggable = false;

      images.push(img);
    }
    return images;
  }

  function destroyFlip(){
    if (flip){
      try { flip.destroy(); } catch(e){}
      flip = null;
    }
    bookEl.innerHTML = "";
  }

  async function buildFlipbook(scale){
    destroyFlip();
    setStatus("Loading PDF…");
    pdfDoc = await pdfjsLib.getDocument(PDF_URL).promise;

    setStatus("Preparing…");
    const images = await renderAllPagesToImages(pdfDoc, scale);

    flip = new St.PageFlip(bookEl, {
      width: 460,
      height: 650,
      size: "stretch",
      minWidth: 320,
      maxWidth: 1000,
      minHeight: 420,
      maxHeight: 1400,
      maxShadowOpacity: 0.18,
      showCover: false,
      mobileScrollSupport: true,
      useMouseEvents: true
    });

    flip.loadFromImages(images);

    setStatus(`Ready • ${pdfDoc.numPages} pages`);

    document.getElementById("prevBtn").onclick = () => flip.flipPrev();
    document.getElementById("nextBtn").onclick = () => flip.flipNext();

    flip.on("flip", (e) => {
      const p = e.data + 1;
      setStatus(`Page ${p} / ${pdfDoc.numPages}`);
    });
  }

  document.getElementById("zoomIn").onclick = async () => {
    currentScale = Math.min(currentScale + 0.15, 2.0);
    await buildFlipbook(currentScale);
  };
  document.getElementById("zoomOut").onclick = async () => {
    currentScale = Math.max(currentScale - 0.15, 0.85);
    await buildFlipbook(currentScale);
  };

  buildFlipbook(currentScale).catch(err => {
    console.error(err);
    setStatus("Error loading flipbook.");
  });
</script>
