# Summary, Inferences and Open Issues

## Final results (top-level LDO)

| Parameter | Result |
|---|---|
| Technology | GPDK180 |
| VDD / VREF / VOUT | 3.3 V / 1.5 V / 1.8 V |
| VOUT at 50 mA | 1.80148 V |
| VFB | 1.50123 V (error 1.23 mV, 0.082 %) |
| Load range | 10–50 mA |
| Load regulation | 0.004 mV/mA (4 mV/A), 0.0089 % variation |
| Line regulation (2.5–3.3 V) | 1.35 mV/V |
| Quiescent current (no load) | 957.253 µA |
| Dropout (1 %, 50 mA) | ≈ 107 mV (VDD ≈ 1.907 V) |
| Undershoot (10 → 50 mA) | 8.66 mV (0.481 %) |
| Overshoot (50 → 10 mA) | 15.61 mV (0.867 %) |
| Total transient excursion | 24.27 mV |
| Transient within ±1 % (1.782–1.818 V) | Yes |

## Block results

| Block | Result |
|---|---|
| Error amplifier | ~168 V/V (~44.5 dB), low-pass |
| CFFRC | DC: 0 errors. AC: ~70–85 mV flat, rises sharply near 1 GHz |
| NFSSF | Valid DC operating point, non-zero currents, sensible VGS |

## Comparison with the reference paper

| Metric | Paper | This work |
|---|---|---|
| Line regulation | 0.28 mV/V | 1.35 mV/V |
| Quiescent current | 20.4–36.5 µA | 957.253 µA |

## Overall inferences
1. The feedback loop works: VFB tracks VREF within 1.23 mV and VOUT stays near 1.8 V.
2. Load regulation is excellent over 10–50 mA (0.16 mV total change).
3. Line regulation is good but about 5× worse than the paper's.
4. Dropout is small (~107 mV at 50 mA), with fast loss of regulation below ~1.9 V.
5. Transient behavior stays inside ±1 % for the 10 ↔ 50 mA step. Load removal gives the bigger deviation.
6. Quiescent current is high and the output is not regulated at zero load.

## Open issues / things to be aware of
- **No-load behavior:** VOUT rises to 3.29982 V at 0 mA, so regulation only holds within the tested load range.
- **High IQ:** 957 µA versus the paper's ~20–36 µA. Bias and amplifier currents need optimizing.
- **Line regulation** does not match the paper.
- **Dropout is interpolated** between 1.90 V and 1.91 V; simulate directly at about 1.907 V for a precise value.
- **Peak-response times** are not settling times.
- **M3 marker value:** the original report's table lists 1.81321 V at 7.00842 µs, but the plot marker reads 1.81231 V. This folder uses the plot value (1.81231 V). Check which is correct.
- **Layout pending:** DRC, LVS, parasitic extraction and post-layout simulation are future work.
