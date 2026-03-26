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
    

    <section class="core-contrib">
    
      <div class="cc-head">
        <h2 class="cc-title">Core Research Contributions</h2>
        <p class="cc-subtitle">
          Optimization-driven photovoltaic energy system: 
          modeling → tracking → power conversion → experimental validation.
        </p>
      </div>
    
      <div class="cc-grid">
    
        <!-- CARD 1 -->
        <article class="cc-card">
          <div class="cc-media">
            <img src="{{ '/assets/img/PV Modeling Parameter Optimization.jpg' | relative_url }}"
             alt="PV modeling and parameter optimization"
             class="cc-img">
          </div>
    
          <div class="cc-body">
      
          <h3 class="cc-h3">
            PV Modeling & Parameter Optimization
          </h3>
      
          <p class="cc-text">
            Development of nonlinear equivalent-circuit models for photovoltaic cells and modules, with parameter identification formulated as an optimization problem to reproduce experimental I–V characteristics under varying irradiance and temperature conditions.
          </p>
      
          <ul class="cc-list">
          <li><strong>Nonlinear Modeling:</strong> single-, double- and multi-diode PV cell models</li>
          <li><strong>Optimization:</strong> parameter identification from experimental I–V curves</li>
          <li><strong>PV Modules:</strong> cell interconnections and behavior under shading and mismatch</li>
          </ul>
      
      
          <a class="cc-link" href="{{ '/projects/pv-modeling/' | relative_url }}">
            Read More →
          </a>
      
        </div>
        </article>
    

        <!-- CARD 2 -->
        <article class="cc-card">
        
          <div class="cc-media">
            <img src="{{ '/assets/img/solar-tracking.jpg' | relative_url }}"
                 alt="Solar tracking and energy yield optimization"
                 class="cc-img">
          </div>
        
          <div class="cc-body">
        
            <h3 class="cc-h3">
              Solar Tracking & Energy Yield Optimization
            </h3>
        
            <p class="cc-text">
              Development of solar trajectory estimation algorithms and photovoltaic energy yield analysis for fixed and tracking systems. The work integrates solar position computation, irradiance estimation, and the design of a dual-axis solar tracking platform validated through simulation and experimental implementation.
            </p>
        
            <ul class="cc-list">
              <li><strong>Solar Trajectory Modeling:</strong> solar position estimation using SPA and SOLPOS algorithms</li>
              <li><strong>Energy Yield Analysis:</strong> comparison of fixed, single-axis, and dual-axis photovoltaic tracking strategies</li>
              <li><strong>Dual-Axis Tracker Design:</strong> embedded mechatronic implementation for autonomous solar orientation</li>
            </ul>
        
            <a class="cc-link" href="{{ '/projects/solar-tracking/' | relative_url }}">
              Read More →
            </a>
        
          </div>
        </article>
    
        
        <!-- CARD 3 -->
        <article class="cc-card">
        
          <div class="cc-media">
            <img src="{{ '/assets/img/pv-energy-conversion-cover.jpg' | relative_url }}"
                 alt="PV energy conversion and MPPT control"
                 class="cc-img">
          </div>
        
          <div class="cc-body">
        
            <h3 class="cc-h3">
              PV Energy Conversion & MPPT Control
            </h3>
        
            <p class="cc-text">
              Design and modeling of an autonomous photovoltaic energy conversion chain integrating DC–DC boost conversion, battery storage, and maximum power point tracking. The system combines photovoltaic source modeling, converter synthesis, and MPPT control to optimize energy extraction from solar modules.
            </p>
        
            <ul class="cc-list">
              <li><strong>Power Electronics Design:</strong> synthesis of a DC–DC boost converter operating in continuous conduction mode</li>
              <li><strong>Battery Storage Modeling:</strong> parameter identification of lead-acid battery dynamics</li>
              <li><strong>MPPT Control Strategy:</strong> Perturb-and-Observe algorithm for maximum power extraction</li>
            </ul>
        
            <a class="cc-link" href="{{ '/projects/pv-energy-conversion/' | relative_url }}">
              Read More →
            </a>
        
          </div>
        </article>
    
        
        <!-- CARD 4 -->
        <article class="cc-card">
        
          <div class="cc-media">
            <img src="{{ '/assets/img/pv-iot-monitoring.jpg' | relative_url }}"
                 alt="Embedded PV monitoring and IoT supervision"
                 class="cc-img">
          </div>
        
          <div class="cc-body">
        
            <h3 class="cc-h3">
              Cloud Monitoring & IoT Supervision
            </h3>
        
            <p class="cc-text">
              Development of an embedded monitoring architecture for photovoltaic energy systems integrating multi-sensor acquisition, edge processing, and cloud-based supervision for real-time performance monitoring.
            </p>
        
            <ul class="cc-list">
              <li><strong>Embedded Monitoring:</strong> multi-sensor acquisition using Arduino-based controllers</li>
              <li><strong>Edge Processing:</strong> Raspberry Pi supervision for real-time data aggregation</li>
              <li><strong>Cloud Supervision:</strong> IoT platform for remote visualization and diagnostics</li>
            </ul>
        
            <a class="cc-link" href="{{ '/projects/pv-iot-monitoring/' | relative_url }}">
              Read More →
            </a>
        
          </div>
        
        </article>
    
      </div>
    </section>
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


  <!-- =========================
       FULL CONTENT INSIDE CARD
       ========================= -->
