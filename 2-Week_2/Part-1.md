# Week 2 – BabySoC Fundamentals & Functional Modelling

## My Notes - Summary of BabySoC Fundamentals

### 🔹 What is SoC?

* A **System-on-Chip (SoC)** = complete computing system packed inside a single chip.
* Combines **CPU + Memory + Peripherals + Interconnect**.
* Advantage → smaller, faster, consumes less power compared to separate components.
* Examples → processors inside smartphones, IoT devices, embedded boards.

---

### 🔹 Components of a Typical SoC

1. **CPU (Core)** → executes instructions, brain of the chip.
2. **Memory** → program + data storage (SRAM/DRAM/Flash).
3. **Peripherals** → UART, GPIO, timers etc. for external communication.
4. **Interconnect/Bus** → backbone for CPU ↔ Memory ↔ Peripherals communication.

---
# 🔎 Introduction to VSDBabySoC  

**VSDBabySoC** is a small yet powerful **RISC-V based SoC**, designed as a simplified platform to explore and test SoC concepts.  
Its primary goal is to:  
- Integrate and validate **three open-source IP cores** together for the first time.  
- Provide a platform to **calibrate and interact with analog parts** of the design.  

### 🧩 Components of VSDBabySoC  
1. **RVMYTH Microprocessor**  
   - A simple RISC-V based CPU introduced in a workshop by **RedwoodEDA** and **VSD**.  
   - Built in just **5 days** by students (even middle-schoolers!) using **TL-Verilog (TLV)** for rapid development.  
   - Ongoing contributions are open-source, encouraging community-driven development.  

2. **8x PLL (Phase-Locked Loop)**  
   - A control system that generates a stable output clock signal, phase-locked to the input reference clock.  
   - Essential for **clock generation and synchronization** within the SoC.  

3. **10-bit DAC (Digital-to-Analog Converter)**  
   - Converts **digital signals → analog signals**.  
   - Widely used in communication systems for generating transmission signals.  
   - Enables VSDBabySoC to interface with external **analog devices**.  

---
<img width="2270" height="1260" alt="vsdbabysoc_block_diagram" src="https://github.com/user-attachments/assets/d49cc262-ce4e-4b68-b96d-b589dc7c6c86" />


### 🔹 Why BabySoCis a simplified model for learning SoC concepts?

* It’s a **learning-friendly version** of SoC.
* Has **minimal blocks** (small CPU, simple memory, basic I/O).
* Helps me:

  * Understand **block-level interactions** clearly.
  * Trace **data flow** without too much complexity.
  * Build a strong **foundation before diving into real SoCs**.


---

### 🔹 Functional Modelling – Role in Design Flow

* Comes **before RTL and Physical Design**.
* Purpose:

  * Check **basic functionality** of the SoC.
  * Validate that CPU, memory, and peripherals interact as expected.
  * Find design-level mistakes early (cheaper to fix now than later).
* Tools:

  * **Icarus Verilog (iverilog)** → simulate the Verilog code.
  * **GTKWave** → visualize waveforms, debug signal transitions.

Basically → **functional model = reference blueprint** before jumping into actual RTL implementation.

---



## ✅ Key Takeaways

* SoC = CPU + Memory + Peripherals + Interconnect → all in 1 chip.
* BabySoC is a **minimal learning SoC**, easy to simulate & debug.
* Functional modelling = **first step** in SoC design flow.
* Tools: **iverilog + GTKWave** = simulate + view waveforms.
* BabySoC learning prepares me for **real SoC RTL + VLSI flow**.

---
