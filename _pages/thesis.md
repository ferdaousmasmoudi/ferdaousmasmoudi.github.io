---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis in English and French with book and scroll views
---

<div class="thesis-fullbleed">
  <style>
    .thesis-fullbleed { width: 100%; }

    .thesis-wrap {
      width: min(1400px, 96vw);
      margin: 0 auto;
      padding: 10px 0 30px;
    }

    .thesis-topbar {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      gap: 16px;
      flex-wrap: wrap;
      margin: 10px 0 14px;
    }

    .thesis-title { margin: 0; }

    .thesis-doc-title {
      margin: 5px 0 0;
      font-size: 14px;
      font-weight: 600;
      color: rgba(0,0,0,.62);
    }

    .hint {
      font-size: 13px;
      color: rgba(0,0,0,.55);
      margin: 0;
    }

    .thesis-controls {
      display: flex;
      gap: 14px;
      align-items: flex-end;
      flex-wrap: wrap;
    }

    .control-block {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }

    .control-label {
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: .06em;
      color: rgba(0,0,0,.48);
    }

    .switch-row {
      display: flex;
      gap: 6px;
      align-items: center;
      flex-wrap: wrap;
    }

    .switchbtn,
    .bookbtn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      border-radius: 12px;
      border: 1px solid rgba(0,0,0,.12);
      background: rgba(255,255,255,.88);
      color: rgba(0,0,0,.82);
      font-weight: 700;
      cursor: pointer;
      user-select: none;
      text-decoration: none;
    }

    .switchbtn {
      padding: 8px 11px;
      font-size: 13px;
      line-height: 1;
    }

    .switchbtn.active {
      border-color: rgba(31,75,153,.55);
      background: rgba(31,75,153,.10);
      color: #1f4b99;
    }

    .bookbtn {
      padding: 9px 12px;
      line-height: 1;
    }

    .panel { display: none; }
    .panel.active { display: block; }

    .bookbar {
      display: flex;
      gap: 10px;
      align-items: center;
      justify-content: space-between;
      margin: 10px 0 12px;
      flex-wrap: wrap;
    }

    #book {
      width: 100%;
      height: min(88vh, 900px);
      border-radius: 16px;
      overflow: auto;
      background: rgba(255,255,255,.75);
      border: 1px solid rgba(0,0,0,.08);
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
    }

    .spread {
      height: 100%;
      min-height: 560px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      background: rgba(255,255,255,.75);
    }

    .pageSlot {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 12px;
      box-sizing: border-box;
    }

    .pageSlot.left {
      border-right: 1px solid rgba(0,0,0,.06);
    }

    .pageSlot img {
      max-width: 100%;
      max-height: 100%;
      width: auto;
      height: auto;
      display: block;
      border-radius: 8px;
      object-fit: contain;
    }

    #scrollPdf {
      width: 100%;
      height: min(88vh, 920px);
      border-radius: 16px;
      overflow: auto;
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
      background: #f4f5f7;
      border: 1px solid rgba(0,0,0,.08);
      padding: 14px 0;
    }

    #scrollPdf .pdfpage {
      display: flex;
      justify-content: center;
      padding: 10px 0;
      min-height: 60px;
    }

    #scrollPdf canvas {
      background: #fff;
      border-radius: 10px;
      box-shadow: 0 10px 24px rgba(0,0,0,.10);
    }

    .open-row {
      margin-top: 10px;
      display: flex;
      gap: 8px;
      align-items: center;
      flex-wrap: wrap;
    }

    @media (max-width: 900px) {
      .spread { grid-template-columns: 1fr; }
      .pageSlot.left {
        border-right: none;
        border-bottom: 1px solid rgba(0,0,0,.06);
      }
      .thesis-controls { width: 100%; }
    }
  </style>

  <div class="thesis-wrap">
    <div class="thesis-topbar">
      <div>
        <h1 class="thesis-title">PhD Thesis</h1>
        <p class="thesis-doc-title" id="docTitle">Optimization of Stand-Alone Photovoltaic Systems</p>
        <p class="hint" id="editionHint">English version</p>
      </div>

      <div class="thesis-controls">
        <div class="control-block">
          <span class="control-label">Language</span>
          <div class="switch-row" aria-label="Thesis language">
            <button class="switchbtn active" id="btnEN" type="button">English</button>
            <button class="switchbtn" id="btnFR" type="button">Français</button>
          </div>
        </div>

        <div class="control-block">
          <span class="control-label">View</span>
          <div class="switch-row" aria-label="View mode">
            <button class="switchbtn active" id="btnBook" type="button">Book view</button>
            <button class="switchbtn" id="btnScroll" type="button">Scroll view</button>
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
          <div class="pageSlot left" id="L"><span class="hint">Loading…</span></div>
          <div class="pageSlot" id="R"><span class="hint">Loading…</span></div>
        </div>
      </div>
    </section>

    <section class="panel" id="panelScroll">
      <p class="hint">Continuous view. Pages render progressively as you scroll.</p>

      <div id="scrollPdf">
        <div class="pdfpage"><span class="hint">Loading…</span></div>
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
      fr: "{{ '/assets/pdf/These_Ferdaous_Overleaf_FR_2026.pdf' | relative_url }}"
    };

    const META = {
      en: {
        title: "Optimization of Stand-Alone Photovoltaic Systems",
        edition: "English version"
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
    const bookEl = document.getElementById("book");
    const L = document.getElementById("L");
    const R = document.getElementById("R");
    const scrollHost = document.getElementById("scrollPdf");

    let currentLang = "en";
    let currentView = "book";
    let pdfDoc = null;
    let currentScale = 1.0;
    let leftPage = 1;
    let loadingLanguage = false;

    let scrollScale = 1.0;
    let scrollInited = false;
    let scrollCanvases = [];
    let scrollObserver = null;
    const scrollRendering = new Set();

    function clamp(n, a, b) {
      return Math.max(a, Math.min(b, n));
    }

    function spinner() {
      return '<span class="hint" style="font-weight:700;opacity:.65;">Loading…</span>';
    }

    function setStatus(text) {
      statusEl.textContent = text;
    }

    function isSinglePageMode() {
      return window.matchMedia && window.matchMedia("(max-width: 900px)").matches;
    }

    function updateLanguageUI() {
      btnEN.classList.toggle("active", currentLang === "en");
      btnFR.classList.toggle("active", currentLang === "fr");
      docTitle.textContent = META[currentLang].title;
      editionHint.textContent = META[currentLang].edition;
      fullscreenLink.href = PDFS[currentLang];
    }

    function clearScroll() {
      scrollHost.innerHTML = "";
      scrollCanvases = [];
      scrollRendering.clear();
      if (scrollObserver) {
        scrollObserver.disconnect();
        scrollObserver = null;
      }
      scrollInited = false;
    }

    async function computeBookFitScale() {
      if (!pdfDoc) return;
      const page = await pdfDoc.getPage(1);
      const viewport = page.getViewport({ scale: 1 });
      const bookW = bookEl.clientWidth || 1000;
      const bookH = bookEl.clientHeight || 700;
      const perPageW = (isSinglePageMode() ? bookW : bookW / 2) - 24;
      const perPageH = bookH - 24;
      currentScale = clamp(
        Math.min(perPageW / viewport.width, perPageH / viewport.height),
        0.65,
        1.6
      );
    }

    async function renderBookPage(pageNumber, scale) {
      const page = await pdfDoc.getPage(pageNumber);
      const viewport = page.getViewport({ scale });
      const canvas = document.createElement("canvas");
      const context = canvas.getContext("2d", { alpha: false });
      canvas.width = Math.floor(viewport.width);
      canvas.height = Math.floor(viewport.height);
      await page.render({ canvasContext: context, viewport }).promise;
      return canvas.toDataURL("image/jpeg", 0.90);
    }

    async function showSpread() {
      if (!pdfDoc || loadingLanguage) return;

      leftPage = clamp(leftPage, 1, pdfDoc.numPages);
      const rightPage = isSinglePageMode()
        ? leftPage
        : clamp(leftPage + 1, 1, pdfDoc.numPages);

      L.innerHTML = spinner();
      R.innerHTML = spinner();
      setStatus(`Loading pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);

      try {
        const leftImage = await renderBookPage(leftPage, currentScale);
        L.innerHTML = `<img alt="Page ${leftPage}" src="${leftImage}">`;

        if (rightPage !== leftPage) {
          const rightImage = await renderBookPage(rightPage, currentScale);
          R.innerHTML = `<img alt="Page ${rightPage}" src="${rightImage}">`;
        } else {
          R.innerHTML = "";
        }

        setStatus(`${META[currentLang].edition} • pages ${leftPage}-${rightPage} / ${pdfDoc.numPages}`);
      } catch (error) {
        console.error(error);
        setStatus("Unable to render these pages.");
      }
    }

    async function computeScrollScale() {
      const firstPage = await pdfDoc.getPage(1);
      const viewport = firstPage.getViewport({ scale: 1 });
      const availableWidth = (scrollHost.clientWidth || 900) - 40;
      scrollScale = clamp(availableWidth / viewport.width, 0.6, 1.8);
    }

    function createScrollShell(pageNumber) {
      const wrapper = document.createElement("div");
      wrapper.className = "pdfpage";
      wrapper.dataset.page = String(pageNumber);

      const canvas = document.createElement("canvas");
      canvas.width = 10;
      canvas.height = 10;
      wrapper.appendChild(canvas);
      scrollHost.appendChild(wrapper);
      scrollCanvases[pageNumber] = canvas;
    }

    async function renderScrollPage(pageNumber) {
      if (!pdfDoc || scrollRendering.has(pageNumber)) return;
      scrollRendering.add(pageNumber);

      try {
        const page = await pdfDoc.getPage(pageNumber);
        const viewport = page.getViewport({ scale: scrollScale });
        const canvas = scrollCanvases[pageNumber];
        if (!canvas) return;

        const context = canvas.getContext("2d", { alpha: false });
        canvas.width = Math.floor(viewport.width);
        canvas.height = Math.floor(viewport.height);
        await page.render({ canvasContext: context, viewport }).promise;
      } finally {
        scrollRendering.delete(pageNumber);
      }
    }

    function setupScrollObserver() {
      scrollObserver = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            renderScrollPage(Number(entry.target.dataset.page)).catch(console.error);
          }
        });
      }, {
        root: scrollHost,
        rootMargin: "900px 0px",
        threshold: 0.01
      });

      scrollHost.querySelectorAll(".pdfpage").forEach((page) => {
        scrollObserver.observe(page);
      });
    }

    async function initScroll(targetPage = 1) {
      if (!pdfDoc) return;

      clearScroll();
      await computeScrollScale();

      scrollCanvases = new Array(pdfDoc.numPages + 1);
      for (let page = 1; page <= pdfDoc.numPages; page++) {
        createScrollShell(page);
      }

      const firstVisible = clamp(targetPage, 1, pdfDoc.numPages);
      await renderScrollPage(firstVisible);
      setupScrollObserver();
      scrollInited = true;

      const target = scrollHost.querySelector(`.pdfpage[data-page="${firstVisible}"]`);
      if (target) scrollHost.scrollTop = target.offsetTop - 10;
    }

    function currentScrollPage() {
      const pages = Array.from(scrollHost.querySelectorAll(".pdfpage"));
      if (!pages.length) return leftPage;

      const hostTop = scrollHost.getBoundingClientRect().top;
      let bestPage = 1;
      let bestDistance = Infinity;

      pages.forEach((page) => {
        const distance = Math.abs(page.getBoundingClientRect().top - hostTop);
        if (distance < bestDistance) {
          bestDistance = distance;
          bestPage = Number(page.dataset.page) || 1;
        }
      });

      return bestPage;
    }

    async function setLanguage(lang) {
      if (lang === currentLang && pdfDoc) return;

      const savedPage = currentView === "scroll" && scrollInited
        ? currentScrollPage()
        : leftPage;

      currentLang = lang;
      updateLanguageUI();
      loadingLanguage = true;
      clearScroll();
      L.innerHTML = spinner();
      R.innerHTML = spinner();
      setStatus(`Loading ${META[lang].edition}…`);

      try {
        pdfDoc = await pdfjsLib.getDocument(PDFS[lang]).promise;
        leftPage = clamp(savedPage || 1, 1, pdfDoc.numPages);
        await computeBookFitScale();
      } catch (error) {
        console.error(error);
        setStatus("Unable to load the selected thesis PDF.");
        loadingLanguage = false;
        return;
      }

      loadingLanguage = false;

      if (currentView === "book") {
        await showSpread();
      } else {
        await initScroll(leftPage);
      }
    }

    function setView(view) {
      currentView = view;
      const bookMode = view === "book";

      btnBook.classList.toggle("active", bookMode);
      btnScroll.classList.toggle("active", !bookMode);
      panelBook.classList.toggle("active", bookMode);
      panelScroll.classList.toggle("active", !bookMode);

      if (!bookMode && pdfDoc) {
        initScroll(leftPage).catch(console.error);
      }
    }

    btnEN.addEventListener("click", () => setLanguage("en"));
    btnFR.addEventListener("click", () => setLanguage("fr"));
    btnBook.addEventListener("click", () => setView("book"));
    btnScroll.addEventListener("click", () => setView("scroll"));

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

    let resizeTimer = null;
    window.addEventListener("resize", () => {
      clearTimeout(resizeTimer);
      resizeTimer = setTimeout(async () => {
        if (!pdfDoc) return;

        if (currentView === "book") {
          await computeBookFitScale();
          await showSpread();
        } else {
          const visiblePage = currentScrollPage();
          await initScroll(visiblePage);
        }
      }, 200);
    });

    updateLanguageUI();
    setView("book");
    setLanguage("en").catch(console.error);
  </script>
</div>
