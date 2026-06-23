# Digital Weighing Scale (Pre-Alpha)

## Overview

One day, after returning home from the hostel for the holidays, I found myself stepping onto an old weighing scale after eating far more than I probably should have. While staring at the number it displayed, a question popped into my head: **How does this machine know my weight so accurately?** The question disappeared as quickly as it arrived, only to return when I watched a coffee enthusiast using a precision scale capable of measuring coffee grounds to two decimal places. That curiosity led me down a rabbit hole of strain gauges, load cells, Wheatstone bridges, and signal conditioning. This project is my attempt to understand how a modern digital weighing scale works by designing one from scratch.

This repository is my attempt to understand how a digital weighing scale works by studying its sensing chain, selecting the required components, and beginning the PCB design process. At its current stage, this project is just hardware planning.

---

## Project Goal

The purpose of this project is to understand how force can be converted into a measurable electrical signal and eventually into a digital output.

This project currently explores:

* Strain gauge technology
* Load cell operation
* Wheatstone bridge fundamentals
* Signal amplification using HX711
* Embedded system architecture
* Power regulation
* PCB planning in KiCad

---

## Current Stage

This project is currently in **pre-alpha**.

What has been done so far:

* Researched the working principle of digital weighing scales
* Studied strain gauge and load cell operation
* Selected all major components
* Defined the complete sensing chain
* Started the PCB schematic layout in KiCad

What has **not** been done yet:

* Component interconnections are incomplete
* PCB routing has not started
* BOM has not been generated
* STM32 firmware has not been written
* Calibration routines have not been implemented
* Simulation and hardware testing have not been performed

---

## Proposed System Architecture

```text
Weight Applied
      ↓
20 kg Single-Point Load Cell
      ↓
Wheatstone Bridge Output
      ↓
HX711 Load Cell Amplifier
      ↓
STM32F103C8T6 Microcontroller
      ↓
0.96" OLED Display
```

---

## Selected Components

### 20 kg Single-Point Load Cell
Chosen as the primary force sensing element. The load cell contains strain gauges arranged in a Wheatstone bridge configuration, producing a small differential voltage when deformed.

### HX711 Load Cell Amplifier
Selected for:
* High precision amplification
* 24-bit ADC conversion
* Easy microcontroller interfacing

This component is essential because the load cell output is too small to be directly processed.

### STM32F103C8T6
Chosen because of prior familiarity with the Blue Pill platform.
Responsibilities will include:
* Reading HX711 output
* Processing weight values
* Handling display communication
* Future filtering and calibration

### 0.96" OLED Display
Chosen as the output interface. Will communicate over I²C. Mostly because I wanted to use my I²C knowledge properly for once.

### Power Section

Planned:
* USB-C input (5V)
* AMS1117 3.3V regulator

To provide stable operating voltage for the system.


## Planned Development Roadmap

### Phase 1

* Complete schematic connections
* Verify circuit integrity
* Generate BOM

### Phase 2

* Finish PCB layout
* Perform ERC and DRC checks
* Prepare fabrication files

### Phase 3

* Write STM32 firmware
* Interface HX711
* Interface OLED

### Phase 4

* Implement calibration
* Add tare functionality
* Add filtering

### Phase 5

* Fabricate and test hardware

---

## Limitations

At this stage, this project is only a design and research exercise. It does not yet function as a working weighing scale. No physical or software validation has been performed yet.

---

## Author's Note

This repository is less about building something perfect and more about understanding how an everyday device works. Right now, this is mostly curiosity, component selection, half-baked knowledge from five odd seniors and unfinished wires.

But every project starts there.
