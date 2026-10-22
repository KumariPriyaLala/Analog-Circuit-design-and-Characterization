[github_readme.md](https://github.com/user-attachments/files/33828092/github_readme.md)
# Multi-Stage Analog Signal Conditioning Unit & Op-Amp Characterization

A comprehensive analog circuit design, simulation, and analysis project covering multi-stage BJT amplifiers, discrete MOSFET differential amplifiers, Op-Amp closed-loop topologies, and high-CMRR instrumentation amplifier architectures.

---

## 📌 Executive Summary
This project focuses on the design, simulation, and parameter extraction of discrete and integrated analog front-end circuits. The objective is to analyze small-signal dynamic range, frequency response, non-ideal Op-Amp DC parameters, and differential noise rejection capabilities across several cascaded and feedback-controlled topologies.

---

## 🚀 Key Features & Circuit Architectures

### 1. Multi-Stage BJT Common-Emitter (CE) Amplifier
* **Topology:** Two-stage RC-coupled Common-Emitter BJT amplifier.
* **Frequency Analysis:** Evaluated $f_{L}$ (lower cutoff) and $f_{H}$ (upper cutoff) frequencies to calculate overall gain-bandwidth product (GBW).
* **Gain Characteristics:** Observed multi-stage voltage loading effects and stage interaction.

### 2. Discrete MOSFET Differential Amplifier
* **Topology:** Differential pair utilizing discrete N-channel MOSFETs with a tail current source/resistor.
* **Performance Metrics:**
  * **Differential Gain ($A_d$):** ~70.7
  * **Common-Mode Gain ($A_{cm}$):** ~0.59 mV/V
  * **Common-Mode Rejection Ratio (CMRR):** ~101.56 dB

### 3. Integrated Operational Amplifier Analysis (LM741 / Standard Op-Amp)
* **Feedback Configurations:** Designed and verified Inverting, Non-Inverting ($A_v = 30 \text{ to } 50$), and Voltage Follower (Buffer) configurations.
* **DC Parameter Characterization:**
  * **Input Bias Current ($I_B$):** $\approx 64.4\text{ nA}$
  * **Input Offset Current ($I_{io}$):** $\approx 18.3\text{ nA}$
  * **Input Offset Voltage ($V_{ios}$):** $\approx -38\,\mu\text{V}$

### 4. 3-Op-Amp Instrumentation Amplifier (INA)
* **Architecture:** Two-stage instrumentation topology consisting of an input buffering differential gain stage cascaded with a difference amplifier.
* **Function:** Precision extraction of weak sensor signals in high common-mode noise environments.

---

## 📊 Schematic & Simulation Workflows

All circuits were synthesized and characterized using **SPICE / NI Multisim**:

```
[ Sensor / AC Input ] ──► [ Discrete MOSFET Diff-Pair ] ──► [ Multi-Stage BJT Amp ] ──► [ 3-Op-Amp INA ] ──► [ Output ]
                                                                     │
                                                      [ DC Parameter Extraction ]
```

### Key Simulation Types Performed
* **DC Sweep / Operating Point Analysis:** Biasing verification ($I_{CQ}$, $V_{CEsat}$, $V_{GS}$).
* **AC Small-Signal Analysis:** Bode plots for bandwidth, gain margin, and phase response.
* **Transient Analysis:** Total Harmonic Distortion (THD) and dynamic range clipping boundaries.

---

## 🛠️ Tools & Technologies Used
* **EDA / Simulation:** NI Multisim / LTspice / SPICE Engine
* **Components:** BJTs, N-Channel MOSFETs, LM741 Op-Amps, Passive RLC Networks
* **Instrumentation Simulated:** Oscilloscope, Bode Plotter, Digital Multimeter (DMM)

---

## 📁 Repository Structure

```
.
├── schematics/            # SPICE / Multisim circuit files (.ms14, .asc)
├── plots/                 # Frequency response Bode plots and transient waveforms
├── docs/                  # Design calculations and DC offset parameter derivations
└── README.md              # Project documentation
```

---

## 🎓 Key Engineering Takeaways
1. **Gain vs. Bandwidth Trade-off:** Cascading stages increases overall voltage gain at the expense of system bandwidth due to pole accumulation.
2. **Noise Suppression via High CMRR:** Differential amplification significantly reduces common-mode power supply and environmental noise.
3. **Offset Mitigation:** Understanding non-ideal $I_B$ and $V_{ios}$ parameters is essential for high-precision DC measurement applications.
