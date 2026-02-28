---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis (dual view)
---
<div class="thesis-fullbleed">
<style>
  .thesis-wrap{
    max-width: none;          /* IMPORTANT */
    width: min(1400px, 96vw); /* la largeur réelle */
    margin: 0 auto;
    padding:10px 0 30px;
  }
  .thesis-topbar{
    display:flex; align-items:center; justify-content:space-between;
    gap:12px; flex-wrap:wrap; margin:10px 0 14px;
  }
  .thesis-title{margin:0}
  .view-switch{
    display:flex; gap:8px; align-items:center; flex-wrap:wrap;
  }
  .viewbtn{
    display:inline-flex; align-items:center; justify-content:center; gap:8px;
    padding:8px 10px; border-radius:12px;
    border:1px solid rgba(0,0,0,.12);
    background:rgba(255,255,255,.85);
    cursor:pointer; user-select:none;
    font-weight:700; font-size:13px;
  }
  .viewbtn.active{
    border-color: rgba(31, 75, 153, .55);
    background: rgba(31, 75, 153, .10);
    color:#1f4b99;
  }
  .hint{
    font-size:13px;
    color:rgba(0,0,0,.55);
    margin:0;
  }
  
  .panel{display:none}
  .panel.active{display:block}

  /* Scroll viewer */
  
  .pdf-zoom-wrap{
    width:100%;
    height:min(85vh, 920px);
    border-radius:16px;
    overflow:auto;                 /* IMPORTANT: scroll */
    box-shadow:0 12px 40px rgba(0,0,0,.10);
    background:#1f1f1f;
  }
  
  .pdf-frame{
    width:100%;
    height:100%;
    border:0;
    background:#fff;
    transform-origin: top center;  /* IMPORTANT */
  }

  /* Book viewer container */
  #book{
    width:100%;
    height:min(78vh, 720px);
    border-radius:16px;
    overflow:hidden;
    background:rgba(255,255,255,.75);
    border:1px solid rgba(0,0,0,.08);
    box-shadow:0 12px 40px rgba(0,0,0,.10);
  }
  .bookbar{
    display:flex; gap:10px; align-items:center; justify-content:space-between;
    margin:10px 0 12px; flex-wrap:wrap;
  }
  .bookbtn{
    display:inline-flex; align-items:center; justify-content:center; gap:8px;
    padding:9px 12px; border-radius:12px;
    border:1px solid rgba(0,0,0,.12);
    background:rgba(255,255,255,.85);
    color:rgba(0,0,0,.82);
    font-weight:700; cursor:pointer; user-select:none;
  }
  .bookbtn:hover{transform:translateY(-1px); box-shadow:0 10px 22px rgba(0,0,0,.10)}
  .scrollbar{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    flex-wrap:wrap;
    margin: 0 0 10px 0;
  }
  
  .scroll-zoom{
    display:flex;
    align-items:center;
    gap:8px;
  }

</style>

<div class="thesis-wrap">

  <div class="thesis-topbar">
    <div>
      <h1 class="thesis-title">PhD Thesis</h1>
      <p class="hint" id="netHint"></p>
    </div>

    <div class="view-switch" aria-label="View mode">
      <button class="viewbtn active" id="btnBook" type="button">Book view</button>
      <button class="viewbtn" id="btnScroll" type="button">Scroll view</button>
    </div>
  </div>

  <!-- BOOK PANEL -->
  <section class="panel active" id="panelBook">
    <p class="hint">Two-page spread. Use zoom if text looks small.</p>

    <div class="bookbar">
      <div style="display:flex; gap:10px; align-items:center; flex-wrap:wrap;">
        <button class="bookbtn" id="prevBtn" type="button">← Prev</button>
        <button class="bookbtn" id="nextBtn" type="button">Next →</button>
        <button class="bookbtn" id="zoomIn" type="button">＋ Zoom</button>
        <button class="bookbtn" id="zoomOut" type="button">－ Zoom</button>
      </div>
      <div class="hint" id="status">Loading…</div>
    </div>

    <div id="book"></div>

  </section>


  <!-- SCROLL PANEL -->
  <section class="panel" id="panelScroll">
    <div class="scrollbar">
      <p class="hint" style="margin:0;">Fast vertical scroll (lighter).</p>
  
      <div class="scroll-zoom">
        <button class="bookbtn" id="sZoomOut" type="button">－</button>
        <div class="hint" id="sZoomLabel">100%</div>
        <button class="bookbtn" id="sZoomIn" type="button">＋</button>
      </div>
    </div>
  
    <div class="pdf-zoom-wrap" id="scrollWrap">
      <iframe
        class="pdf-frame"
        id="scrollFrame"
        src="{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}#view=FitH&toolbar=0&navpanes=0&scrollbar=1"
        loading="lazy">
      </iframe>
    </div>
    
  </section>

