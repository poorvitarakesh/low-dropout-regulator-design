# Test 2 – Load Regulation

## Setup
Load current varied 10 mA to 50 mA with VDD (3.3 V) and VREF (1.5 V) fixed.

## Data
| ILOAD (mA) | VOUT (V) |
|---|---|
| 10 | 1.80162 |
| 20 | 1.80157 |
| 30 | 1.80153 |
| 40 | 1.80160 |
| 50 | 1.80146 |

## Calculation
- VOUT,max = 1.80162 V, VOUT,min = 1.80146 V
- ΔVOUT = 0.16 mV
- ΔIOUT = 50 − 10 = 40 mA
- Load regulation = 0.16 mV / 40 mA = **0.004 mV/mA = 4 mV/A**
- Variation = 0.16 mV / 1.8 V × 100 = **0.0089 %**

## No-load condition (not part of the calculation)
At ILOAD = 0 mA, VOUT = 3.29982 V. This point is excluded from the 10–50 mA calculation because regulation is evaluated over the specified load range. It does show that the design does not hold 1.8 V at zero load (see quiescent-current test).

## Inference
Over 10–50 mA the output moves by only about 0.0089 %, so load regulation is very good within the specified range.
