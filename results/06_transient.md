# Test 6 – Transient Load Response

## Setup
- VDD = 3.3 V, VREF = 1.5 V, nominal VOUT = 1.8 V
- Load: 10 mA → 50 mA (at ~1 µs) → 10 mA (at ~5 µs)
- Both load application and load removal were observed.

![VOUT transient](images/transient_vout.png)

## Cursor readings
| Marker | Time (µs) | VOUT (V) |
|---|---|---|
| M5 | 1.55900 | 1.79404 |
| M1 | 3.03141 | 1.79134 |
| M3 | 7.00842 | 1.81231 |
| M2 | 7.52830 | ≈ 1.814 |
| M4 | 8.99943 | 1.81561 |

Extrema: minimum 1.79134 V, maximum 1.81561 V, nominal 1.80000 V.

## Load increase (10 → 50 mA)
- Undershoot = 1.80000 − 1.79134 = **8.66 mV** (0.481 % of 1.8 V)
- Minimum at ≈ 3.03141 µs; step at ≈ 1 µs → peak-response time ≈ **2.03 µs**
- The output dips because demand rises suddenly, before the loop and transient circuitry respond.

## Load decrease (50 → 10 mA)
- Overshoot = 1.81561 − 1.80000 = **15.61 mV** (0.867 %)
- Maximum at ≈ 8.99943 µs; step at ≈ 5 µs → peak-response time ≈ **4.00 µs**
- The output rises because demand drops suddenly, before the loop pulls it back.

## Total excursion
1.81561 − 1.79134 = **24.27 mV**

## ±1 % window
| Limit | Value |
|---|---|
| Lower | 1.782 V |
| Upper | 1.818 V |
| Measured range | 1.79134 – 1.81561 V |

The entire measured transient stays inside the window.

## Summary
| Parameter | Result |
|---|---|
| Nominal VOUT | 1.80000 V |
| Minimum VOUT | 1.79134 V |
| Undershoot | 8.66 mV (0.481 %) |
| Peak undershoot time | 3.03141 µs |
| Peak-response time after load increase | ≈ 2.03 µs |
| Maximum VOUT | 1.81561 V |
| Overshoot | 15.61 mV (0.867 %) |
| Peak overshoot time | 8.99943 µs |
| Peak-response time after load decrease | ≈ 4.00 µs |
| Total excursion | 24.27 mV |
| ±1 % range | 1.782 – 1.818 V |

## Inference
- The LDO keeps the output close to 1.8 V during sudden 10–50 mA load changes, with small deviations in both directions.
- The NFSSF and overshoot-stabilizer circuitry contribute to this transient behavior.
- Load removal (overshoot, 15.61 mV) causes a larger deviation than load application (undershoot, 8.66 mV).
- The times above are peak-response times (step to extremum), **not** settling times. A settling time needs a defined tolerance band and the time after which VOUT stays inside it. With the ±1 % band, the waveform never leaves the band, so settling in that sense is immediate.