</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script>
  const PDF_URL = "{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}";

  // ---------- View toggle ----------
  const btnBook = document.getElementById("btnBook");
  const btnScroll = document.getElementById("btnScroll");
  const panelBook = document.getElementById("panelBook");
  const panelScroll = document.getElementById("panelScroll");

  function setActiveView(mode){
    const isBook = mode === "book";
    btnBook.classList.toggle("active", isBook);
    btnScroll.classList.toggle("active", !isBook);
    panelBook.classList.toggle("active", isBook);
    panelScroll.classList.toggle("active", !isBook);
    localStorage.setItem("thesis_view_mode", mode);
  }

  btnBook.addEventListener("click", () => setActiveView("book"));
  btnScroll.addEventListener("click", () => setActiveView("scroll"));

  // Default: book, but restore last choice
  const saved = localStorage.getItem("thesis_view_mode");
  if (saved === "scroll") setActiveView("scroll");

   // ---------- SCROLL VIEW: light zoom (iframe hash) ----------
  const scrollFrame = document.getElementById("scrollFrame");
  const sZoomIn = document.getElementById("sZoomIn");
  const sZoomOut = document.getElementById("sZoomOut");
  const sZoomLabel = document.getElementById("sZoomLabel");
  
  // let scrollZoom = 100;
  
  let scrollZoom = 1; // 1 = 100%
  
  function setScrollZoom(z){
    scrollZoom = Math.max(0.7, Math.min(1.8, z)); // 70%..180%
    if (sZoomLabel) sZoomLabel.textContent = `${Math.round(scrollZoom*100)}%`;
  
    // scale iframe
    scrollFrame.style.transform = `scale(${scrollZoom})`;
  
    // garder la largeur visible (sinon ça “rentre”)
    scrollFrame.style.width = `${100/scrollZoom}%`;
    scrollFrame.style.height = `${100/scrollZoom}%`;
  }
  
  sZoomIn.addEventListener("click", () => setScrollZoom(scrollZoom + 0.1));
  sZoomOut.addEventListener("click", () => setScrollZoom(scrollZoom - 0.1));
  setScrollZoom(1);
    
  
  
  // ---------- Light network hint (optional) ----------
  const netHint = document.getElementById("netHint");
  try{
    const c = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
    if (c && (c.effectiveType || c.downlink)){
      const t = c.effectiveType ? `Network: ${c.effectiveType}` : "";
      const d = c.downlink ? `~${c.downlink}Mbps` : "";
      const msg = [t,d].filter(Boolean).join(" ");
      netHint.textContent = msg ? msg + " • If loading is slow, switch to Scroll view." : "";
    } else {
      netHint.textContent = "";
    }
  } catch(e){ netHint.textContent = ""; }

  // ---------- BOOK VIEW (PDF.js 2-page spread) ----------
  const pdfjsLib = window.pdfjsLib;
  pdfjsLib.GlobalWorkerOptions.workerSrc =
    "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

  const statusEl = document.getElementById("status");
  const bookEl = document.getElementById("book");

  let pdfDoc = null;
  let currentScale = 1.25;
  let leftPage = 1;
  const cache = new Map();
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
      <div style="height:100%;display:grid;grid-template-columns:1fr 1fr;background:rgba(255,255,255,0.75);">
        <div id="L" style="border-right:1px solid rgba(0,0,0,0.06);display:flex;align-items:center;justify-content:center;"></div>
        <div id="R" style="display:flex;align-items:center;justify-content:center;"></div>
      </div>`;
  }
  function spinner(){ return `<div style="opacity:.55;font-weight:700;">Loading…</div>`; }

  async function showSpread(){
    if (busy) return;
    busy = true;

    leftPage = clamp(leftPage, 1, pdfDoc.numPages);
    const rightPage = clamp(leftPage + 1, 1, pdfDoc.numPages);

    makeSpreadShell();
    function makeSpreadShell(){
      bookEl.innerHTML = `
        <div style="height:100%;display:grid;grid-template-columns:1fr 1fr;gap:0;background:rgba(255,255,255,0.75);">
          <div id="L" style="border-right:1px solid rgba(0,0,0,0.06);display:flex;align-items:center;justify-content:center;padding:10px;"></div>
          <div id="R" style="display:flex;align-items:center;justify-content:center;padding:10px;"></div>
        </div>`;
    }
    const L = document.getElementById("L");
    const R = document.getElementById("R");

    L.innerHTML = spinner();
    R.innerHTML = spinner();
    setStatus(`Loading pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

    try{
      const leftUrl = await renderPageToDataURL(leftPage, currentScale);
      L.innerHTML = `<img alt="p${leftPage}" src="${leftUrl}" style="width:100%;height:auto;display:block;border-radius:8px;object-fit:contain;"/>`;

      if (rightPage !== leftPage){
        const rightUrl = await renderPageToDataURL(rightPage, currentScale);
        R.innerHTML = `<img alt="p${rightPage}" src="${rightUrl}" style="width:100%;height:auto;display:block;border-radius:8px;object-fit:contain;"/>`;
      } else {
        R.innerHTML = "";
      }

      setStatus(`Ready • pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

      // prefetch next spread (best-effort)
      const nextL = leftPage + 2, nextR = leftPage + 3;
      if (nextL <= pdfDoc.numPages) renderPageToDataURL(nextL, currentScale).catch(()=>{});
      if (nextR <= pdfDoc.numPages) renderPageToDataURL(nextR, currentScale).catch(()=>{});

    } catch(e){
      console.error(e);
      setStatus("Error rendering pages. Switch to Scroll view.");
      L.innerHTML = `<div style="color:#b00020;font-weight:700;">Render error</div>`;
      R.innerHTML = "";
    } finally {
      busy = false;
    }
  }

  async function initBook(){
    setStatus("Loading PDF…");
    // If you ever get worker issues again, you can force disableWorker:true:
    // pdfDoc = await pdfjsLib.getDocument({ url: PDF_URL, disableWorker: true }).promise;
    pdfDoc = await pdfjsLib.getDocument(PDF_URL).promise;

    leftPage = 1;
    cache.clear();

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

  // Load book viewer only once (and keep it ready even if user switches tabs)
  initBook().catch(err => {
    console.error(err);
    setStatus("Error loading PDF. Switch to Scroll view.");
  });
</script>
</div>
