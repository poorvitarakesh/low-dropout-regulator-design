# Test 3 – Line Regulation

## Setup
VDD swept 2.5 V to 3.3 V, ILOAD = 50 mA, VREF = 1.5 V.

## Data
| VDD (V) | ILOAD (mA) | VOUT (V) |
|---|---|---|
| 2.5 | 50 | 1.80040 |
| 2.7 | 50 | 1.80065 |
| 2.9 | 50 | 1.80092 |
| 3.1 | 50 | 1.80120 |
| 3.3 | 50 | 1.80148 |

## Calculation
- VOUT,max = 1.80148 V, VOUT,min = 1.80040 V, ΔVOUT = 1.08 mV
- ΔVDD = 3.3 − 2.5 = 0.8 V
- Line regulation = 1.08 mV / 0.8 V = **1.35 mV/V**

## Comparison with the paper
| | Line regulation |
|---|---|
| Paper | 0.28 mV/V |
| This simulation | 1.35 mV/V |

## Inference
Line regulation is good (about a millivolt of change over a 0.8 V supply change) but does not reproduce the paper's 0.28 mV/V. The difference can come from transistor sizing, device models, component values, simulation conditions and implementation differences. Improving it is listed as future work.
