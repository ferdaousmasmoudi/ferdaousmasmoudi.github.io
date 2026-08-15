---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis in English and French with book and scroll views
---

<div class="thesis-fullbleed">

  <style>
    .thesis-fullbleed{ width:100%; }

    .thesis-wrap{
      width:min(1400px, 96vw);
      margin:0 auto;
      padding:10px 0 30px;
    }

    .thesis-topbar{
      display:flex;
      align-items:flex-end;
      justify-content:space-between;
      gap:16px;
      flex-wrap:wrap;
      margin:10px 0 14px;
    }

    .thesis-title{ margin:0; }

    .thesis-doc-title{
      margin:5px 0 0;
      font-size:14px;
      font-weight:600;
      color:rgba(0,0,0,.62);
    }

    .hint{
      font-size:13px;
      color:rgba(0,0,0,.55);
      margin:0;
    }

    .thesis-controls{
      display:flex;
      gap:14px;
      align-items:flex-end;
      flex-wrap:wrap;
    }

    .control-block{
      display:flex;
      flex-direction:column;
      gap:5px;
    }

    .control-label{
      font-size:11px;
      font-weight:700;
      text-transform:uppercase;
      letter-spacing:.06em;
      color:rgba(0,0,0,.48);
    }

    .view-switch,
    .lang-switch{
      display:flex;
      gap:6px;
      align-items:center;
      flex-wrap:wrap;
    }

    .viewbtn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:8px 11px;
      border-radius:12px;
      border:1px solid rgba(0,0,0,.12);
      background:rgba(255,255,255,.85);
      cursor:pointer;
      user-select:none;
      font-weight:700;
      font-size:13px;
      line-height:1;
    }

    .viewbtn.active{
      border-color:rgba(31,75,153,.55);
      background:rgba(31,75,153,.10);
      color:#1f4b99;
    }

    .panel{ display:none; }
    .panel.active{ display:block; }

    .bookbar{
      display:flex;
      gap:10px;
      align-items:center;
      justify-content:space-between;
      margin:10px 0 12px;
      flex-wrap:wrap;
    }

    .bookbtn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding:9px 12px;
      border-radius:12px;
      border:1px solid rgba(0,0,0,.12);
      background:rgba(255,255,255,.85);
      color:rgba(0,0,0,.82);
      font-weight:700;
      cursor:pointer;
      user-select:none;
      line-height:1;
      text-decoration:none;
    }

    #book{
      width:100%;
      height:min(88vh, 900px);
      border-radius:16px;
      overflow:auto;
      background:rgba(255,255,255,.75);
      border:1px solid rgba(0,0,0,.08);
      box-shadow:0 12px 40px rgba(0,0,0,.10);
    }

    .spread{
      height:100%;
      min-height:560px;
      display:grid;
      grid-template-columns:1fr 1fr;
      background:rgba(255,255,255,.75);
    }

    .pageSlot{
      display:flex;
      align-items:center;
      justify-content:center;
      padding:12px;
      box-sizing:border-box;
    }

    .pageSlot.left{
      border-right:1px solid rgba(0,0,0,.06);
    }

    .pageSlot img{
      max-width:100%;
      max-height:100%;
      width:auto;
      height:auto;
      display:block;
      border-radius:8px;
      object-fit:contain;
    }

    #scrollPdf{
      width:100%;
      height:min(88vh, 920px);
      border-radius:16px;
      overflow:auto;
      box-shadow:0 12px 40px rgba(0,0,0,.10);
      background:#f4f5f7;
      border:1px solid rgba(0,0,0,.08);
      padding:14px 0;
    }

    #scrollPdf .pdfpage{
      display:flex;
      justify-content:center;
      padding:10px 0;
    }

    #scrollPdf canvas{
      background:#fff;
      border-radius:10px;
      box-shadow:0 10px 24px rgba(0,0,0,.10);
    }

    .open-row{
      margin-top:10px;
      display:flex;
      gap:8px;
      align-items:center;
      flex-wrap:wrap;
    }

    @media (max-width:900px){
      .spread{ grid-template-columns:1fr; }
      .pageSlot.left{
        border-right:none;
        border-bottom:1px solid rgba(0,0,0,.06);
      }
      .thesis-controls{ width:100%; }
    }
  </style>

  <div class="thesis-wrap">

    <div class="thesis-topbar">
      <div>
        <h1 class="thesis-title">PhD Thesis</h1>
        <p class="thesis-doc-title" id="docTitle">Optimization of Stand-Alone Photovoltaic Systems</p>
        <p class="hint" id="editionHint">English edition</p>
        <p class="hint" id="netHint"></p>
      </div>

      <div class="thesis-controls">
        <div class="control-block">
          <span class="control-label">Language</span>
          <div class="lang-switch" aria-label="Thesis language">
            <button class="viewbtn active" id="btnEN" type="button">English</button>
            <button class="viewbtn" id="btnFR" type="button">Français</button>
          </div>
        </div>

        <div class="control-block">
          <span class="control-label">View</span>
          <div class="view-switch" aria-label="View mode">
            <button class="viewbtn active" id="btnBook" type="button">Book view</button>
            <button class="viewbtn" id="btnScroll" type="button">Scroll view</button>
          </div>
        </div>
      </div>
    </div>

    <section class="panel active" id="panelBook">
      <p class="hint">Two-page spread. Use zoom for readability; scroll inside the viewer to pan.</p>

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
          <div class="pageSlot left" id="L"><span class="hint" style="font-weight:700;opacity:.65;">Loading…</span></div>
          <div class="pageSlot" id="R"><span class="hint" style="font-weight:700;opacity:.65;">Loading…</span></div>
        </div>
      </div>
    </section>

    <section class="panel" id="panelScroll">
      <p class="hint">Continuous PDF.js view. Pages render progressively as you scroll.</p>

      <div id="scrollPdf">
        <div class="pdfpage"><span class="hint" style="font-weight:700;opacity:.65;">Loading…</span></div>
      </div>

      <div class="open-row">
        <a class="bookbtn" id="fullscreenLink"
           href="{{ '/assets/pdf/These_Ferdaous_Overleaf_EN_2026.pdf' | relative_url }}"
           target="_blank" rel="noopener">
          Open fullscreen
        </a>
      </div>
    </section>

  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
  <script>
    const PDFS = {
      en: "{{ '/assets/pdf/These_Ferdaous_Overleaf_EN_2026.pdf' | relative_url }}",
      fr: "{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}"
    };

    const META = {
      en: {
        title: "Optimization of Stand-Alone Photovoltaic Systems",
        edition: "English edition"
      },
      fr: {
        title: "Optimisation de Systèmes Photovoltaïques Autonomes",
        edition: "Version française"
      }
    };

    const pdfjsLib = window.pdfjsLib;
    pdfjsLib.GlobalWorkerOptions.workerSrc =
      "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

    const btnEN = document.getElementById("btnEN");
    const btnFR = document.getElementById("btnFR");
    const btnBook = document.getElementById("btnBook");
    const btnScroll = document.getElementById("btnScroll");
    const panelBook = document.getElementById("panelBook");
    const panelScroll = document.getElementById("panelScroll");
    const docTitle = document.getElementById("docTitle");
    const editionHint = document.getElementById("editionHint");
    const fullscreenLink = document.getElementById("fullscreenLink");
    const statusEl = document.getElementById("status");
    const netHint = document.getElementById("netHint");

    const bookEl = document.getElementById("book");
    const L = document.getElementById("L");
    const R = document.getElementById("R");
    const scrollHost = document.getElementById("scrollPdf");

    let currentLang = "en";
    let currentView = "book";
    let pdfDoc = null;
    let currentScale = 1.0;
    let leftPage = 1;
    let bookRendering = false;
    let loadSerial = 0;

    let scrollDoc = null;
    let scrollScale = 1;
    let scrollInited = false;
    let scrollCanvases = [];
    let scrollObs = null;
    const scrollRendering = new Set();

    function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }
    function setStatus(txt){ statusEl.textContent = txt; }
    function spinner(){ return '<span class="hint" style="font-weight:700;opacity:.65;">Loading…</span>'; }

    function updateLanguageUI(){
      btnEN.classList.toggle("active", currentLang === "en");
      btnFR.classList.toggle("active", currentLang === "fr");
      docTitle.textContent = META[currentLang].title;
      editionHint.textContent = META[currentLang].edition;
      fullscreenLink.href = PDFS[currentLang];
      document.documentElement.lang = currentLang;
    }

    function setActiveView(mode){
      currentView = mode;
      const isBook = mode === "book";
      btnBook.classList.toggle("active", isBook);
      btnScroll.classList.toggle("active", !isBook);
      panelBook.classList.toggle("active", isBook);
      panelScroll.classList.toggle("active", !isBook);

      try { localStorage.setItem("thesis_view_mode", mode); } catch(e){}

      if (!isBook){
        setTimeout(() => initScrollPdf().catch(console.error), 30);
      }
    }

    try{
      const c = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
      if (c && (c.effectiveType || c.downlink)){
        const t = c.effectiveType ? `Network: ${c.effectiveType}` : "";
        const d = c.downlink ? `~${c.downlink}Mbps` : "";
        const msg = [t,d].filter(Boolean).join(" ");
        netHint.textContent = msg ? (msg + " • Scroll view may be faster on slower connections.") : "";
      }
    } catch(e){}

    function isSinglePageMode(){
      return window.matchMedia && window.matchMedia("(max-width: 900px)").matches;
    }

    async function renderPageToDataURL(pageNumber, scale){
      const page = await pdfDoc.getPage(pageNumber);
      const viewport = page.getViewport({ scale });
      const canvas = document.createElement("canvas");
      const ctx = canvas.getContext("2d", { alpha:false });
      canvas.width = Math.floor(viewport.width);
      canvas.height = Math.floor(viewport.height);
      await page.render({ canvasContext:ctx, viewport }).promise;
      return canvas.toDataURL("image/jpeg", 0.90);
    }

    async function computeFitScale(){
      if (!pdfDoc) return;
      const page = await pdfDoc.getPage(1);
      const v = page.getViewport({ scale:1 });
      const bookW = bookEl.clientWidth || 1000;
      const bookH = bookEl.clientHeight || 700;
      const pad = 24;
      const perPageW = (isSinglePageMode() ? bookW : (bookW / 2)) - pad;
      const perPageH = bookH - pad;
      const s = Math.min(perPageW / v.width, perPageH / v.height);
      currentScale = clamp(s, 0.75, 1.6);
    }

    async function showSpread(){
      if (!pdfDoc || bookRendering) return;
      bookRendering = true;

      leftPage = clamp(leftPage, 1, pdfDoc.numPages);
      let rightPage = isSinglePageMode() ? leftPage : leftPage + 1;
      rightPage = clamp(rightPage, 1, pdfDoc.numPages);

      L.innerHTML = spinner();
      R.innerHTML = spinner();
      setStatus(`Loading pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

      try{
        const leftUrl = await renderPageToDataURL(leftPage, currentScale);
        L.innerHTML = `<img alt="Page ${leftPage}" src="${leftUrl}">`;

        if (rightPage !== leftPage){
          const rightUrl = await renderPageToDataURL(rightPage, currentScale);
          R.innerHTML = `<img alt="Page ${rightPage}" src="${rightUrl}">`;
        } else {
          R.innerHTML = "";
        }

        setStatus(`${META[currentLang].edition} • pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);
      } catch(e){
        console.error(e);
        setStatus("Error rendering pages. Try Scroll view.");
        L.innerHTML = '<span class="hint" style="color:#b00020;font-weight:700;">Render error</span>';
        R.innerHTML = "";
      } finally{
        bookRendering = false;
      }
    }

    function clearScroll(){
      scrollHost.innerHTML = "";
      scrollCanvases = [];
      scrollRendering.clear();
      if (scrollObs){
        scrollObs.disconnect();
        scrollObs = null;
      }
    }

    function currentScrollPage(){
      const pages = Array.from(scrollHost.querySelectorAll(".pdfpage"));
      if (!pages.length) return leftPage || 1;

      const hostTop = scrollHost.getBoundingClientRect().top;
      let bestPage = 1;
      let bestDistance = Infinity;

      pages.forEach(el => {
        const d = Math.abs(el.getBoundingClientRect().top - hostTop - 10);
        if (d < bestDistance){
          bestDistance = d;
          bestPage = Number(el.dataset.page) || 1;
        }
      });

      return bestPage;
    }

    async function computeScrollFitScale(page){
      const containerW = (scrollHost.clientWidth || 900) - 40;
      const vp1 = page.getViewport({ scale:1 });
      scrollScale = clamp(containerW / vp1.width, 0.6, 1.8);
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
      if (!scrollDoc || scrollRendering.has(pageNum)) return;
      scrollRendering.add(pageNum);

      try{
        const page = await scrollDoc.getPage(pageNum);
        const viewport = page.getViewport({ scale:scrollScale });
        const canvas = scrollCanvases[pageNum];
        if (!canvas) return;

        const ctx = canvas.getContext("2d", { alpha:false });
        canvas.width = Math.floor(viewport.width);
        canvas.height = Math.floor(viewport.height);
        await page.render({ canvasContext:ctx, viewport }).promise;
      } catch(e){
        console.error(e);
      } finally{
        scrollRendering.delete(pageNum);
      }
    }

    function setupScrollObserver(){
      scrollObs = new IntersectionObserver((entries) => {
        for (const ent of entries){
          if (ent.isIntersecting){
            renderScrollPage(Number(ent.target.dataset.page));
          }
        }
      }, { root:scrollHost, rootMargin:"900px 0px", threshold:0.01 });

      scrollHost.querySelectorAll(".pdfpage").forEach(el => scrollObs.observe(el));
    }

    async function initScrollPdf(targetPage){
      if (scrollInited && !targetPage) return;
      if (!pdfDoc) return;

      clearScroll();
      scrollDoc = pdfDoc;

      const first = await scrollDoc.getPage(1);
      await computeScrollFitScale(first);

      const n = scrollDoc.numPages;
      scrollCanvases = new Array(n + 1);
      for (let i = 1; i <= n; i++){
        scrollCanvases[i] = makePageShell(i);
      }

      const startPage = clamp(targetPage || 1, 1, n);
      await renderScrollPage(startPage);
      setupScrollObserver();
      scrollInited = true;

      if (startPage > 1){
        const target = scrollHost.querySelector(`.pdfpage[data-page="${startPage}"]`);
        if (target) scrollHost.scrollTop = target.offsetTop - 10;
      } else {
        scrollHost.scrollTop = 0;
      }
    }

    async function loadLanguage(lang, preservePosition = true){
      if (lang === currentLang && pdfDoc) return;

      const previousLang = currentLang;
      const previousBookPage = leftPage || 1;
      const previousScrollPage = scrollInited ? currentScrollPage() : previousBookPage;
      const serial = ++loadSerial;

      currentLang = lang;
      updateLanguageUI();
      setStatus(`Loading ${META[lang].edition}…`);
      L.innerHTML = spinner();
      R.innerHTML = spinner();

      try{
        const newDoc = await pdfjsLib.getDocument(PDFS[lang]).promise;
        if (serial !== loadSerial) return;

        pdfDoc = newDoc;
        scrollDoc = newDoc;
        scrollInited = false;
        clearScroll();

        leftPage = preservePosition ? clamp(previousBookPage, 1, pdfDoc.numPages) : 1;
        await computeFitScale();
        await showSpread();

        if (currentView === "scroll"){
          await initScrollPdf(preservePosition ? previousScrollPage : 1);
        }

        try { localStorage.setItem("thesis_language", lang); } catch(e){}
      } catch(e){
        console.error(e);

        if (lang === "en"){
          setStatus("English PDF not found yet. Loading the French version…");
          currentLang = previousLang === "fr" ? "fr" : "fr";
          updateLanguageUI();
          await loadLanguage("fr", preservePosition);
        } else {
          setStatus("Unable to load the selected thesis PDF.");
        }
      }
    }

    btnEN.addEventListener("click", () => loadLanguage("en", true));
    btnFR.addEventListener("click", () => loadLanguage("fr", true));
    btnBook.addEventListener("click", () => setActiveView("book"));
    btnScroll.addEventListener("click", () => setActiveView("scroll"));

    document.getElementById("prevBtn").addEventListener("click", async () => {
      if (!pdfDoc) return;
      leftPage = clamp(leftPage - (isSinglePageMode() ? 1 : 2), 1, pdfDoc.numPages);
      await showSpread();
    });

    document.getElementById("nextBtn").addEventListener("click", async () => {
      if (!pdfDoc) return;
      leftPage = clamp(leftPage + (isSinglePageMode() ? 1 : 2), 1, pdfDoc.numPages);
      await showSpread();
    });

    document.getElementById("zoomIn").addEventListener("click", async () => {
      currentScale = clamp(currentScale + 0.15, 0.6, 2.2);
      await showSpread();
    });

    document.getElementById("zoomOut").addEventListener("click", async () => {
      currentScale = clamp(currentScale - 0.15, 0.6, 2.2);
      await showSpread();
    });

    let resizeBookTimer = null;
    window.addEventListener("resize", () => {
      clearTimeout(resizeBookTimer);
      resizeBookTimer = setTimeout(async () => {
        if (!pdfDoc) return;
        await computeFitScale();
        if (currentView === "book") await showSpread();
      }, 150);
    });

    let resizeScrollTimer = null;
    window.addEventListener("resize", () => {
      if (!scrollInited || !scrollDoc) return;
      clearTimeout(resizeScrollTimer);
      resizeScrollTimer = setTimeout(async () => {
        const p = currentScrollPage();
        scrollInited = false;
        await initScrollPdf(p);
      }, 250);
    });

    updateLanguageUI();
    setActiveView("book");

    // English is the default for the international website.
    // If the English PDF has not yet been uploaded, the viewer falls back to French.
    loadLanguage("en", false).catch(console.error);
  </script>

</div>