<div class="home-sections">
<section class="core-contrib">
  <div class="cc-head">
    <h2 class="cc-title">Welcome</h2>
    <p class="cc-subtitle">
I am a multidisciplinary researcher with a PhD in Electrical Engineering, focusing on the design, development, and deployment of intelligent embedded and robotic systems in real-world environments.
    </p>
    <p class="cc-subtitle">
My work has progressively expanded toward the integration of embedded intelligence, robotics, IoT, and advanced control architectures. I aim to bridge intelligent hardware with complex, dynamic environments, with a strong emphasis on adaptive behavior, real-time decision-making, and human–system interaction.
    </p>
    <p class="cc-subtitle">
I aim to bridge intelligent hardware with complex, dynamic environments, with a strong emphasis on adaptive behavior, real-time decision-making, and human–system interaction.
    </p>
  </div>
 </section>
  
  <section class="welcome-story">
  

    <div class="welcome-grid">
      <article class="welcome-card">
        <span class="welcome-step">01</span>
        <h3>Foundation in Energy Systems</h3>
        <p>
          My early work focused on photovoltaic & energy systems, where I developed a solar-tracking robotic platform for remote agricultural applications. 
          
        </p>
      </article>

      <article class="welcome-card">
        <span class="welcome-step">02</span>
        <h3>From Mechatronics to Autonomy</h3>
        <p>
         This foundation combined mechatronic design, embedded control, and energy optimization, naturally evolved into the design of intelligent autonomous systems integrating hardware, control logic, sensing, and real-time decision layers.
        </p>
      </article>

      <article class="welcome-card">
        <span class="welcome-step">03</span>
        <h3>Robotics, AI &amp; Connected Systems</h3>
        <p>
          I have led and contributed to applied R&amp;D projects involving mobile robotics, sensor fusion, AI-based task execution, and cloud-connected monitoring platforms. These solutions were implemented in real operational contexts, addressing challenges related to autonomy, environmental interaction, and system reliability.
        </p>
      </article>

      <article class="welcome-card">
        <span class="welcome-step">04</span>
        <h3>Current Research Direction</h3>
        <p>
          Today, I am especially interested in interdisciplinary research combining embedded intelligence, adaptive interaction, robotics, soft actuation, and brain-machine interfaces.
        </p>
      </article>
    </div>
  </section>
 


<section class="core-contrib">
  <div class="cc-head">
    <h2 class="cc-title">Expertise Areas</h2>
    <p class="cc-subtitle">
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
    </p>
  </div>
 </section>


   
<section class="core-contrib">
  <div class="cc-head">
    <h2 class="cc-title">Key Competencies</h2>
    <p class="cc-subtitle">
    <h3>Key Competencies</h3>
    <ul>
      <li>Mathematical Modeling | Control Theory | Optimization</li>
      <li>MATLAB/Simulink | C++ | Python | Embedded Systems</li>
      <li>PCB Design &amp; Firmware Development | IoT &amp; LoRa</li>
      <li>ROS/ROS2 | Linux | Git | Cloud Platforms</li>
    </ul>
    </p>
  </div>
 </section>


<section class="core-contrib">
  <div class="cc-head">
    <h2 class="cc-title">Professional Background</h2>
    <p class="cc-subtitle">
    <h3>Key Competencies</h3>
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
    </p>
  </div>
 </section>





 

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
