# CMOS Low-Dropout Regulator (LDO)

Transistor-level design and simulation of a CMOS Low-Dropout Regulator using **Cadence Virtuoso** with the **GPDK180** technology library.

## Overview

This project implements a 1.8 V LDO from a 3.3 V supply using a 1.5 V reference. The design includes the bias circuit, folded-cascode error amplifier, capacitance-free fast-response circuit (CFFRC), negative-feedback source follower (NFSSF), overshoot stabilization circuit, PMOS pass transistor, and feedback network.

The design has been evaluated through DC operating-point and transient simulations, along with load regulation, line regulation, quiescent-current, and dropout analysis.

## Specifications

| Parameter         |            Value |
| ----------------- | ---------------: |
| Technology        |          GPDK180 |
| Input Voltage     |            3.3 V |
| Reference Voltage |            1.5 V |
| Output Voltage    |            1.8 V |
| Load Current      |         10–50 mA |
| Design Tool       | Cadence Virtuoso |
| Simulator         |  Cadence Spectre |

## Circuit Blocks

### Bias Circuit

Generates the bias voltages required by the analog blocks and establishes their operating currents.

### Folded-Cascode Error Amplifier

Compares the feedback voltage with the reference voltage and generates the control signal for the regulation loop.

### CFFRC

Provides a fast-response path to improve the regulator's response to rapid changes in operating conditions.

### NFSSF and Overshoot Stabilization

Provides additional control around the pass-transistor path and contributes to the transient response of the regulator.

### PMOS Pass Transistor

Controls the current delivered from the supply to the output.

## Simulation Results

### DC Operating Point

At VDD = 3.3 V, VREF = 1.5 V and ILOAD = 50 mA:

* VOUT = 1.80148 V
* VFB = 1.50123 V
* Feedback error = 1.23 mV
* Reference error = 0.082%

The simulated load current was approximately 51.45 mA.

### Load Regulation

The load current was varied from 10 mA to 50 mA.

| Load Current |      VOUT |
| -----------: | --------: |
|        10 mA | 1.80162 V |
|        20 mA | 1.80157 V |
|        30 mA | 1.80153 V |
|        40 mA | 1.80160 V |
|        50 mA | 1.80146 V |

**Load regulation: 0.004 mV/mA (4 mV/A)**

Output variation over the tested range: **0.16 mV**

### Line Regulation

VDD was varied from 2.5 V to 3.3 V at a constant 50 mA load.

|   VDD |      VOUT |
| ----: | --------: |
| 2.5 V | 1.80040 V |
| 2.7 V | 1.80065 V |
| 2.9 V | 1.80092 V |
| 3.1 V | 1.80120 V |
| 3.3 V | 1.80148 V |

**Line regulation: 1.35 mV/V**

### Quiescent Current

At no external load:

* VDD = 3.3 V
* VREF = 1.5 V
* ILOAD = 0 A
* IQ = 0.957 mA

The output rises close to the supply voltage under the no-load condition. The relatively high quiescent current is an area for further optimization.

### Dropout

Dropout was evaluated at a constant 50 mA load by reducing the input supply.

Using a 1% deviation from the nominal 1.8 V output as the criterion:

* Estimated dropout threshold: 1.907 V
* Estimated dropout voltage: approximately 107 mV

### Transient Load Response

The load was stepped from:

**10 mA → 50 mA → 10 mA**

at VDD = 3.3 V and VREF = 1.5 V.

| Parameter              |    Result |
| ---------------------- | --------: |
| Minimum VOUT           | 1.79134 V |
| Undershoot             |   8.66 mV |
| Undershoot             |    0.481% |
| Maximum VOUT           | 1.81561 V |
| Overshoot              |  15.61 mV |
| Overshoot              |    0.867% |
| Total output excursion |  24.27 mV |

The measured output remained within the defined ±1% range of 1.782 V to 1.818 V.

## Results Summary

| Parameter                 |          Result |
| ------------------------- | --------------: |
| Nominal VOUT              |           1.8 V |
| Load Range                |        10–50 mA |
| Load Regulation           |     0.004 mV/mA |
| Line Regulation           |       1.35 mV/V |
| Quiescent Current         |        0.957 mA |
| Estimated Dropout         | ~107 mV @ 50 mA |
| Load-Step Undershoot      |         8.66 mV |
| Load-Step Overshoot       |        15.61 mV |
| Total Transient Excursion |        24.27 mV |

## Tools

* Cadence Virtuoso
* Cadence Spectre
* GPDK180
* CMOS transistor-level design
* DC and transient simulation

## Project Status

**Simulation completed. Layout pending.**

The schematic-level design and simulation analysis are complete. The next stage is physical layout followed by DRC, LVS, parasitic extraction, and post-layout simulation.

## Future Work

* Complete transistor-level layout
* DRC and LVS verification
* Parasitic extraction
* Post-layout simulation
* Further optimization of quiescent current and line regulation
