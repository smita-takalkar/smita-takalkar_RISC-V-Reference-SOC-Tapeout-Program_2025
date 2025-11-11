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
![docker_start](https://github.com/user-attachments/assets/5925158d-7495-4c20-90e8-8cc918dd2279)

![design_prep](https://github.com/user-attachments/assets/003070f8-969e-4b1a-b090-ba63f44c1ee9)

![WhatsApp Image 2025-11-11 at 12 35 05 PM (5)](https://github.com/user-attachments/assets/1abf98ea-5759-49c6-a771-704e5f812a49)

![synthesis_successful](https://github.com/user-attachments/assets/006c893b-4503-4867-bd87-07396c237ed7)

![WhatsApp Image 2025-11-11 at 12 35 05 PM (4)](https://github.com/user-attachments/assets/f9470a99-23e0-4e16-a4f5-0a4c5646ba36)

![WhatsApp Image 2025-11-11 at 12 35 05 PM (3)](https://github.com/user-attachments/assets/fbd719ef-990c-4db0-ade5-a5d1f1233613)
![picorv32a synthesis v](https://github.com/user-attachments/assets/80b1ad61-b1f5-4e37-be0a-005948e07cc3)
![WhatsApp Image 2025-11-11 at 12 35 05 PM (2)](https://github.com/user-attachments/assets/43f4b2be-b246-433f-921c-44622ed82a1e)

![WhatsApp Image 2025-11-11 at 12 35 05 PM (1)](https://github.com/user-attachments/assets/6bd09d56-99e1-42fe-a4f2-6e30c7ed75ed)
![WhatsApp Image 2025-11-11 at 12 35 05 PM](https://github.com/user-attachments/assets/1a608e70-fc87-46a5-896e-d3e3ead2e392)

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
**Formula:**
Flop Ratio = (Number of D Flip-Flops / Total Number of Cells) × 100 

Flop Ratio = (1613 / 14876) × 100 = 10.84%

| Parameter      | Value      |
| -------------- | ---------- |
| Total Cells    | 14,876     |
| D Flip-Flops   | 1,613      |
| **Flop Ratio** | **10.84%** |

This metric helps estimate **sequential logic density** in the design — an important factor in timing and power analysis.


---

## 🏁 **Outcome**

By the end of Day 1, we:

* Understood how open-source EDA tools collaborate in a complete digital flow
* Explored OpenLANE’s environment setup and synthesis
* Learned to interpret synthesis reports and calculate key design metrics

---

