# Week 2 – BabySoC Fundamentals & Functional Modelling

## 🎯 Objective  
To build a **solid understanding of SoC fundamentals** and practice **functional modelling of BabySoC** using open-source simulation tools:  
- [Icarus Verilog](http://iverilog.icarus.com/) for compiling & simulating Verilog  
- [GTKWave](http://gtkwave.sourceforge.net/) for waveform analysis  

---
##This week's task are divided into two parts as:
## 📘 Part 1 – Theory (Conceptual Understanding)  

### Topics to Focus On  
- **What is a System-on-Chip (SoC)?**  
  A SoC integrates multiple components such as CPU, memory, peripherals, and interconnects on a single chip, enabling efficient and compact designs.  

- **Components of a Typical SoC**  
  - **CPU** → Processing unit  
  - **Memory** → Stores instructions/data  
  - **Peripherals** → Interfaces like UART, GPIO, DAC/ADC  
  - **Interconnect** → Communication backbone (bus/NoC)  

- **Why BabySoC?**  
  BabySoC is a **simplified RISC-V based SoC** designed for learning.  
  - Easy to understand for beginners  
  - Integrates **RVMYTH CPU + PLL + DAC**  
  - Helps grasp SoC design flow without the complexity of large SoCs  

- **Role of Functional Modelling**  
  - First step before RTL and physical design  
  - Ensures correctness of design intent and module interactions  
  - Reduces errors in later synthesis and layout stages  

### 📄 Deliverable  
- A **1–2 page write-up** summarizing SoC design fundamentals and BabySoC’s role in this learning journey.  
- This document will be included in the `theory/` folder of this repo.  

---

## 🧪 Part 2 – Labs (Functional Modelling)  

Hands-on modelling and simulation using BabySoC project.  

**Steps:**  
1. Clone the BabySoC project repo  
2. Compile Verilog modules with **iverilog**  
3. Run simulation and generate `.vcd` waveforms  
4. Analyze results in **GTKWave**:  
   - Reset operation  
   - Clocking  
   - Dataflow between modules  
5. Document observations with **waveform screenshots + explanations**  

### 📦 Deliverables  
- Simulation logs  
- `.vcd` waveform dumps  
- Screenshots (Reset, Clocking, Dataflow)  
- Short explanation for each  

---

