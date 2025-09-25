DAY 1 
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


