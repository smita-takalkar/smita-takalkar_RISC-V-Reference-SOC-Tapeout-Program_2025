# 🧠 **Day 1 – Inception of Open-Source EDA, OpenLANE, and SKY130PDK**

## 🔬 **LAB 1 – Design Preparation and Synthesis**

**Commands Executed:**

```bash
# Navigate to OpenLANE working directory
cd Desktop/work/tools/openlane_working_dir/openlane_old/

# Launch Docker environment
docker

# Check current directory
bash-4.2$ pwd

# Start OpenLANE in interactive mode
bash-4.2$ ./flow.tcl -interactive

% package require openlane 0.9

# Prepare design
% prep -design picorv32a
```

🧠 **Note:**
The `prep` command sets up the file system and merges **cell-level LEF** and **technology LEF** into a single file for design integration.

---

### ▶️ **Run Synthesis**

```bash
% run_synthesis
```

After synthesis, OpenLANE generates the **gate-level netlist** and various reports (area, timing, and cell count).

---

## 📊 **Synthesis Result Characterization**

| Parameter      | Value      |
| -------------- | ---------- |
| Total Cells    | 14,876     |
| D Flip-Flops   | 1,613      |
| **Flop Ratio** | **10.84%** |

**Formula:**
[
\text{Flop Ratio} = \frac{\text{No. of D Flip-Flops}}{\text{Total Cells}} \times 100 = \frac{1613}{14876} \times 100 = 10.84%
]

This metric helps estimate **sequential logic density** in the design — an important factor in timing and power analysis.


---

## 🏁 **Outcome**

By the end of Day 1, we:

* Understood how open-source EDA tools collaborate in a complete digital flow
* Explored OpenLANE’s environment setup and synthesis
* Learned to interpret synthesis reports and calculate key design metrics

---

