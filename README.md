# Analog Signal Conditioning & Circuit Design Suite

[![NI Multisim](https://img.shields.io/badge/NI%20Multisim-003366?style=for-the-badge&logo=National-Instruments&logoColor=white)](https://www.ni.com/en-in/shop/electronic-test-instrumentation/application-software-for-electronic-test-and-instrumentation-category/what-is-multisim.html)
[![SPICE](https://img.shields.io/badge/SPICE-Simulation-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/SPICE)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

## Project Overview
This repository contains a comprehensive design, simulation, and parametric characterization suite of fundamental analog circuit building blocks developed using **NI Multisim** and **SPICE** simulation tools. 

The project consolidates five core analog systems—ranging from multi-stage discrete transistor amplifiers to non-ideal operational amplifier (Op-Amp) models and specialized instrumentation amplifiers—into a unified signal processing pipeline.

---

## Technical Summary & Highlights

### 1. Two-Stage RC-Coupled CE Amplifier
* **Architecture:** Cascaded BJT Common Emitter (CE) stages utilizing self-bias voltage dividers and emitter bypass capacitors.
* **Specifications:** $V_{CC} = 12\text{ V}$, $I_C = 3\text{ mA}$, $\beta = 100$, operating with a small-signal input $V_{in} = 0.5\text{ mVpk}$ at $10\text{ kHz}$.
* **Key Results:** Achieved high dynamic voltage gain across cascaded stages and evaluated the lower/upper $-3\text{ dB}$ cutoff frequencies ($f_L, f_H$) and bandwidth through AC frequency sweeps.

### 2. MOSFET Differential Amplifier
* **Architecture:** Discrete NMOS differential pair using matched `2N7000` transistors biased with a $2\text{ mA}$ tail current source under $\pm 15\text{ V}$ dual supplies.
* **Modes Analyzed:**
  * **Differential Mode ($A_d$):** $V_{id} = 20\text{ mVpk}$ differential signal yielding $A_d = 70.7$.
  * **Common Mode ($A_{cm}$):** $V_{icm} = 10\text{ mVpk}$ in-phase signal yielding $A_{cm} = 0.5903\text{ m}$.
* **Performance:** Extracted a **Common-Mode Rejection Ratio (CMRR)** of **$101.56\text{ dB}$**, demonstrating high common-mode noise suppression.

### 3. Closed-Loop Op-Amp Topologies (IC 741)
* **Topologies Designed & Analyzed:**
  * **Voltage Follower:** Unity gain ($A_v = 1$) for high-impedance buffer isolation.
  * **Inverting Amplifier:** Designed for closed-loop gain $A_v = -50$ ($R_f = 50\text{ k}\Omega, R_1 = 1\text{ k}\Omega$), producing a $180^\circ$ phase shift.
  * **Non-Inverting Amplifier:** Designed for closed-loop gain $A_v = 50$ ($R_f = 50\text{ k}\Omega, R_1 = 1.02\text{ k}\Omega$), producing an in-phase amplified output.

### 4. DC Characteristics & Non-Ideal Op-Amp Parameters (IC 741)
* **Parameter Extraction:** Quantified internal DC non-idealities through high-resistance feedback topologies:
  * **Input Bias Currents:** $I_B^+ = 55.305\text{ nA}$, $I_B^- = 73.592\text{ nA}$ (Average $I_B = 64.45\text{ nA}$).
  * **Input Offset Current ($I_{io}$):** $18.287\text{ nA}$.
  * **Input Offset Voltage ($V_{ios}$):** $-38\ \mu\text{V}$.

### 5. Three Op-Amp Instrumentation Amplifier
* **Architecture:** Dual non-inverting input buffer stage combined with a difference amplifier stage ($U_1, U_2, U_3$).
* **Design & Gain:** Set for an overall differential voltage gain $A_v = 30$ ($A_v = \left[1 + \frac{2 R_f}{R_g}\right] \times \frac{R_2}{R_1}$).
* **Key Results:** Verified differential input signal extraction with negligible common-mode interference ($V_o \approx 597.74\text{ mVpk}$ for $V_{in} = 19.95\text{ mVpk}$, corresponding to $A_v = 29.95$).

---

## Repository Structure

```text
├── closed_loop_opamp.ms14     # Voltage Follower, Inverting, & Non-Inverting Op-Amps
├── instrumentation_amp.ms14   # 3-Op-Amp Instrumentation Amplifier (Av = 30)
├── mosfet_diff_amp.ms14       # MOSFET Differential Pair (Differential & Common Mode)
├── opamp_dc_char.ms14         # Op-Amp Input Bias & Offset Parameter Measurement Setup
├── two_stage_ce_amp.ms14      # Two-Stage RC-Coupled BJT Amplifier
├── .gitattributes             # GitHub Linguist language association file
└── README.md                  # Project documentation
