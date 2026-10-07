# Test 5 – Dropout Voltage

## Setup
ILOAD = 50 mA, VREF = 1.5 V, nominal VOUT = 1.8 V. VDD reduced step by step to find the lowest input at which the output is still regulated.

## Data
| VDD (V) | ILOAD (mA) | VOUT (V) |
|---|---|---|
| 2.50 | 50 | 1.80040 |
| 2.40 | 50 | 1.80030 |
| 2.30 | 50 | 1.80020 |
| 2.20 | 50 | 1.80012 |
| 2.10 | 50 | 1.79995 |
| 2.00 | 50 | 1.79836 |
| 1.92 | 50 | 1.79099 |
| 1.91 | 50 | 1.78617 |
| 1.90 | 50 | 1.77861 |
| 1.80 | 50 | 1.67141 |
| 1.70 | 50 | 1.55180 |

## Criterion
1 % deviation from 1.8 V = 0.018 V, so VOUT,min = 1.782 V.

- At VDD = 1.91 V: VOUT = 1.78617 V > 1.782 V → still within 1 %.
- At VDD = 1.90 V: VOUT = 1.77861 V < 1.782 V → outside 1 %.

So the dropout threshold lies between 1.90 V and 1.91 V. Linear interpolation gives VDD,drop ≈ 1.907 V.

## Result
VDO = VDD,drop − VOUT,nom ≈ 1.907 − 1.8 ≈ 0.107 V → **≈ 107 mV at 50 mA**.

## Inference
- Regulation is held over a wide range: at VDD = 2.0 V, VOUT is still about 1.798 V.
- Below ~1.9 V the output drops quickly (1.67141 V at 1.8 V, 1.55180 V at 1.7 V), which is clearly the dropout region.
- Note: 107 mV is an interpolated estimate between the 1.90 V and 1.91 V simulations. A direct simulation around 1.907 V would give a more precise value.
