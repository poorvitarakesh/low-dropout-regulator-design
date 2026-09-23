# Transistor-Level LDO Design Using Cadence Virtuoso

## Project Status
Work in Progress

## Overview

This project focuses on the transistor-level design and simulation of a Low-Dropout Regulator (LDO) using Cadence Virtuoso and the GPDK180 technology.

The design is being developed as a collection of functional analog blocks that will eventually be integrated into the complete LDO.

## Current Progress

The following blocks have been designed and simulated so far:

- Folded-Cascode Amplifier
- Bias Circuit
- Error Amplifier
- Common-Feedback Feedforward Compensation (CFFRC)
- NFSSF
- Overshoot Voltage Stabilization Circuit

## Completed Work

### Folded-Cascode Amplifier

The folded-cascode amplifier was designed and evaluated using DC and AC simulations.

Key simulation result:

- Low-frequency gain: approximately 168 V/V
- Gain: approximately 44.5 dB
- Response: Low-pass

### Bias Circuit

The bias circuit was designed to generate the required bias conditions for the analog blocks of the LDO.

### Error Amplifier

The error-amplifier stage was developed using the designed analog amplifier and bias circuitry.

### CFFRC

The CFFRC block was designed and simulated using Cadence Virtuoso.

The DC operating point was verified and the AC response was analyzed.

A 0.5 pF compensation capacitor was used in the documented design.

### NFSSF

The NFSSF block was designed and its DC operating point was checked.

The simulation showed non-zero drain currents and sensible VGS values for the transistors.

### Overshoot Voltage Stabilization

An overshoot voltage stabilization circuit was developed as part of the LDO regulation and transient-response circuitry.

## Tools and Technology

- Cadence Virtuoso
- Cadence Spectre
- GPDK180
- Analog CMOS Design
- DC Analysis
- AC Analysis
- Transistor-Level Circuit Simulation

## Repository Structure

```text
LDO-Cadence-Virtuoso/
│
├── 02_Bias_Circuit/
│   ├── sch.oa
│   └── thumbnail_128x128.png
│
├── 04_CFFRC/
│   ├── sch.oa
│   └── thumbnail_128x128.png
│
├── 05_NFSSF/
│   ├── sch.oa
│   └── thumbnail_128x128.png
│
├── simulations/
├── results/
└── documentation/
