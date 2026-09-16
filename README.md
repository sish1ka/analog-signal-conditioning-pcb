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

![Op-Amp Supply Voltage](Documentation/opamp-supply-voltage.png)

## Files

- `LTspice/` — circuit simulations
- `KiCad/` — schematic and PCB design files
- `Documentation/` — design images and results
- `BOM/` — bill of materials
