---
layout: page
title: Research Projects
permalink: /projects/
description: Research and development projects
nav: true
nav_order: 3
---

<div class="home-hero rp-hero">
  <div class="home-hero-grid rp-grid">

    <!-- LEFT -->
    <div>
      <h1>Research Projects</h1>

      <div class="home-tags">
        <span class="tag-line">Photovoltaics • Batteries • Robotics • Power Electronics</span>
        <span class="tag-line">MATLAB/Simulink • Modeling • Control • Experimental Results</span>
      </div>

      <p class="lead">
        Click a domain to view a quick technical overview, selected figures/results, and downloadable simulation/code artifacts.
      </p>

      <div class="home-cta rp-cta">
        <a class="home-btn primary" href="#domains">Browse Domains</a>
        <a class="home-btn secondary" href="/publications/">Publications</a>
        <a class="home-btn ghost" href="/thesis/">Thesis</a>
        <a class="home-btn ghost" href="/cv/">CV</a>
      </div>

      <div class="home-sections">
        <h2 id="domains">Domains</h2>

        <div class="rp-cards">

          <!-- PV -->
          <button class="rp-card" type="button" data-modal="rp-modal-pv" aria-haspopup="dialog" aria-controls="rp-modal-pv">
            <div class="rp-card-top">
              <span class="rp-badge">Photovoltaics</span>
              <span class="rp-chip">MATLAB</span>
              <span class="rp-chip">Simulink</span>
            </div>
            <h3 class="rp-title">PV Cell Modeling & Parameter Extraction</h3>
            <p class="rp-desc">
              Single/Double diode models, parameter identification, temperature & irradiance influence, I–V / P–V results.
            </p>
            <div class="rp-foot">
              <span class="rp-kpi"><strong>Artifacts</strong><span>Plots + Models</span></span>
              <span class="rp-kpi"><strong>Scope</strong><span>Modeling + Validation</span></span>
              <span class="rp-open">View details →</span>
            </div>
          </button>

          <!-- Batteries -->
          <button class="rp-card" type="button" data-modal="rp-modal-bat" aria-haspopup="dialog" aria-controls="rp-modal-bat">
            <div class="rp-card-top">
              <span class="rp-badge">Batteries</span>
              <span class="rp-chip">ECM</span>
              <span class="rp-chip">SoC</span>
            </div>
            <h3 class="rp-title">Battery Modeling & Estimation</h3>
            <p class="rp-desc">
              Equivalent circuit models, charge/discharge profiles, estimation logic, comparison plots.
            </p>
            <div class="rp-foot">
              <span class="rp-kpi"><strong>Artifacts</strong><span>Datasets + Plots</span></span>
              <span class="rp-kpi"><strong>Outputs</strong><span>SoC / V / I</span></span>
              <span class="rp-open">View details →</span>
            </div>
          </button>

          <!-- Tracker -->
          <button class="rp-card" type="button" data-modal="rp-modal-trk" aria-haspopup="dialog" aria-controls="rp-modal-trk">
            <div class="rp-card-top">
              <span class="rp-badge">Robotics</span>
              <span class="rp-chip">Control</span>
              <span class="rp-chip">Embedded</span>
            </div>
            <h3 class="rp-title">Dual-Axis Solar Tracker (Robotized)</h3>
            <p class="rp-desc">
              Design, control modes (open/closed/hybrid), sensor integration, fixed vs tracked energy results.
            </p>
            <div class="rp-foot">
              <span class="rp-kpi"><strong>Modes</strong><span>3</span></span>
              <span class="rp-kpi"><strong>Axes</strong><span>2</span></span>
              <span class="rp-open">View details →</span>
            </div>
          </button>

          <!-- Power -->
          <button class="rp-card" type="button" data-modal="rp-modal-pow" aria-haspopup="dialog" aria-controls="rp-modal-pow">
            <div class="rp-card-top">
              <span class="rp-badge">Power</span>
              <span class="rp-chip">DC-DC</span>
              <span class="rp-chip">MPPT</span>
            </div>
            <h3 class="rp-title">Conversion Systems & Power Electronics</h3>
            <p class="rp-desc">
              Converter modeling, MPPT control, efficiency/ripple analysis, simulation results.
            </p>
            <div class="rp-foot">
              <span class="rp-kpi"><strong>KPIs</strong><span>η / ripple</span></span>
              <span class="rp-kpi"><strong>Blocks</strong><span>Converters</span></span>
              <span class="rp-open">View details →</span>
            </div>
          </button>

        </div>

        <hr/>

        <h2>How downloads work</h2>
        <p>
          Each modal exposes direct links to ZIP/PDF assets stored in <code>/assets/downloads/</code>.
          You control exactly what is downloadable (no auto-detection from the internet).
        </p>
      </div>
    </div>

    <!-- RIGHT -->
    <div>
      <div class="home-focus rp-side">
        <div class="home-focus-row">
          <span class="home-focus-dot"></span>
          <span class="home-focus-label">Workflow</span>
          <span class="home-focus-text">Model → Simulate → Validate</span>
        </div>
        <div class="home-focus-row">
          <span class="home-focus-dot secondary"></span>
          <span class="home-focus-label">Outputs</span>
          <span class="home-focus-text">Plots, datasets, code, reports</span>
        </div>
        <div class="home-focus-row">
          <span class="home-focus-dot"></span>
          <span class="home-focus-label">Tools</span>
          <span class="home-focus-text">MATLAB/Simulink, Control, Embedded</span>
        </div>
      </div>

      <div class="home-metrics rp-metrics">
        <h2>Snapshot</h2>
        <div class="home-metric-grid">
          <div class="home-metric"><strong>4</strong><span>Domains</span></div>
          <div class="home-metric"><strong>Code</strong><span>MATLAB/Simulink</span></div>
          <div class="home-metric"><strong>Results</strong><span>Plots & comparisons</span></div>
          <div class="home-metric"><strong>Docs</strong><span>PDF summaries</span></div>
        </div>
      </div>
    </div>

  </div>
