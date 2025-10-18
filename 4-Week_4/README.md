# 🧠 Week 4 – Ngspice Sky130 Workshop Documentation

### *CMOS Device Behavior, SPICE Simulation & Robustness Evaluation*

---

## 📘 Overview

* Focus on **NMOS, PMOS, and CMOS inverter** behavior using **Ngspice** with **Sky130 PDK**.
* Objective: Understand **device-level operation**, **SPICE modeling**, and **circuit robustness** through simulations.


---

## 📅 Day 1 – NMOS Basics & SPICE Introduction

* Importance of **SPICE simulations** in verifying delay and behavior before fabrication.
* Study of **NMOS transistor structure** – terminals (G, D, S, B), p-substrate, n+ diffusion, oxide layers.
  <img width="1920" height="1080" alt="Screenshot 2025-10-15 152603" src="https://github.com/user-attachments/assets/e68a340a-1fb1-4b93-aacd-2e79653f1e26" />

* Concept of **threshold voltage (Vth)** and **depletion region formation**.
  <img width="1920" height="1080" alt="Screenshot 2025-10-15 232527" src="https://github.com/user-attachments/assets/9d7787f7-79bf-434a-8788-2afa4bc611a2" />

* **Regions of operation:** Cutoff, Resistive (Linear), and Saturation.
  

## ⚙️ SPICE Netlist Syntax and Meaning

In SPICE, a **netlist** describes the circuit components and their interconnections.
Each line defines one component with its name, connected nodes, model, and parameters.

---

### **1️⃣ MOSFET Declaration**

```
M1 vdd n1 0 0 nmos W=1.8u L=1.2u
```

**Explanation:**

| Element    | Meaning                                         |
| ---------- | ----------------------------------------------- |
| **M1**     | MOSFET name (M = MOSFET, “1” = instance number) |
| **vdd**    | Drain terminal                                  |
| **n1**     | Gate terminal                                   |
| **0**      | Source terminal (connected to ground)           |
| **0**      | Bulk/Substrate terminal (connected to ground)   |
| **nmos**   | Model name defined in the technology/model file |
| **W=1.8u** | Width of MOSFET gate (in micrometers)           |
| **L=1.2u** | Length of MOSFET gate (in micrometers)          |

✅ **Purpose:** Defines an **NMOS transistor** connected between `vdd`, `n1`, and ground, using parameters from the model library.

---

### **2️⃣ Resistor Declaration**

```
R1 in n1 55
```

**Explanation:**

| Element | Meaning                                             |
| ------- | --------------------------------------------------- |
| **R1**  | Resistor name (R = resistor, “1” = instance number) |
| **in**  | First terminal node                                 |
| **n1**  | Second terminal node                                |
| **55**  | Resistance value (in ohms)                          |

✅ **Purpose:** Connects a **55 Ω resistor** between nodes `in` and `n1`.

---

### **3️⃣ Voltage Source Declaration**

```
Vdd vdd 0 2.5
Vin in 0 2.5
```

**Explanation:**

| Element       | Meaning                                  |
| ------------- | ---------------------------------------- |
| **Vdd / Vin** | Voltage source name (V = voltage source) |
| **vdd / in**  | Positive terminal node                   |
| **0**         | Negative terminal node (ground)          |
| **2.5**       | Voltage value (in volts)                 |

✅ **Purpose:**

* `Vdd` provides a **2.5 V supply** to the circuit.
* `Vin` applies a **2.5 V input signal** between node `in` and ground.

---

### 🧩 Summary

* Each SPICE component line follows a consistent format:

  ```
  ElementName  Node1  Node2  ...  [Model]  [Parameters]
  ```
* **Node names** define connections between elements.
* **Model names** (like `nmos`, `pmos`) reference device characteristics from the **technology model file**.
* **Parameters** (like `W`, `L`, `R`, or `V`) specify individual component properties.

---

* **Model parameters:** Vto, γ (gamma), Kn’, λ (lambda).
* **Hands-on focus:**

  * Id–Vds and Id–Vgs plots for NMOS.
  * Defining model libraries using `.MODEL` and `.LIB`.
  * First SPICE run using Sky130 NMOS parameters.

---

## ⚡ Day 2 – Velocity Saturation & CMOS Inverter Fundamentals

* Concept of **long-channel vs short-channel behavior**.
* **Velocity saturation** effect at high electric fields.
* **Drain current modeling** for lower technology nodes.
* Introduction to **CMOS inverter operation** and **VTC (Voltage Transfer Characteristic)** analysis.
* Conversion of gate-source and drain-source voltages for PMOS and NMOS.
* **Labs and simulations:**

  * Id–Vgs curves for long and short channel devices.
  * Vt extraction from simulation.
  * Plotting CMOS inverter VTC using load curves.

---

## 🔍 Day 3 – Switching Threshold & Dynamic Simulation

* Definition and importance of **switching threshold (Vm)**.
* Analytical relation between **Vm and (W/L)p / (W/L)n** ratios.
* **SPICE deck setup** for CMOS inverter.
* **Static and dynamic behavior analysis** using `.DC` and `.TRAN` simulations.
* Observation of **rise/fall times** and **delay behavior**.
* **Impact of transistor sizing:** increasing PMOS width shifts Vm and improves balance.
* **Practical labs:**

  * Static VTC extraction and threshold measurement.
  * Transient analysis of inverter switching behavior.

---

## 🔈 Day 4 – CMOS Noise Margin & Robustness Evaluation

* Concept of **Noise Margin High (NMH)** and **Noise Margin Low (NML)**.
* **Noise margin equations** and their significance in digital reliability.
* Study of **VTC curve slopes** and intersection points for determining noise margins.
* **Effect of PMOS width** variation on NMH/NML balance.
* **SPICE simulations:**

  * Extraction of NMH and NML from inverter VTC.
  * Analysis of inverter robustness against noise variations.

---

## ⚙️ Day 5 – Power Supply & Device Variation Robustness

* **Power supply variation effects:** analyzing circuit behavior for different VDD levels.
* **Advantages and drawbacks of low VDD operation:**

  * Reduced power but slower switching and smaller noise margins.
* **Device variations** due to manufacturing processes:

  * Etching, oxide thickness, and doping variations.
* **Smart SPICE simulations** to analyze sensitivity to model parameters.
* **Key labs:**

  * Supply variation analysis using `.DC` sweeps.
  * Device variation experiments and parameter sensitivity study.

---

## 🧩 Key Learnings

* Strong understanding of **NMOS/PMOS operation** and **threshold voltage behavior**.
* Ability to construct and interpret **SPICE netlists**.
* Detailed insight into **CMOS inverter operation**, **VTC**, and **switching behavior**.
* Understanding of **noise margins**, **supply robustness**, and **device variation effects**.
* Practical skill in verifying **simulation data** with **analytical models**.
* Familiarity with **Sky130 model parameters** and **Ngspice workflow**.

---

## 🛠️ Tools 

* **Ngspice** – circuit simulation tool.
* **Sky130 PDK** – open-source CMOS process design kit.
* **Linux environment / terminal-based simulation setup**.




---
