---
layout: page
title: Home
permalink: /
subtitle: PhD in Electrical Engineering | Energy Systems Modeling, Control & Optimization | AgriTech Innovation

profile:
  align: right
  image: ferdaous.png
  image_circular: false
  more_info: >
    <p>Sfax, Tunisia</p>
    <p>French residence permit</p>
    <p><a href="mailto:ferdaous.masmoudi@gmail.com">ferdaous.masmoudi@gmail.com</a></p>
    <p>+216 23 605 813</p>

selected_papers: true
social: true
---

<div class="home-hero">
  <div class="home-hero-grid">
    <div>
      <h1>Ferdaous Masmoudi, PhD</h1>
      <div class="home-tags">
        <span class="tag-line">
          Photovoltaic • Renewable Energy • Power Systems • Embedded Systems
        </span>
        <span class="tag-line">
          Robotics • IoT • AI • Blockchain
        </span>
      </div>

      <p class="lead">
        Developing intelligent energy and robotic systems; modeling, optimization, embedded AI &amp; prototyping.
      </p>

      <div class="home-cta">
        <a class="home-btn primary" 
           href="{{ '/assets/pdf/ModernCVFerdaous2026EN.pdf' | relative_url }}" 
           target="_blank"
           rel="noopener">
           Download CV
        </a>
        <a class="home-btn secondary" 
           href="{{ '/thesis/' | relative_url }}"
           target="_blank"
           rel="noopener">
           Read Thesis
           </a>
        <a class="home-btn ghost" 
           href="{{ '/publications/' | relative_url }}"
           target="_blank"
           rel="noopener">
           Publications
           </a>
        <a class="home-btn ghost" 
           href="{{ '/projects/' | relative_url }}"
           target="_blank"
           rel="noopener">
           Research Projects
           </a>
      </div>
    </div>

    <div>
      <div class="home-photo">
        <img src="{{ '/assets/img/ferdaous.png' | relative_url }}" alt="Ferdaous Masmoudi">
      </div>

      <div class="home-focus">
        <div class="home-focus-row">
          <span class="home-focus-dot"></span>
          <div>
            <div class="home-focus-label">Primary Focus</div>
            <div class="home-focus-text">Photovoltaic Control &amp; Optimization</div>
          </div>
        </div>
        <div class="home-focus-row">
          <span class="home-focus-dot secondary"></span>
          <div>
            <div class="home-focus-label">Secondary Focus</div>
            <div class="home-focus-text">Robotics &amp; Embedded AI</div>
          </div>
        </div>
      </div>

      <div class="home-metrics">
        <h2>Highlight Metrics</h2>
        <div class="home-metric-grid">
          <div class="home-metric">
            <strong>10+ years</strong>
            <span>experience</span>
          </div>
          <div class="home-metric">
            <strong>25+</strong>
            <span>experimental validation</span>
          </div>
          <div class="home-metric">
            <strong>Real-time</strong>
            <span>AI prototyping</span>
          </div>
          <div class="home-metric">
            <strong>Hardware</strong>
            <span>platform integration</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  
    <div class="cc-head">
      <h2 class="cc-title">Core Research Contributions</h2>
      <p class="cc-subtitle">
        Optimization-driven photovoltaic energy system: modeling → tracking → conversion → experimental validation.
      </p>
    </div>
  
    <div class="cc-grid">
      <!-- 1) PV Modeling -->
      <article class="cc-card">
        <div class="cc-media">
          <img
            src="/assets/img/thesis/ch5_pv_model_iv.png"
            alt="PV equivalent circuit and I–V curves comparison"
            loading="lazy"
          />
        </div>
        <div class="cc-body">
          <h3 class="cc-h3">1) PV Modeling & Parameter Identification (Optimization)</h3>
          <p class="cc-text">
            Nonlinear PV modeling using equivalent circuits, with parameter estimation formulated as an optimization problem
            to fit I–V characteristics under varying irradiance and temperature.
          </p>
          <ul class="cc-list">
            <li>Equivalent-circuit PV models (module/cell level)</li>
            <li>Parameter identification via optimization criteria (error minimization)</li>
            <li>Validation against experimental or reference I–V curves</li>
          </ul>
          <div class="cc-tags">
            <span class="cc-tag">Nonlinear modeling</span>
            <span class="cc-tag">Identification</span>
            <span class="cc-tag">Optimization</span>
          </div>
        </div>
      </article>
  
      <!-- 2) Solar Tracking -->
      <article class="cc-card">
        <div class="cc-media">
          <img
            src="/assets/img/thesis/ch5_tracker_proto.png"
            alt="Dual-axis solar tracker prototype"
            loading="lazy"
          />
        </div>
        <div class="cc-body">
          <h3 class="cc-h3">2) Dual-Axis Solar Tracking (Energy Yield Optimization)</h3>
          <p class="cc-text">
            Design and implementation of a dual-axis tracking mechanism driven by solar trajectory estimation to maximize
            incident irradiance and harvested energy.
          </p>
          <ul class="cc-list">
            <li>Mechanical structure + sensors + embedded control</li>
            <li>Open-loop trajectory tracking (sun path)</li>
            <li>Experimental measurements and tracking variables logging</li>
          </ul>
          <div class="cc-tags">
            <span class="cc-tag">Mechatronics</span>
            <span class="cc-tag">Tracking</span>
            <span class="cc-tag">Embedded</span>
          </div>
        </div>
      </article>
  
      <!-- 3) MPPT + Boost -->
      <article class="cc-card">
        <div class="cc-media">
          <img
            src="/assets/img/thesis/ch5_boost_mppt.png"
            alt="Boost converter and MPPT control"
            loading="lazy"
          />
        </div>
        <div class="cc-body">
          <h3 class="cc-h3">3) PV Power Conversion & MPPT Control (Efficiency Optimization)</h3>
          <p class="cc-text">
            Design of a DC–DC Boost stage and control strategy (MPPT) to operate the PV generator near its maximum power
            point and transfer energy efficiently to storage/load.
          </p>
          <ul class="cc-list">
            <li>Boost sizing + power stage implementation</li>
            <li>MPPT strategy integrated in embedded controller</li>
            <li>Oscilloscope validation: Vgs, Vpv, Vds, Vs</li>
          </ul>
          <div class="cc-tags">
            <span class="cc-tag">Power electronics</span>
            <span class="cc-tag">MPPT</span>
            <span class="cc-tag">Efficiency</span>
          </div>
        </div>
      </article>
  
      <!-- 4) Experimental Platform + Cloud -->
      <article class="cc-card">
        <div class="cc-media">
          <img
            src="/assets/img/thesis/ch5_cloud_monitoring.png"
            alt="Cloud-based monitoring and data acquisition architecture"
            loading="lazy"
          />
        </div>
        <div class="cc-body">
          <h3 class="cc-h3">4) Experimental Validation & Remote Monitoring (System Optimization)</h3>
          <p class="cc-text">
            Full prototype validation with real outdoor tests, real-time data acquisition, and cloud-based monitoring for
            analysis, supervision, and dataset building.
          </p>
          <ul class="cc-list">
            <li>Sensor acquisition layer + embedded computing</li>
            <li>Remote supervision (web service / cloud logging)</li>
            <li>Experimental dataset used to confirm simulation trends</li>
          </ul>
          <div class="cc-tags">
            <span class="cc-tag">Experimental</span>
            <span class="cc-tag">Cloud</span>
            <span class="cc-tag">Data</span>
          </div>
        </div>
      </article>
    </div>
  
  <!-- =========================
       FULL CONTENT INSIDE CARD
       ========================= -->

  <div class="home-sections">

    <h2>Welcome</h2>
    <p>
      I am a <strong>PhD in Electrical Engineering</strong> specializing in
      <strong>Energy Systems Modeling, Control &amp; Optimization</strong>.
      My research focuses on nonlinear mathematical modeling, parameter identification,
      optimization strategies, and real-time embedded control for photovoltaic and electrochemical systems.
    </p>

    <h2>Research Profile</h2>

    <h3>Expertise Areas</h3>
    <ul>
      <li>Photovoltaic systems modeling &amp; MPPT control</li>
      <li>Power electronics &amp; DC-DC converter design</li>
      <li>Embedded systems &amp; real-time control (STM32, ESP32, Arduino)</li>
      <li>Data-driven parameter identification &amp; state estimation (EKF)</li>
      <li>AgriTech innovation &amp; IoT platforms</li>
      <li>Mobile &amp; web development (Android, REST APIs)</li>
      <li>Computer vision &amp; AI/ML integration</li>
    </ul>

    <h3>Key Competencies</h3>
    <ul>
      <li>Mathematical Modeling | Control Theory | Optimization</li>
      <li>MATLAB/Simulink | C++ | Python | Embedded Systems</li>
      <li>PCB Design &amp; Firmware Development | IoT &amp; LoRa</li>
      <li>ROS/ROS2 | Linux | Git | Cloud Platforms</li>
    </ul>

    <h2>Professional Background</h2>

    <h3>Industry</h3>
    <p><strong>Co-founder &amp; R&amp;D Lead</strong> at NOVEL-TI (2016–Present)</p>
    <ul>
      <li>End-to-end development of intelligent energy systems</li>
      <li>AgriTech solutions with blockchain-based traceability</li>
      <li>Multi-disciplinary technical team leadership</li>
    </ul>

    <h3>Education</h3>
    <ul>
      <li>PhD in Electrical Engineering, ENIS Sfax (2016)</li>
      <li>MSc in Electrical Conversion &amp; Renewable Energy, ENIS Sfax (2012)</li>
      <li>Engineering Degree in Electrical Engineering, ENIS Sfax (2011)</li>
    </ul>

    <h2>Research Contributions</h2>
    <p>
      My doctoral research focused on <strong>optimization of standalone photovoltaic systems</strong>, including:
    </p>
    <ul>
      <li>Nonlinear PV cell modeling (single, double, multi-diode configurations)</li>
      <li>Optimization-based control strategies &amp; MPPT algorithms</li>
      <li>Embedded implementation on microcontroller platforms</li>
      <li>Real-time multi-sensor acquisition &amp; cloud supervision</li>
    </ul>

    <p><strong>3 Scopus-indexed journal publications</strong> &amp; <strong>12+ IEEE conference papers</strong></p>

    <hr>

    <p>
      <strong>→ Quick access:</strong>
      <a href="{{ '/cv/' | relative_url }}">CV</a>,
      <a href="{{ '/thesis/' | relative_url }}">Thesis</a>,
      <a href="{{ '/publications/' | relative_url }}">Publications</a>,
      <a href="{{ '/projects/' | relative_url }}">Research Projects</a>
    </p>

  </div>
</div>
