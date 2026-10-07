# Test 1 – DC Operating Point

## Objective
Verify output voltage, feedback voltage, transistor operating points, and that the feedback loop regulates the output.

## Setup
- VDD = 3.3 V, VREF = 1.5 V, ILOAD = 50 mA
- VREF drives the negative input of the error amplifier. The feedback node (from R0/R1 divider on VOUT) drives the positive input.
- VOUT = VREF × (1 + R0/R1). For example R0 = R1 would give 3.0 V; the ratio is chosen as R0/R1 = VOUT/VREF − 1 (here the divider gives 1.8 V).

## Simulator statistics
| Item | Value |
|---|---|
| Errors | 0 |
| Warnings | 5 |
| Notices | 6 |
| DC iterations | 36 |
| Max V(net4) | 4.028 V |
| Max I(V0:p) | 51.45 mA |

Operating-point information files were generated, so Spectre completed the analysis.

## Results
| Quantity | Value |
|---|---|
| VOUT | 1.80148 V |
| VFB | 1.50123 V |
| VREF | 1.5 V |
| Feedback error VE = VFB − VREF | 1.23 mV |
| Error as % of VREF | 0.082 % |
| Load current (target / simulated) | 50 mA / 51.45 mA |
| Load current difference | 1.45 mA (2.9 %) |

![DC operating point](images/top_level_schematic_dc_op.png)

## Inferences
- VFB ≈ VREF, so the negative-feedback loop is operating correctly.
- The small difference in current (51.45 vs 50 mA) comes from the actual operating point and the current drawn by the connected circuitry.
- The output capacitor carries no current in DC (IC = C·dV/dt = 0), so it behaves as an open circuit here and only matters in transient.
- Dropout figure from this operating point: VDD − VOUT = 3.3 − 1.8 ≈ 1.5 V. This is just the voltage across the pass device at this condition. It is **not** the minimum dropout; that is measured in the dropout test.
- The CFFRC and NFSSF blocks must not disturb the DC point. They reach valid operating points and the loop still regulates, which is what this test confirms. Their transient benefit needs the transient test.
