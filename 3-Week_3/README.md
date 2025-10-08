# 🧩 **WEEK 3 – Post-Synthesis GLS & STA Fundamentals**

### 🎯 **Objective**

To understand and perform **Gate-Level Simulation (GLS)** after synthesis, validate post-synthesis functionality, and explore **Static Timing Analysis (STA)** concepts with practical experiments using **OpenSTA**.

---

## ⚙️ **Part 1 – Post-Synthesis GLS**

### 📘 **Reference**

🔗 [GLS Reference – VSD_HDP (Day 6)](https://github.com/Ananya-KM/VSD_HDP/blob/main/Day%206.md)

---

### 🧠 **Concept Overview**

Gate-Level Simulation (GLS) ensures that the **synthesized netlist** behaves functionally the same as the **RTL design**.
It helps verify:

* ✅ Functional equivalence between RTL and synthesized logic
* ✅ Proper timing and propagation delays
* ✅ Synthesis-simulation consistency

---

### 🧪 **Steps to Perform GLS**

#### 🧩 Step 1 – Perform Synthesis

```bash
$ yosys
yosys> read_verilog baby_soc.v
yosys> synth -top baby_soc
yosys> write_verilog baby_soc_synth.v
```

#### ⚙️ Step 2 – Run Gate-Level Simulation

```bash
$ iverilog baby_soc_synth.v testbench.v
$ ./a.out
$ gtkwave dump.vcd
```

#### 🔍 Step 3 – Compare Outputs

Compare the **GLS waveform** with your **Week 2 functional simulation**.
✅ *They must match to confirm correct synthesis.*

---

### 📦 **Deliverables**

| Deliverable                     | Description                                           |
| ------------------------------- | ----------------------------------------------------- |
| 📝 **Synthesis Logs**           | Terminal logs or screenshots of synthesis completion  |
| 📈 **GLS Waveform Screenshots** | GTKWave screenshots showing post-synthesis simulation |
| ✍️ **Confirmation Note**        | Short note confirming “GLS = Functional outputs”      |

---

## 🕒 **Part 2 – Fundamentals of STA (Static Timing Analysis)**

### 📚 **Learning Resource**

If STA is new to you, take this free course *(Free for next 4 days)*:
🔗 [STA Fundamentals – Udemy](https://www.udemy.com/course/vlsi-academy-stachecks/?couponCode=F960AEDD365E0CD12546)

---

### 🧠 **Focus Areas**

* ⏱️ **Setup and Hold Checks** – Timing margins for flip-flops
* ⚖️ **Slack** – Timing margin indicating violations or safety
* 🕰️ **Clock Definitions** – Clock creation and constraints
* 🔍 **Path-Based Analysis** – Analyzing critical timing paths

---

### 🧾 **Deliverable**

📄 **One-page summary or key notes** from the STA course (bullet points allowed).
Include:

* Key definitions
* Setup & hold equations
* Slack interpretation
* Example STA flow using OpenSTA

---

## 📈 **Part 3 – Generate Timing Graphs with OpenSTA**

### 📘 **References**

* 🔗 [OpenSTA GitHub](https://github.com/The-OpenROAD-Project/OpenSTA)
* 🔗 [Example Script – Day 19](https://github.com/arunkpv/vsd-hdp/blob/main/docs/Day_19.md)
* 📄 [OpenSTA Documentation (PDF)](https://github.com/The-OpenROAD-Project/OpenSTA/blob/master/doc/OpenSTA.pdf)

---

### 🧪 **Steps to Perform**

#### 1️⃣ Load Synthesized Netlist and Constraints

```bash
read_liberty slow.lib
read_verilog baby_soc_synth.v
link_design baby_soc
read_sdc constraints.sdc
```

---

#### 2️⃣ Generate Timing Graphs and Reports

```bash
create_clock -period 10 clk
report_checks -path_delay min_max
report_tns
report_wns
```

Visualize the timing graph:

```bash
write_timing_graph -dot baby_soc_timing.dot
dot -Tpng baby_soc_timing.dot -o baby_soc_timing.png
```

---

#### 3️⃣ Analyze Results

* Identify the **critical path** (longest data path).
* Check **setup/hold** paths for violations.
* Note **slack** values for timing margins.

---





### 🌟 **Summary**

Week 3 bridges **functional verification (GLS)** with **timing verification (STA)** — essential to ensure the design is both logically correct and timing-clean before moving to layout.
