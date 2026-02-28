---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis (dual view)
---

<div class="thesis-fullbleed">

  <style>
    /* --- Full-bleed WITHOUT touching al-folio template --- */
    .thesis-fullbleed{ width:100%; }

    .thesis-wrap{
      width: min(1400px, 96vw);
      margin: 0 auto;
      padding: 10px 0 30px;
    }

    .thesis-topbar{
      display:flex;
      align-items:flex-end;
      justify-content:space-between;
      gap:12px;
      flex-wrap:wrap;
      margin: 10px 0 14px;
    }
    .thesis-title{ margin:0; }

    .hint{
      font-size:13px;
      color: rgba(0,0,0,.55);
      margin: 0;
    }

    .view-switch{
      display:flex;
      gap:8px;
      align-items:center;
      flex-wrap:wrap;
    }

    .viewbtn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:8px 10px;
      border-radius:12px;
      border:1px solid rgba(0,0,0,.12);
      background: rgba(255,255,255,.85);
      cursor:pointer;
      user-select:none;
      font-weight:700;
      font-size:13px;
      line-height:1;
    }
    .viewbtn.active{
      border-color: rgba(31, 75, 153, .55);
      background: rgba(31, 75, 153, .10);
      color:#1f4b99;
    }

    .panel{ display:none; }
    .panel.active{ display:block; }

    /* --- Book viewer --- */
    .bookbar{
      display:flex;
      gap:10px;
      align-items:center;
      justify-content:space-between;
      margin: 10px 0 12px;
      flex-wrap:wrap;
    }

    .bookbtn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:9px 12px;
      border-radius:12px;
      border:1px solid rgba(0,0,0,.12);
      background: rgba(255,255,255,.85);
      color: rgba(0,0,0,.82);
      font-weight:700;
      cursor:pointer;
      user-select:none;
      line-height:1;
      text-decoration:none;
    }
    .bookbtn:hover{
      transform: translateY(-1px);
      box-shadow: 0 10px 22px rgba(0,0,0,.10);
    }

    #book{
      width:100%;
      height: min(82vh, 860px);
      border-radius:16px;
      overflow:auto; /* IMPORTANT: zoom won't cut, you can pan */
      background: rgba(255,255,255,.75);
      border: 1px solid rgba(0,0,0,.08);
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
    }

    .spread{
      height: 100%;
      min-height: 520px;
      display:grid;
      grid-template-columns: 1fr 1fr;
      background: rgba(255,255,255,0.75);
    }

    .pageSlot{
      display:flex;
      align-items:center;
      justify-content:center;
      padding: 12px;
      box-sizing: border-box;
    }

    .pageSlot.left{
      border-right: 1px solid rgba(0,0,0,0.06);
    }

    .pageSlot img{
      max-width: 100%;
      max-height: 100%;
      width: auto;
      height: auto;
      display:block;
      border-radius: 8px;
      object-fit: contain;
    }

    /* Small screens: single page */
    @media (max-width: 900px){
      .spread{ grid-template-columns: 1fr; }
      .pageSlot.left{ border-right: none; border-bottom: 1px solid rgba(0,0,0,0.06); }
    }

    /* --- Scroll viewer (PDF.js progressive render) --- */
    .scrollpdf{
      width:100%;
      height: min(88vh, 920px);
      overflow:auto;
      border-radius:16px;
      background:#f6f7f9;
      border: 1px solid rgba(0,0,0,.08);
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
      padding: 14px 0;
    }
    .scrollpdf .pdfpage{
      display:flex;
      justify-content:center;
      padding: 10px 0;
    }
    .scrollpdf canvas{
      background:#fff;
      border-radius:10px;
      box-shadow: 0 10px 24px rgba(0,0,0,.10);
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
      <p class="hint">Two-page spread. Zoom increases readability; scroll inside the viewer to pan.</p>

      <div class="bookbar">
        <div style="display:flex; gap:10px; align-items:center; flex-wrap:wrap;">
          <button class="bookbtn" id="prevBtn" type="button">← Prev</button>
          <button class="bookbtn" id="nextBtn" type="button">Next →</button>
          <button class="bookbtn" id="zoomIn" type="button">＋ Zoom</button>
          <button class="bookbtn" id="zoomOut" type="button">－ Zoom</button>
        </div>
        <div class="hint" id="status">Loading…</div>
      </div>

      <div id="book">
        <div class="spread">
          <div class="pageSlot left" id="L"><span class="hint">Loading…</span></div>
          <div class="pageSlot" id="R"><span class="hint">Loading…</span></div>
        </div>
      </div>
    </section>

    <!-- SCROLL PANEL -->
    <section class="panel" id="panelScroll">
      <p class="hint">Fast scroll (PDF.js). Pages render progressively as you scroll.</p>

      <div id="scrollPdf" class="scrollpdf">
        <div class="pdfpage"><span class="hint">Loading…</span></div>
      </div>

      <div style="margin-top:10px;">
        <a class="bookbtn"
           href="{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}"
           target="_blank" rel="noopener">
          Open fullscreen
        </a>
      </div>
    </section>

  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
  <script>
    const PDF_URL = "{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}";

    // ---------- View toggle (default: BOOK) ----------
    const btnBook = document.getElementById("btnBook");
    const btnScroll = document.getElementById("btnScroll");
    const panelBook = document.getElementById("panelBook");
    const panelScroll = document.getElementById("panelScroll");

    // Always open on BOOK first load; only switch if user explicitly saved scroll
    function setActiveView(mode, persist=true){
      const isBook = mode === "book";
      btnBook.classList.toggle("active", isBook);
      btnScroll.classList.toggle("active", !isBook);
      panelBook.classList.toggle("active", isBook);
      panelScroll.classList.toggle("active", !isBook);
      if (persist){
        try { localStorage.setItem("thesis_view_mode", mode); } catch(e){}
      }
    }

    btnBook.addEventListener("click", () => setActiveView("book"));
    btnScroll.addEventListener("click", () => setActiveView("scroll"));

    // Default book. If you want to ignore saved mode forever, comment this block.
    try {
      const saved = localStorage.getItem("thesis_view_mode");
      if (saved === "scroll") setActiveView("scroll", false);
    } catch(e){}

    // ---------- Light network hint ----------
    const netHint = document.getElementById("netHint");
    try{
      const c = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
      if (c && (c.effectiveType || c.downlink)){
        const t = c.effectiveType ? `Network: ${c.effectiveType}` : "";
        const d = c.downlink ? `~${c.downlink}Mbps` : "";
        const msg = [t,d].filter(Boolean).join(" ");
        netHint.textContent = msg ? (msg + " • If loading is slow, switch to Scroll view.") : "";
      }
    } catch(e){}

    // ---------- PDF.js setup ----------
    const pdfjsLib = window.pdfjsLib;
    pdfjsLib.GlobalWorkerOptions.workerSrc =
      "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

    function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }

    // ---------- BOOK VIEW (2-page spread) ----------
    const statusEl = document.getElementById("status");
    const L = document.getElementById("L");
    const R = document.getElementById("R");

    let pdfDoc = null;
    let currentScale = 1.15; // initial render scale
    let leftPage = 1;
    let busy = false;

    function setStatus(txt){ statusEl.textContent = txt; }
    function spinner(){ return '<span class="hint" style="font-weight:700;opacity:.65;">Loading…</span>'; }

    async function renderPageToDataURL(pageNumber, scale){
      const page = await pdfDoc.getPage(pageNumber);
      const viewport = page.getViewport({ scale });

      const canvas = document.createElement("canvas");
      const ctx = canvas.getContext("2d", { alpha: false });

      canvas.width = Math.floor(viewport.width);
      canvas.height = Math.floor(viewport.height);

      await page.render({ canvasContext: ctx, viewport }).promise;
      return canvas.toDataURL("image/jpeg", 0.90);
    }

    async function showSpread(){
      if (!pdfDoc || busy) return;
      busy = true;

      leftPage = clamp(leftPage, 1, pdfDoc.numPages);
      let rightPage = leftPage + 1;

      const single = window.matchMedia && window.matchMedia("(max-width: 900px)").matches;
      if (single) rightPage = leftPage;
      rightPage = clamp(rightPage, 1, pdfDoc.numPages);

      L.innerHTML = spinner();
      R.innerHTML = spinner();
      setStatus(`Loading pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

      try{
        const leftUrl = await renderPageToDataURL(leftPage, currentScale);
        L.innerHTML = `<img alt="p${leftPage}" src="${leftUrl}">`;

        if (rightPage !== leftPage){
          const rightUrl = await renderPageToDataURL(rightPage, currentScale);
          R.innerHTML = `<img alt="p${rightPage}" src="${rightUrl}">`;
        } else {
          R.innerHTML = "";
        }

        setStatus(`Ready • pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);
      } catch(e){
        console.error(e);
        setStatus("Error rendering pages. Switch to Scroll view.");
        L.innerHTML = '<span class="hint" style="color:#b00020;font-weight:700;">Render error</span>';
        R.innerHTML = "";
      } finally {
        busy = false;
      }
    }

    async function initBook(){
      setStatus("Loading PDF…");
      pdfDoc = await pdfjsLib.getDocument(PDF_URL).promise;

      leftPage = 1;

      document.getElementById("prevBtn").onclick = async () => {
        leftPage = clamp(leftPage - 2, 1, pdfDoc.numPages);
        await showSpread();
      };

      document.getElementById("nextBtn").onclick = async () => {
        leftPage = clamp(leftPage + 2, 1, pdfDoc.numPages);
        await showSpread();
      };

      document.getElementById("zoomIn").onclick = async () => {
        currentScale = clamp(currentScale + 0.15, 0.85, 2.0);
        await showSpread();
      };

      document.getElementById("zoomOut").onclick = async () => {
        currentScale = clamp(currentScale - 0.15, 0.85, 2.0);
        await showSpread();
      };

      window.addEventListener("resize", () => {
        if (busy) return;
        showSpread();
      });

      await showSpread();
    }

    // ---------- SCROLL VIEW (PDF.js progressive render) ----------
    const scrollHost = document.getElementById("scrollPdf");
    let scrollDoc = null;
    let scrollRendering = new Set();
    let scrollPageCanvases = [];
    let scrollScale = 1;
    let scrollInited = false;

    function clearScrollView(){
      scrollHost.innerHTML = "";
      scrollRendering.clear();
      scrollPageCanvases = [];
    }

    async function computeScrollFitScale(page){
      const containerW = (scrollHost.clientWidth || 900) - 40; // margins
      const vp1 = page.getViewport({ scale: 1 });
      const s = containerW / vp1.width;
      scrollScale = clamp(s, 0.6, 1.8);
    }

    function makePageShell(pageNum){
      const wrap = document.createElement("div");
      wrap.className = "pdfpage";
      wrap.dataset.page = String(pageNum);

      const canvas = document.createElement("canvas");
      canvas.width = 10;
      canvas.height = 10;

      wrap.appendChild(canvas);
      scrollHost.appendChild(wrap);
      return canvas;
    }

    async function renderScrollPage(pageNum){
      if (!scrollDoc) return;
      if (scrollRendering.has(pageNum)) return;
      scrollRendering.add(pageNum);

      try{
        const page = await scrollDoc.getPage(pageNum);
        const viewport = page.getViewport({ scale: scrollScale });

        const canvas = scrollPageCanvases[pageNum];
        if (!canvas) return;

        const ctx = canvas.getContext("2d", { alpha: false });
        canvas.width = Math.floor(viewport.width);
        canvas.height = Math.floor(viewport.height);

        await page.render({ canvasContext: ctx, viewport }).promise;
      } catch(e){
        console.error(e);
      } finally{
        scrollRendering.delete(pageNum);
      }
    }

    function setupScrollObserver(){
      const root = scrollHost;
      const obs = new IntersectionObserver((entries) => {
        for (const ent of entries){
          if (ent.isIntersecting){
            const pageNum = Number(ent.target.dataset.page);
            renderScrollPage(pageNum);
          }
        }
      }, { root, rootMargin: "900px 0px", threshold: 0.01 });

      root.querySelectorAll(".pdfpage").forEach(el => obs.observe(el));
      return obs;
    }

    let scrollObs = null;

    async function initScrollPdf(){
      if (!scrollHost || scrollInited) return;

      clearScrollView();

      // Reuse already loaded doc if possible (fast)
      scrollDoc = pdfDoc || await pdfjsLib.getDocument(PDF_URL).promise;

      const p1 = await scrollDoc.getPage(1);
      await computeScrollFitScale(p1);

      const n = scrollDoc.numPages;
      scrollPageCanvases = new Array(n + 1);
      for (let i = 1; i <= n; i++){
        scrollPageCanvases[i] = makePageShell(i);
      }

      // Render first page immediately
      await renderScrollPage(1);

      // Observe the rest
      scrollObs = setupScrollObserver();
      scrollInited = true;
    }

    // Init scroll only when user opens scroll tab (keeps first paint fast)
    btnScroll.addEventListener("click", () => {
      setActiveView("scroll");
      setTimeout(() => { initScrollPdf().catch(console.error); }, 50);
    });

    // If the page loads with scroll active (saved), initialize it
    (function(){
      const isScrollActive = panelScroll.classList.contains("active");
      if (isScrollActive){
        setTimeout(() => { initScrollPdf().catch(console.error); }, 50);
      }
    })();

    // ---------- boot ----------
    initBook().catch(err => {
      console.error(err);
      setStatus("Error loading PDF. Switch to Scroll view.");
    });

    // Optional: refit scroll pages on resize (kept light)
    let resizeT = null;
    window.addEventListener("resize", () => {
      if (!scrollInited) return;
      clearTimeout(resizeT);
      resizeT = setTimeout(async () => {
        try{
          const p1 = await scrollDoc.getPage(1);
          await computeScrollFitScale(p1);

          // Re-render only visible pages soon; simplest: clear and re-init
          if (scrollObs) scrollObs.disconnect();
          scrollInited = false;
          await initScrollPdf();
        } catch(e){ console.error(e); }
      }, 250);
    });
  </script>

</div>
