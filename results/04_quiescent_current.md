# Test 4 – Quiescent Current

## Setup
VDD = 3.3 V, VREF = 1.5 V, ILOAD = 0 A. DC operating-point analysis.

## Results
| Quantity | Value |
|---|---|
| VOUT (no load) | 3.29982 V |
| IVDD | −957.253 µA |
| IQ (magnitude) | **957.253 µA ≈ 0.957 mA** |

The negative sign is only Cadence's current reference direction.

## Comparison with the paper
| | Quiescent current |
|---|---|
| Paper | ~20.4 – 36.5 µA |
| This simulation | 957.253 µA |

## Inference
- With no load the output rises to about VDD (VOUT ≈ VDD), so the present design does not hold the nominal 1.8 V at zero load.
- IQ is far higher than the reference implementation, meaning the internal/bias current consumption is much larger than it should be.
- This is an area for optimization (mainly bias and amplifier currents), not a reproduction of the paper's value.
