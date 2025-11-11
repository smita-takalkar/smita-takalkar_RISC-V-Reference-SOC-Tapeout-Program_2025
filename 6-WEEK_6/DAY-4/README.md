## 🧭 **DAY 4 – Pre-Layout Timing Analysis and Importance of a Good Clock Tree**

---

# ⚙️ **Timing Modelling Using Delay Tables**

---

### 🔹 **57 – Convert Grid Info to Track Info**

* Define **track pitch** and **offset** for routing layers.
* Align standard-cell pins to routing tracks for optimal wire routing.

---

### 🧩 **58 – Convert Magic Layout to Standard-Cell LEF**

* Extract cell boundary, pins, and obstruction data from Magic layout.
* Generate **Library Exchange Format (LEF)** to use in PnR tools.

```bash
magic -T sky130A.tech
lef write vsdinv.lef
```

---

### 🧠 **59 – Timing Libraries & Adding a New Cell in Synthesis**

* **.lib timing files** describe cell delays and power.
* Include new cell (e.g., `vsdinv`) in synthesis by adding its LEF and .lib paths in the OpenLANE configuration.

---

### 📈 **60 – Introduction to Delay Tables**

* Delay depends on **input transition** and **output load capacitance**.
* Delay tables store this 2-D relationship in `.lib` format.

```text
cell_rise(delay_template_3x3) {
  values ( (0.02, 0.03, 0.05), (0.04, 0.06, 0.08), (0.06, 0.09, 0.12) );
}
```

---

### 🧮 **61 – Delay Table Usage (Part 1)**

* Used during **Static Timing Analysis (STA)** to calculate pin-to-pin delays.
* Enables accurate pre-layout timing estimation.

---

### 🧠 **62 – Delay Table Usage (Part 2)**

* Helps tools choose proper **cell sizes** and **buffer strength** during optimization.
* Crucial for achieving timing closure.

---

### 🔧 **63 – Configure Synthesis Settings to Fix Slack & Include vsdinv**

* Edit synthesis configuration to insert the new inverter cell.
* Adjust clock period or drive strength to **fix negative slack**.

---

# ⏱️ **Timing Analysis with Ideal Clocks using OpenSTA**

---

### 🧩 **64 – Setup Timing Analysis & Flip-Flop Setup Time**

* Setup time = minimum time data must be stable **before clock edge**.
* Violation ⇒ data arrives too late.

---

### 🕒 **65 – Clock Jitter & Uncertainty**

* **Clock jitter:** variation in clock arrival time.
* **Uncertainty:** includes jitter + skew margin.
* Added to timing equations for safe analysis.

---

### ⚙️ **66 – Configure OpenSTA for Post-Synthesis Timing**

```bash
sta pre_sta.conf
read_liberty timing.lib
read_verilog synth.v
read_sdc constraints.sdc
report_checks
```

---

### 🚀 **67 – Optimize Synthesis to Reduce Setup Violations**

* Resize gates or buffer long paths.
* Reduce data path delay to meet setup constraints.

---

### 🧰 **68 – Perform Basic Timing ECO**

* **ECO (Engineering Change Order):** small logic change to fix timing without re-synthesizing the full design.

---

# 🕸️ **Clock Tree Synthesis (CTS) – TritonCTS & Signal Integrity**

---

### 🌳 **69 – Clock Tree Routing & Buffering (H-Tree Algorithm)**

* Distributes clock signal evenly with minimal skew.
* Uses **H-Tree structure** for symmetric delay paths.

---

### ⚡ **70 – Crosstalk & Clock Net Shielding**

* Shield clock nets with power/ground lines to prevent noise coupling.
* Maintain consistent delay across branches.

---

### 🧱 **71 – Run CTS using TritonCTS**

```bash
run_cts
```

* Automatically inserts buffers and routes the clock tree.

---

### 🔍 **72 – Verify CTS Runs**

* Review generated clock tree report.
* Check **skew**, **latency**, and **buffer insertion count**.

---

# ⏱️ **Timing Analysis with Real Clocks using OpenSTA**

---

### 🧩 **73 – Setup Timing with Real Clocks**

* Analyze setup timing using post-CTS netlist.
* Real clock delays and skews are included.

---

### 🧠 **74 – Hold Timing Analysis**

* Hold time = minimum time data must stay stable **after clock edge**.
* Fix by inserting small buffers in short paths.

---

### 🧮 **75 – Analyze Timing with Real Clocks**

```bash
sta post_cts.conf
report_checks -path_delay min_max
```

---

### ⚙️ **76 – Execute OpenSTA with Correct Timing Libraries & CTS Assignment**

* Load **post-CTS netlist**, **clock tree SDC**, and **.lib** for all corners.

---

### 📊 **77 – Impact of Larger CTS Buffers**

* Larger buffers improve skew but may increase setup delay.
* Analyze trade-off between **setup** and **hold** slack.

---