</div>

<!-- =========================
     MODALS
     ========================= -->

<div class="rp-modal" id="rp-modal-pv" role="dialog" aria-modal="true" aria-labelledby="rp-pv-title" aria-hidden="true">
  <div class="rp-modal-card" role="document">
    <button class="rp-close" type="button" aria-label="Close dialog">×</button>
    <h2 id="rp-pv-title">PV Cell Modeling & Parameter Extraction</h2>
    <p class="rp-sub">
      Single/Double diode models, parameter identification, and I–V / P–V results under temperature/irradiance variations.
    </p>

    <div class="rp-gallery">
      <img src="/assets/img/research/pv/pv_1.png" alt="PV result 1">
      <img src="/assets/img/research/pv/pv_2.png" alt="PV result 2">
      <img src="/assets/img/research/pv/pv_3.png" alt="PV result 3">
    </div>

    <div class="rp-results">
      <div class="rp-panel">
        <h3>Highlights</h3>
        <ul>
          <li>Identification workflow and parameter extraction</li>
          <li>Comparative curves (I–V, P–V)</li>
          <li>Sensitivity to temperature & irradiance</li>
        </ul>
      </div>
      <div class="rp-panel">
        <h3>Downloads</h3>
        <div class="rp-downloads">
          <a class="home-btn ghost" href="/assets/downloads/pv/pv_matlab_code.zip">Download MATLAB</a>
          <a class="home-btn ghost" href="/assets/downloads/pv/pv_simulink_models.zip">Download Simulink</a>
          <a class="home-btn secondary" href="/assets/downloads/pv/pv_summary.pdf">PDF Summary</a>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="rp-modal" id="rp-modal-bat" role="dialog" aria-modal="true" aria-labelledby="rp-bat-title" aria-hidden="true">
  <div class="rp-modal-card" role="document">
    <button class="rp-close" type="button" aria-label="Close dialog">×</button>
    <h2 id="rp-bat-title">Battery Modeling & Estimation</h2>
    <p class="rp-sub">Equivalent circuit modeling, profiles, and estimation plots (SoC/V/I).</p>

    <div class="rp-gallery">
      <img src="/assets/img/research/batteries/bat_1.png" alt="Battery result 1">
      <img src="/assets/img/research/batteries/bat_2.png" alt="Battery result 2">
      <img src="/assets/img/research/batteries/bat_3.png" alt="Battery result 3">
    </div>

    <div class="rp-results">
      <div class="rp-panel">
        <h3>Highlights</h3>
        <ul>
          <li>ECM response vs profile data</li>
          <li>Curve fitting & evaluation plots</li>
          <li>Estimation logic documentation</li>
        </ul>
      </div>
      <div class="rp-panel">
        <h3>Downloads</h3>
        <div class="rp-downloads">
          <a class="home-btn ghost" href="/assets/downloads/batteries/battery_matlab_code.zip">Download MATLAB</a>
          <a class="home-btn ghost" href="/assets/downloads/batteries/battery_models.zip">Download Models</a>
          <a class="home-btn secondary" href="/assets/downloads/batteries/battery_summary.pdf">PDF Summary</a>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="rp-modal" id="rp-modal-trk" role="dialog" aria-modal="true" aria-labelledby="rp-trk-title" aria-hidden="true">
  <div class="rp-modal-card" role="document">
    <button class="rp-close" type="button" aria-label="Close dialog">×</button>
    <h2 id="rp-trk-title">Dual-Axis Solar Tracker (Robotized)</h2>
    <p class="rp-sub">Design + control modes + fixed vs tracked comparison results.</p>

    <div class="rp-gallery">
      <img src="/assets/img/research/tracker/trk_1.png" alt="Tracker result 1">
      <img src="/assets/img/research/tracker/trk_2.png" alt="Tracker result 2">
      <img src="/assets/img/research/tracker/trk_3.png" alt="Tracker result 3">
    </div>

    <div class="rp-results">
      <div class="rp-panel">
        <h3>Highlights</h3>
        <ul>
          <li>Open/Closed/Hybrid control modes</li>
          <li>Energy gain vs fixed orientation</li>
          <li>Implementation notes (sensors/actuators)</li>
        </ul>
      </div>
      <div class="rp-panel">
        <h3>Downloads</h3>
        <div class="rp-downloads">
          <a class="home-btn ghost" href="/assets/downloads/tracker/tracker_code.zip">Download Code</a>
          <a class="home-btn ghost" href="/assets/downloads/tracker/tracker_simulink.zip">Download Simulink</a>
          <a class="home-btn secondary" href="/assets/downloads/tracker/tracker_summary.pdf">PDF Summary</a>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="rp-modal" id="rp-modal-pow" role="dialog" aria-modal="true" aria-labelledby="rp-pow-title" aria-hidden="true">
  <div class="rp-modal-card" role="document">
    <button class="rp-close" type="button" aria-label="Close dialog">×</button>
    <h2 id="rp-pow-title">Conversion Systems & Power Electronics</h2>
    <p class="rp-sub">DC-DC modeling, MPPT, efficiency/ripple plots, simulation results.</p>

    <div class="rp-gallery">
      <img src="/assets/img/research/power/pow_1.png" alt="Power result 1">
      <img src="/assets/img/research/power/pow_2.png" alt="Power result 2">
      <img src="/assets/img/research/power/pow_3.png" alt="Power result 3">
    </div>

    <div class="rp-results">
      <div class="rp-panel">
        <h3>Highlights</h3>
        <ul>
          <li>Converter block modeling</li>
          <li>MPPT controller response</li>
          <li>η and ripple comparison plots</li>
        </ul>
      </div>
      <div class="rp-panel">
        <h3>Downloads</h3>
        <div class="rp-downloads">
          <a class="home-btn ghost" href="/assets/downloads/power/power_code.zip">Download Code</a>
          <a class="home-btn ghost" href="/assets/downloads/power/power_simulink.zip">Download Simulink</a>
          <a class="home-btn secondary" href="/assets/downloads/power/power_summary.pdf">PDF Summary</a>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
  (function () {
    const openButtons = document.querySelectorAll('[data-modal]');
    const modals = document.querySelectorAll('.rp-modal');
    let lastFocused = null;

    function openModal(id) {
      const modal = document.getElementById(id);
      if (!modal) return;
      lastFocused = document.activeElement;
      modal.setAttribute('aria-hidden', 'false');
      document.body.classList.add('rp-modal-open');
      const closeBtn = modal.querySelector('.rp-close');
      if (closeBtn) closeBtn.focus();
    }

    function closeModal(modal) {
      modal.setAttribute('aria-hidden', 'true');
      document.body.classList.remove('rp-modal-open');
      if (lastFocused) lastFocused.focus();
    }

    openButtons.forEach(btn => btn.addEventListener('click', () => openModal(btn.dataset.modal)));

    modals.forEach(modal => {
      const closeBtn = modal.querySelector('.rp-close');
      if (closeBtn) closeBtn.addEventListener('click', () => closeModal(modal));
      modal.addEventListener('click', (e) => { if (e.target === modal) closeModal(modal); });
    });

    document.addEventListener('keydown', (e) => {
      if (e.key !== 'Escape') return;
      const opened = document.querySelector('.rp-modal[aria-hidden="false"]');
      if (opened) closeModal(opened);
    });
  })();
</script>
