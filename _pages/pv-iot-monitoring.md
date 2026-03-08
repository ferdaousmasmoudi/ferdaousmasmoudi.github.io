---
layout: page
title: Cloud Monitoring & IoT Supervision for Photovoltaic Systems
permalink: /projects/pv-iot-monitoring/
description: Embedded IoT architecture for real-time photovoltaic monitoring
nav: false
---
## Overview

This work presents the design and implementation of an embedded monitoring
architecture for photovoltaic energy systems.

The proposed platform integrates embedded sensing, local data processing,
and cloud-based supervision to enable real-time monitoring of photovoltaic
system performance.

The architecture was experimentally validated on a prototype photovoltaic
energy platform integrating solar tracking, power electronics, and energy
storage.

---

## Embedded Monitoring Architecture

The system relies on a distributed embedded architecture combining
low-level sensor acquisition and high-level system supervision.

The monitoring architecture follows a hierarchical structure:

This architecture enables reliable acquisition, processing,
and remote visualization of photovoltaic system data.

---

## Multi-Sensor Data Acquisition

The embedded monitoring platform integrates several sensors
to characterize the photovoltaic system environment and performance.

Measured variables include:

- solar irradiance
- temperature
- humidity
- photovoltaic voltage and current
- system power output

These measurements provide a detailed representation
of the photovoltaic system operating conditions.

---

## Embedded Control and Processing

Two embedded platforms are used:

### Arduino Nano

Responsible for:

- real-time sensor acquisition
- analog-to-digital conversion
- low-level hardware interface

### Raspberry Pi

Responsible for:

- supervisory control
- data aggregation
- communication with remote services

Communication between the embedded devices is implemented
using serial and I²C communication protocols.

---

## Cloud-Based Monitoring

The monitoring platform enables remote visualization
of the photovoltaic system performance.

Main features include:

- WiFi data transmission
- cloud-based data storage
- remote system supervision
- graphical data visualization

This architecture enables continuous monitoring
and remote diagnostics of the photovoltaic installation.

---

## Experimental Validation

The embedded monitoring system was experimentally evaluated
on a real photovoltaic prototype integrating:

- a monocrystalline photovoltaic module
- a dual-axis solar tracking mechanism
- a boost converter charge controller
- lead-acid battery storage

Outdoor tests confirmed the ability of the system to monitor
the photovoltaic platform in real operating conditions.

---

## Scientific Contribution

This work contributes to the development of intelligent
photovoltaic energy systems through:

- design of an embedded monitoring architecture
- integration of multi-sensor data acquisition
- implementation of IoT-based energy supervision
- experimental validation on a real photovoltaic prototype

---

## System Architecture

Conceptual representation of the monitoring system:


This architecture illustrates the integration of embedded
systems and IoT technologies in photovoltaic energy platforms.
