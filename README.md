# Analog Signal-Conditioning PCB

## Overview

This project involves the design of a small analog signal-conditioning
circuit intended to convert a low-level sensor signal into a
0–3.3 V signal suitable for microcontroller ADC interfacing.

The circuit was designed and simulated using LTspice and implemented
as a 2-layer PCB using KiCad.

## Objectives

- Design an analog amplification stage
- Implement low-pass filtering
- Maintain an ADC-compatible 0–3.3 V output
- Verify circuit behavior through simulation
- Design and verify a 2-layer PCB

## Tools

- LTspice
- KiCad

## Circuit Design

[schematic image will go here]

## LTspice Simulation

### Frequency Response

[Bode plot will go here]

### Transient Response

[transient plot will go here]

## PCB Design

### PCB Layout

[PCB screenshot will go here]

### 3D View

[3D PCB screenshot will go here]

## Results

Simulation results and final design performance will be documented here.

## Verification Procedure

The circuit was verified using a node-by-node transient analysis.
Each verification step checks a specific electrical condition before
proceeding to the next stage.

### 1. Op-Amp Supply Voltage Verification

**Purpose:**  
Verify that the op-amp is receiving the required +5 V and −5 V supply
voltages before evaluating signal behavior.

**Procedure:**
1. Run a transient analysis in LTspice.
2. Probe the op-amp positive supply node (`V+`).
3. Probe the op-amp negative supply node (`V-`).
4. Confirm that the supply voltages are approximately +5 V and −5 V.
5. Verify that both supply voltages remain stable throughout the simulation.

**Expected Result:**

| Parameter | Positive Supply (`V+`) | Negative Supply (`V-`) |
|---|---:|---:|
| Supply voltage | +5 V | −5 V |
| Supply stability | Stable | Stable |

**Measured Result:**  
`V+ = 5.00 V`  
`V- = −5.00 V`

**Result:** Pass

![Op-Amp Supply Voltage](Documentation/test-01-opamp-supply.png)

### 2. Voltage Gain Verification

**Purpose:**  
Verify that the measured voltage gain agrees with the theoretical gain determined by the feedback resistors.

**Theoretical Gain:**

$$
A_v = 1 + \frac{R_2}{R_1}
$$

$$
A_v = 1 + \frac{20k\Omega}{10k\Omega} = 3
$$

**Procedure:**
1. Measure the input signal amplitude from the transient analysis.
2. Measure the output signal amplitude.
3. Calculate the measured voltage gain using:

$$
A_v = \frac{V_{out}}{V_{in}}
$$

4. Compare the measured gain with the theoretical gain of 3×.

**Expected Result:**

| Parameter | Expected |
|---|---:|
| Theoretical gain | 3× |
| Measured gain | ~3× |
| Gain error | Minimal |

**Measured Result:**  
`Theoretical gain = 3.00×`  
`Measured gain = Vout / Vin = 3.00×`

**Result:** Pass

![Voltage Gain Verification](Documentation/test-02-gain.png)

### 3. Input and Op-Amp Output Verification

**Purpose:**  
Verify that the input signal has the expected amplitude and frequency, and that the op-amp produces the expected amplified output.

**Procedure:**
1. Run a transient analysis for 100 ms in LTspice.
2. Probe the input node of the op-amp.
3. Verify that the input signal is a 50 mV amplitude, 60 Hz sine wave centered around 0 V.
4. Probe the op-amp output node.
5. Verify that the output waveform follows the input waveform with the expected 3× voltage gain.
6. Compare the measured input and output amplitudes.

**Expected Result:**

| Parameter | Input | Op-Amp Output |
|---|---:|---:|
| Peak amplitude | 50 mV | ~150 mV |
| Peak-to-peak voltage | 100 mV | ~300 mV |
| Frequency | 60 Hz | 60 Hz |
| DC offset | 0 V | 0 V |
| Voltage gain | — | ~3× |

**Measured Result:**  
`Vin = 50 mV peak`  
`Vout = 150 mV peak`  
`f = 60 Hz`  
`Gain = Vout / Vin ≈ 3`

**Result:**  Pass

![Input and Op-Amp Output Verification](Documentation/test-03-opamp-output.png)

### 4. Filter Response Verification

**Purpose:**  
Verify the frequency response of the output low-pass filter and confirm that the measured cutoff frequency agrees with the theoretical value.

**Theoretical Cutoff Frequency:**

$$
f_c = \frac{1}{2\pi R_3 C_1}
$$

For:

- `R3 = 10 kΩ`
- `C1 = 10 nF`

$$
f_c = \frac{1}{2\pi(10k\Omega)(10nF)}
$$

$$
f_c \approx 1.59\text{ kHz}
$$

**Procedure:**
1. Run an AC analysis in LTspice.
2. Plot the output voltage magnitude.
3. Identify the frequency where the output magnitude decreases by approximately 3 dB from its passband value.
4. Compare the measured cutoff frequency with the theoretical value.

**Expected Result:**

| Parameter | Expected |
|---|---:|
| Filter type | Low-pass |
| Theoretical cutoff | ~1.59 kHz |
| Measured cutoff | ~1.59 kHz |
| Attenuation at cutoff | ~−3 dB |

**Measured Result:**  
`fc ≈ 1.59 kHz`

**Result:** ✅ Pass

![Filter Frequency Response](Documentation/test-04-filter-response.png)

## Files

- `LTspice/` — circuit simulations
- `KiCad/` — schematic and PCB design files
- `Documentation/` — design images and results
- `BOM/` — bill of materials
