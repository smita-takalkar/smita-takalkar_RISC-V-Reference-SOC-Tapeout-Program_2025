# 🏗️ DAY 4: GLS, Blocking vs Non-Blocking, and Synthesis–Simulation Mismatch

## 🔹 1. Gate Level Simulation (GLS)

### 💡 What is GLS?

* **Gate Level Simulation (GLS):** Running the testbench on the **netlist** 🗂️ (post-synthesis design) instead of RTL.
* The **netlist** is logically the same as RTL, so the same testbench 🧪 can be reused.

---

### 🎯 Why GLS?

* ✅ To verify the **logical correctness** of the design after synthesis.
* ⏱️ To ensure that the **timing requirements** are met.
* 📐 GLS can be run with **delay annotation** (SDF – Standard Delay Format), which helps in validating **timing behavior**.

---

### 🛠️ GLS using Icarus Verilog (iverilog):

![gls using iverilog](https://github.com/user-attachments/assets/af80407d-ffc1-42a5-bbfb-8e6327bee030)

* 📌 In the above figure, the design is represented as a **netlist**.
* 🕒 If gate-level models are **delay-annotated**, GLS helps validate timing.
* 🔄 Ensures that simulation matches the synthesized hardware implementation.

---

### 🔹 Process Flow for GLS

#### 1️⃣ RTL Simulation (Behavioral Simulation)

Compile and run RTL design with testbench:

```bash
# Compile RTL design + testbench
iverilog design.v tb_design.v  

# Run the compiled simulation
./a.out  

# Open waveform in GTKWave
gtkwave tb_design.vcd
```

---

#### 2️⃣ Synthesis of Design using Yosys

Convert RTL → Netlist with **Sky130 library support**:

```bash
# Start yosys shell
yosys  

# Load standard cell library
read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025C_1v80.lib  

# Load RTL design
read_verilog design.v  

# Perform synthesis, set top module as 'design'
synth -top design  

# Technology mapping using the liberty file
abc -liberty ../lib/sky130_fd_sc_hd_tt_025C_1v80.lib  

# Write synthesized netlist to 'design_net.v' (without attributes)
write_verilog -noattr design_net.v  

# Show synthesized schematic
show
```

---

#### 3️⃣ Gate-Level Simulation (GLS)

Run simulation using **synthesized netlist** and **cell libraries**:

```bash
# Compile primitives, standard cells, synthesized netlist, and testbench
iverilog ../my_lib/verilog_model/primitives.v \
        ../my_lib/verilog_model/sky130_fd_sc_hd.v \
        design_net.v tb_design.v  

# Run the compiled simulation (now with gate-level netlist)
./a.out  

# Open waveform in GTKWave
gtkwave tb_design.vcd
```
---

Perfect 👍 I’ll keep your content exactly the same and just sprinkle **emojis** for clarity and attractiveness.

---

## 🔹 Synthesis–Simulation Mismatch

**Lecture:** SKY130RTL D4SK1 L2 – *Synthesis–Simulation Mismatch*

Sometimes, the results of **RTL simulation** 🖥️ and **post-synthesis GLS** ⚙️ may differ. Common reasons:

1. ⚠️ **Missing Sensitivity List:**

   * In RTL simulation, the simulator updates outputs only when signals in the sensitivity list change.
   * If sensitivity list is incomplete, RTL simulation may miss changes ❌, but synthesis assumes complete logic ✅ → mismatch.

2. 🔄 **Blocking vs Non-Blocking Assignments:**

   * Incorrect usage may lead to unexpected behavior when synthesized.

3. 🚫 **Non-Standard Verilog Coding:**

   * Using constructs not synthesizable or behaving differently in synthesis.

---

## 🔹  Blocking vs Non-Blocking Assignments

**Lecture:** SKY130RTL D4SK1 L3 – *Blocking and Non-Blocking Statements in Verilog*

Inside an `always` block:

* 🟢 **Blocking (`=`):**

  * Statements execute sequentially, like in C programming.
  * First statement must finish before the next one starts.
  * Example:

    ```verilog
    a = b;
    c = a;
    ```

    → `c` gets the **updated** value of `a`. ✅

* 🔵 **Non-Blocking (`<=`):**

  * All RHS values are evaluated in parallel when the block is entered.
  * Assignments to LHS happen at the end of the time step ⏳.
  * Order of statements does not matter.
  * Example:

    ```verilog
    a <= b;
    c <= a;
    ```

    → `c` gets the **old** value of `a` (before this block). ⏮️

---

### 📌 Usage Guidelines

* 🟢 **Blocking (`=`):** Best suited for **combinational logic** inside `always @(*)`.
* 🔵 **Non-Blocking (`<=`):** Always use in **sequential logic** (`always @(posedge clk)`).

---

## 🔹 Caveats with Blocking Statements

**Lecture:** SKY130RTL D4SK1 L4 – *Caveats with Blocking Statements*

* ⚠️ Using blocking assignments in sequential logic may cause **simulation–synthesis mismatches**.
* ⚡ Since hardware executes in parallel, sequential blocking statements may **not reflect real hardware behavior**.
* ✅ **Best Practice:**

  * Use **non-blocking (`<=`)** for **sequential circuits**.
  * Use **blocking (`=`)** for **combinational logic only**.

---

