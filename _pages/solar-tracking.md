---
layout: page
title: Solar Tracking & Energy Yield Optimization
description: Solar trajectory estimation, PV yield simulation and dual-axis solar tracking system
img: assets/img/solar-tracking.jpg
importance: 2
category: research
---

## Overview

This work investigates the optimization of photovoltaic energy production through **solar trajectory estimation and solar tracking strategies**.  
The study integrates solar position algorithms, irradiance estimation, and photovoltaic energy yield simulation in order to evaluate the performance of different photovoltaic system configurations.

The research combines **solar resource modeling**, **energy yield analysis**, and the **development of a dual-axis solar tracking system** validated through simulation and experimental implementation.

---

## Solar Trajectory Estimation

Accurate computation of the sun trajectory is essential for evaluating photovoltaic energy production and designing solar tracking systems.

Solar position was estimated using well-known algorithms:

- **SPA (Solar Position Algorithm)**
- **SOLPOS solar radiation model**

These algorithms were applied to the **Sfax (Tunisia) geographical location**, allowing precise estimation of:

- solar azimuth  
- solar elevation  
- solar irradiance conditions  

These parameters were used to simulate the expected photovoltaic energy production under realistic solar conditions.

---

## Photovoltaic Energy Yield Analysis

Using the computed solar trajectory and irradiance models, the energy production of different photovoltaic configurations was evaluated.

The study compared three system configurations:

- **Fixed photovoltaic module**
- **Single-axis solar tracker**
- **Dual-axis solar tracker**

The simulations demonstrated the **energy gain obtained through solar tracking**, particularly when using **dual-axis tracking systems** that continuously orient the photovoltaic module toward the sun.

---

## Photovoltaic Module Behavior and Configuration

The research also considered the internal configuration of photovoltaic modules.

The analysis included:

- series and parallel cell associations  
- mismatch effects between cells  
- partial shading conditions  
- bypass diode protection mechanisms  

These factors were integrated into the photovoltaic energy model to better evaluate the real performance of solar systems.

---

## Dual-Axis Solar Tracker Design

A complete **dual-axis solar tracking system** was designed in order to maximize solar radiation capture.

The system includes:

- a mechanical tracking structure  
- two motorized axes for azimuth and elevation control  
- embedded electronics for real-time control  
- solar trajectory estimation algorithms  

The tracking mechanism maintains the photovoltaic module **perpendicular to the incoming solar radiation**, maximizing energy capture compared to fixed installations.

---

## Autonomous Photovoltaic Energy Platform

A prototype of an **autonomous photovoltaic energy system** was developed including:

- dual-axis solar tracker  
- boost converter charge controller  
- real-time sensor acquisition  
- embedded control system  
- remote monitoring architecture  

The platform integrates:

- **Arduino-based sensing and control**
- **Raspberry-Pi supervisory processing**
- **cloud-based monitoring for remote data visualization**

---

## Experimental Validation

Experimental outdoor measurements confirmed the behavior predicted by simulation models.

The results demonstrate:

- the feasibility of the proposed photovoltaic system  
- the energy improvement obtained using solar tracking  
- the effectiveness of the embedded photovoltaic energy platform

---

## Key Contribution

**Energy yield optimization of photovoltaic systems through solar trajectory estimation and dual-axis solar tracking implementation.**

The study demonstrates how solar tracking mechanisms can significantly increase photovoltaic energy production compared to fixed installations.

---

## Illustrations

Recommended illustrations for this project:

- solar trajectory geometry  
- fixed vs tracking photovoltaic comparison  
- dual-axis solar tracker prototype  
- photovoltaic module configuration with bypass diodes
