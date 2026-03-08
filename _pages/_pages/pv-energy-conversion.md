---
layout: page
title: PV Energy Conversion & MPPT Control
permalink: /projects/pv-energy-conversion/
description: Photovoltaic power electronics, boost converter design and MPPT control
nav: false
---

## Overview

This research investigates the design and optimization of an autonomous photovoltaic energy conversion system. The study integrates photovoltaic source modeling, DC–DC power electronics, battery storage, and maximum power point tracking strategies.

The objective is to maximize the energy extracted from photovoltaic modules while ensuring efficient energy conversion and storage.

---

## Photovoltaic Energy Conversion Architecture

The proposed system is based on the following energy conversion chain:

PV generator  
↓  
DC-DC boost converter  
↓  
Battery storage  
↓  
Load

This architecture enables efficient adaptation between the photovoltaic generator and the storage system.

---

## Linearization around the Maximum Power Point

To facilitate converter design, the nonlinear characteristics of the photovoltaic generator and load were linearized around the **Maximum Power Point (MPP)**.

This approach simplifies system analysis and enables optimal converter dimensioning.

Scientific contribution:

**Linearization of photovoltaic source and load characteristics around the maximum power point for converter design and system optimization.**

---

## Lead-Acid Battery Modeling

The energy storage system was modeled using a **lead-acid battery model** including internal parameters and dynamic behavior.

The model enables:

- parameter identification
- simulation of battery charge and discharge behavior
- integration with the photovoltaic energy system.

Scientific contribution:

**Modeling and parameter identification of lead-acid battery storage systems for autonomous photovoltaic applications.**

---

## Boost Converter Design

A **DC-DC boost converter** was designed to adapt the voltage level between the photovoltaic generator and the battery storage system.

The converter operates in **continuous conduction mode (CCM)** and was dimensioned according to the system power requirements.

Scientific contribution:

**Design and synthesis of a DC-DC boost converter for photovoltaic energy conversion operating in continuous conduction mode.**

---

## Maximum Power Point Tracking (MPPT)

A **Perturb and Observe (P&O)** algorithm was implemented to track the maximum power point of the photovoltaic generator.

The MPPT controller continuously adjusts the operating point of the system to maximize the extracted photovoltaic power.

Scientific contribution:

**Implementation of a Perturb-and-Observe MPPT strategy for optimal photovoltaic energy harvesting.**

---

## Experimental Validation

A real prototype of the photovoltaic energy conversion system was implemented and tested experimentally.

The experimental setup integrates:

- photovoltaic module
- boost converter power stage
- battery storage
- MPPT control system.

Experimental results confirm the effectiveness of the proposed energy conversion architecture.

---

## Key Contribution

**Optimal design and experimental validation of an autonomous photovoltaic energy conversion system integrating boost converter power electronics, battery storage, and MPPT control.**
