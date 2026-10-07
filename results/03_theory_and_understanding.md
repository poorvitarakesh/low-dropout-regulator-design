# Theory and Understanding

The reasoning behind the design and how each block and equation relates to the simulated results.

## 1. What was simulated
The LDO consists of: bias circuit, folded-cascode error amplifier, CFFRC, NFSSF with overshoot stabilizer, PMOS pass transistor, feedback resistor network, output capacitor and load.

## 2. Supply and references
VDD = 3.3 V, VREF = 1.5 V (to the error amplifier's negative input), ILOAD = 50 mA. The feedback node is connected to the positive input, so in regulation VFB ≈ VREF.

## 3. Feedback network and output voltage
R0 is between VOUT and the feedback node, R1 between the feedback node and ground.

- VFB = VOUT × R1 / (R0 + R1)
- With VFB ≈ VREF: VOUT = VREF × (R0 + R1) / R1 = VREF × (1 + R0/R1)
- Choosing resistors: R0/R1 = VOUT/VREF − 1
- Example: R0 = R1 gives VOUT = 1.5 × 2 = 3.0 V. For 1.8 V, R0/R1 = 1.8/1.5 − 1 = 0.2.

## 4. Error amplifier operation
The folded-cascode amplifier compares VIN− = VREF and VIN+ = VFB. The error is VE = VFB − VREF. In regulation VE ≈ 0. It amplifies this small difference and drives the pass transistor control. Measured: VE = 1.23 mV (0.082 %).

## 5. Pass transistor
The PMOS pass device has its source at VDD, drain at VOUT and gate driven by the regulation circuitry. It acts as a variable resistance / current source. More load current → the loop moves the gate to conduct more; less load current → the opposite.

## 6. Loop regulation principle
VOUT → feedback divider → VFB → compared with VREF → error amplifier → control/bias circuitry → pass transistor → VOUT.

- If VOUT falls, VFB < VREF, the amplifier increases pass-transistor conduction, more current flows, VOUT rises.
- If VOUT rises, VFB > VREF, the pass-transistor current decreases, VOUT falls.

This negative feedback stabilizes the output.

## 7. Block roles
- **Bias circuit:** generates bias voltages that set operating currents and regions for the error amplifier, CFFRC and NFSSF.
- **CFFRC:** a fast signal path to help the slower main loop (error amp + pass transistor) react quickly. In DC it must not disturb the operating point.
- **NFSSF and overshoot stabilizer:** extra feedback/control around the pass-transistor path to improve transient response and reduce overshoot. In DC it must reach a valid point and give a valid gate voltage.
- **Output capacitor:** reduces output variation, supplies transient current, reduces high-frequency noise, helps stability when compensated, stores charge. DC current is zero (IC = C·dVOUT/dt = 0).

## 8. Transistor operating regions
- NMOS saturation: VDS ≥ VGS − VTH, with VOV = VGS − VTH.
- PMOS (magnitudes): VSD ≥ VSG − |VTH|, with VOV = VSG − |VTH|.
- Saturation applies when VDS (or VSD) ≥ VOV. It matters most for gain devices in the error amplifier and bias circuits.

## 9. MOSFET equations
- Saturation current: ID = ½ μn Cox (W/L) VOV² (NMOS); |ID| = ½ μp Cox (W/L) VOV² (PMOS)
- With channel-length modulation: ID = ½ μ Cox (W/L) VOV² (1 + λVDS)
- Transconductance: gm = ∂ID/∂VGS = μ Cox (W/L) VOV = 2ID/VOV
- Output resistance: ro ≈ 1/(λ ID)
- Stage gain: Av ≈ gm ro

Higher gm gives higher gain and better ability to regulate. In the folded-cascode amplifier the cascode devices raise the output resistance and so the gain. High error-amplifier gain reduces steady-state regulation error, and the measured ~44.5 dB gain is consistent with the small VE.

## 10. Regulation figures of merit (definitions used)
- **Line regulation** = ΔVOUT / ΔVIN (mV/V). A smaller change means better line regulation. Measured by sweeping VDD and recording VOUT.
- **Load regulation** = ΔVOUT / ΔIOUT (mV/mA), measured by sweeping the load current.
- **Dropout voltage** = VIN − VOUT at the point where VOUT can no longer stay regulated. It must be found by sweeping VIN downward at the required load current, not read from a single operating point.
- **Peak-response time** is the time from a load step to the output extremum. It is not a settling time.
