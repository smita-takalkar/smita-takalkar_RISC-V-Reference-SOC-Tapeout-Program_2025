# DAY 1 
# SKY130 RTLD1SK1 L1 – Introduction to Icarus Verilog (iverilog) and Testbench

## Introduction
In RTL design, the implementation of specifications must be verified through simulation.  
In this course, we will use the open-source simulator **Icarus Verilog (iverilog)** to simulate our designs and validate their functionality against given specifications.  
Waveform analysis will be performed using **GTKWave**.

---

## Simulator
- The simulator checks the RTL design for adherence to the specifications by executing the Verilog description.  
- In this course, the simulator used is **iverilog**.

---

## Design
- The **Design** refers to the Verilog code (single or multiple files) that describes the intended functionality.  
- A design generally consists of one or more **primary inputs** and one or more **primary outputs**.  

---

## Testbench
- A **Testbench** provides the required **stimulus (test vectors)** to the design in order to verify its behavior.  
- It does not represent hardware and does not have any primary inputs or outputs.  
- Its purpose is to apply inputs and observe outputs of the design.

---

## How the Simulator Works
- The simulator continuously monitors changes on the input signals.  
- When an input changes, the corresponding outputs are re-evaluated.  
- If there is no change in input, there is no change in output.
  <img width="1710" height="827" alt="Screenshot 2025-09-25 142240" src="https://github.com/user-attachments/assets/6166483d-be14-4886-986a-8ec255dc1931" />


---

## iverilog Based Simulation Flow
1. Write the design code in Verilog.  
2. Write the corresponding testbench.  
3. Compile using **iverilog**:  
  <img width="1920" height="1080" alt="Screenshot 2025-09-25 142544" src="https://github.com/user-attachments/assets/fa534c41-5710-4cc8-80c8-7e4b21cec87f" />

 ---

# Introduction to Yosys and Logic Synthesis

This document summarizes the basics of **Yosys** and **logic synthesis** in the context of digital design using **SKY130 PDK**.

---

## 1. What is a Synthesizer?

A **synthesizer** is a tool used to convert **RTL (Register Transfer Level)** code into a **netlist**.

* **RTL** → Behavioral description of the design (in Verilog HDL).
* **Netlist** → Gate-level representation of the design using standard cells from the technology library (`.lib`).

In this course, we use **Yosys** as the synthesizer.

---

## 2. Yosys Flow

![yosys_flow.png](attachment:73866c11-8cc8-4ed2-8be0-842b1734cd06:26629192-68e7-40f7-b0de-c5ebb423633a.png)

* The RTL design is translated into gates and mapped using the standard cells present in the `.lib`.
* The final output is a **netlist file**.

---

## 3. Verification of Synthesis

![image.png](attachment:5e9cc936-53eb-4f72-8bd8-280600fe6ab0:image.png)

* The **primary inputs and outputs** remain the same between RTL and synthesized netlist.
* The same testbench can be reused for both RTL and netlist verification.

---

## 4. What is Logic Synthesis?

Logic synthesis is the process of converting **RTL design** into **gate-level design**.

### Steps:

1. RTL code (behavioral description in Verilog).
2. Translate into gates.
3. Connect gates to form the equivalent circuit.
4. Generate the **netlist**.
![iverification.png](attachment:00e0d4a5-275c-4897-8661-ff0888e90943:image.png)

---

## 5. The `.lib` File

A **library (`.lib`)** contains a collection of basic logic gates.

* Different versions (flavors) of the same gate:

  * 2-input AND (slow, medium, fast).
  * 3-input AND (slow, medium, fast).
  * 4-input AND (slow, medium, fast).

### Why different flavors?

* The **propagation delay** of a logic path determines the **maximum speed** of the circuit.
* Faster cells = higher performance, but more **power** and **area**.
* Slower cells = lower performance, but save **power** and **area**.

---

## 6. Timing Constraints

For correct operation, the clock period must satisfy:

$$
T_{clk} > T_{cqA} + T_{combi} + T_{setupB}
$$

Where:

* $T_{cqA}$ = Propagation delay of FF_A.
* $T_{combi}$ = Delay of combinational circuit.
* $T_{setupB}$ = Setup time requirement of FF_B.

Maximum clock frequency:

$$
f_{clk,max} = \frac{1}{T_{clk,min}}
$$

---

## 7. Need for Slow Cells

To avoid **hold violations**, the following condition should hold:

$$
T_{hold} < T_{cqA} + T_{combi}
$$

* Sometimes **slower cells** are required to balance timing and ensure correct operation.
* Thus, libraries provide both **fast** and **slow** cells.

---

## 8. Trade-offs: Faster vs Slower Cells

* **Load in digital circuits** = Capacitance.
* Faster charging/discharging → Lower delay.

### Faster Cells:

* Wide transistors (more current).
* **Low delay**, but **high power** and **large area**.

### Slower Cells:

* Narrow transistors.
* **Higher delay**, but **low power** and **small area**.

---

## 9. Cell Selection and Constraints

* The synthesizer must be guided to select an **optimum mix** of cell flavors.
* **Too many fast cells** → High area & power.
* **Too many slow cells** → Sluggish design, may not meet performance.

➡️ This guidance to the synthesizer is called **constraints**.

---






