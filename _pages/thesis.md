---
layout: page
title: Thesis
permalink: /thesis/
description: PhD thesis (dual view)
---

<div class="thesis-fullbleed">

  <style>
    /* Scope everything to this page to avoid breaking al-folio */
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
    }

    #book{
      width:100%;
      height: min(88vh, 900px);    /* a bit taller so a full page fits better */
      border-radius:16px;
      overflow:auto;               /* IMPORTANT: zoom => pan inside (no cut) */
      background: rgba(255,255,255,.75);
      border: 1px solid rgba(0,0,0,.08);
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
    }

    .spread{
      height:100%;
      min-height: 560px;
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
      max-width:100%;
      max-height:100%;
      width:auto;
      height:auto;
      display:block;
      border-radius: 8px;
      object-fit: contain;
    }

    /* Small screens: single page */
    @media (max-width: 900px){
      .spread{ grid-template-columns: 1fr; }
      .pageSlot.left{
        border-right:none;
        border-bottom: 1px solid rgba(0,0,0,0.06);
      }
    }

    /* --- Scroll viewer --- */
    .pdf-frame{
      display:block;
      width:100%;
      height: min(88vh, 920px);
      border:0;
      border-radius:16px;
      overflow:hidden;
      box-shadow: 0 12px 40px rgba(0,0,0,.10);
      background:#fff;
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
      <p class="hint">Two-page spread. Zoom improves readability; scroll inside the viewer to pan.</p>

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

    <!-- SCROLL PANEL -->
    <section class="panel" id="panelScroll">
      <p class="hint">Fast scroll (lighter). For reliable zoom/fullscreen, open in a new tab.</p>

      <iframe
        class="pdf-frame"
        src="{{ '/assets/pdf/These_Ferdaous_Overleaf.pdf' | relative_url }}#view=FitH&toolbar=0&navpanes=0"
        loading="lazy">
      </iframe>

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

      // Optional: remember choice AFTER user clicks (safe)
      try { localStorage.setItem("thesis_view_mode", mode); } catch(e){}
    }

    btnBook.addEventListener("click", () => setActiveView("book"));
    btnScroll.addEventListener("click", () => setActiveView("scroll"));

    // Force default open = BOOK (ignore saved "scroll" to match your requirement)
    setActiveView("book");

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

    // ---------- BOOK VIEW (PDF.js 2-page spread) ----------
    const pdfjsLib = window.pdfjsLib;
    pdfjsLib.GlobalWorkerOptions.workerSrc =
      "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";

    const statusEl = document.getElementById("status");
    const bookEl = document.getElementById("book");
    const L = document.getElementById("L");
    const R = document.getElementById("R");

    let pdfDoc = null;
    let currentScale = 1.0; // will be auto-fit on init
    let leftPage = 1;
    let busy = false;

    function setStatus(txt){ statusEl.textContent = txt; }
    function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }
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

    function isSinglePageMode(){
      return window.matchMedia && window.matchMedia("(max-width: 900px)").matches;
    }

    async function computeFitScale(){
      // Fit page into available slot (per-page) so it starts "normal"
      const page = await pdfDoc.getPage(1);
      const v = page.getViewport({ scale: 1 });

      const bookW = bookEl.clientWidth || 1000;
      const bookH = bookEl.clientHeight || 700;

      const pad = 24; // pageSlot padding approx
      const perPageW = (isSinglePageMode() ? bookW : (bookW / 2)) - pad;
      const perPageH = bookH - pad;

      const s = Math.min(perPageW / v.width, perPageH / v.height);
      currentScale = clamp(s, 0.75, 1.6);
    }

    async function showSpread(){
      if (!pdfDoc || busy) return;
      busy = true;

      leftPage = clamp(leftPage, 1, pdfDoc.numPages);
      let rightPage = leftPage + 1;

      const single = isSinglePageMode();
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

      // Auto-fit on first load
      await computeFitScale();
      await showSpread();

      document.getElementById("prevBtn").onclick = async () => {
        leftPage = clamp(leftPage - (isSinglePageMode() ? 1 : 2), 1, pdfDoc.numPages);
        await showSpread();
      };

      document.getElementById("nextBtn").onclick = async () => {
        leftPage = clamp(leftPage + (isSinglePageMode() ? 1 : 2), 1, pdfDoc.numPages);
        await showSpread();
      };

      document.getElementById("zoomIn").onclick = async () => {
        currentScale = clamp(currentScale + 0.15, 0.6, 2.2);
        await showSpread();
      };

      document.getElementById("zoomOut").onclick = async () => {
        currentScale = clamp(currentScale - 0.15, 0.6, 2.2);
        await showSpread();
      };

      // Refit on resize (keeps it "normal" after layout changes)
      let t = null;
      window.addEventListener("resize", () => {
        clearTimeout(t);
        t = setTimeout(async () => {
          if (!pdfDoc) return;
          await computeFitScale();
          await showSpread();
        }, 150);
      });
    }

    initBook().catch(err => {
      console.error(err);
      setStatus("Error loading PDF. Switch to Scroll view.");
    });
  </script>

</div>
