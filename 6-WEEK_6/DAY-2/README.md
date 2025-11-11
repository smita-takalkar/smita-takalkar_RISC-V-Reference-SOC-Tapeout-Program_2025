# 🧠 **DAY 2 – Good Floorplan vs Bad Floorplan & Introduction to Library Cells**

---

## 🧩 **Chip Floor Planning Considerations**

---

### 🔹 **14 – Utilization Factor and Aspect Ratio**

#### ⚙️ **Steps in Physical Design Floorplan**

1. Define **width** and **height** of the **core** and **die**
2. Consider dimensions of **standard cells** (FFs, latches, logic gates)
3. Calculate **area occupied** by the netlist on the silicon wafer

---

#### 🧱 **Core vs Die**

| Term     | Description                                                                            |
| -------- | -------------------------------------------------------------------------------------- |
| **Core** | Section of the chip where fundamental logic is placed                                  |
| **Die**  | Small semiconductor piece containing the core and periphery; actual fabricated silicon |

---

#### 📐 **Determining Chip Dimensions**

* Place all logical cells inside the core.
* If all area is occupied → **100% Utilization**

```text
Utilization Factor = Area Occupied by Netlist / Total Area of Core
```

> ✅ *In practice, utilization is kept around **50–60%** for routing and optimization margin.*

If `Utilization Factor < 1`, more cells can be added or optimization can be done.

---

#### 📏 **Aspect Ratio**

```text
Aspect Ratio = Height of Core / Width of Core
```

| Condition        | Shape            |
| ---------------- | ---------------- |
| Aspect Ratio = 1 | Square Chip      |
| Aspect Ratio < 1 | Rectangular Chip |

---

### 🧱 **15 – Concept of Pre-Placed Cells**

* Large netlist → divided into **blocks** or **IP modules** (e.g. memory, clock gating, comparators, MUXes).
* Blocks with defined I/O pins act as **black boxes**.
* Their physical arrangement forms the **Floorplan**.

> 🧩 **Pre-Placed Cells** are user-defined blocks positioned **before** automated placement & routing.
> Their location remains **fixed** throughout the design flow.

---

### ⚡ **16 – Decoupling Capacitors**

#### 🔋 **Why They’re Needed**

During circuit switching:

* The design draws **peak current (Iₚₑₐₖ)**
* Due to **Rdd** and **Ldd**, voltage drops occur (Vdd → Vdd’)
* If Vdd’ < noise margin, logic errors occur

---

#### 💡 **Noise Margin**

* Logic `0` and `1` must stay within **NML** and **NMH**
* Values between these are **undefined states**

---

#### 🧠 **Solution: Add Decoupling Capacitors (Cd)**

* During switching → circuit draws current from **Cd**
* Power network replenishes Cd later
* Reduces:

  * Voltage droop
  * Crosstalk
  * Switching noise

> 🛡️ Decoupling capacitors stabilize **local power supply** near active switching circuits.

---

### ⚡ **17 – Power Planning**

#### ⚠️ **The Problem**

* When many gates switch simultaneously:

  * Discharging → **Ground Bounce**
  * Charging → **Vdd Drop (IR Drop)**

---

#### ✅ **The Solution**

* Use **multiple power supply lines**
* Create **power meshes** to evenly distribute current
* Results in:

  * Lower IR drop
  * Stable ground
  * Better power integrity

---

### 🎯 **18 – Pin Placement & Logical Cell Placement Blockage**

#### 📌 **Pin Placement**

* Connectivity between gates = **Netlist (VHDL/Verilog)**
* **I/O pins** placed between **die** and **core**
* **Inputs** → Left/Top
* **Outputs** → Right/Bottom
* **Clock pins** → Thicker (drive FFs; lower resistance)

---

#### 🚫 **Logical Cell Placement Blockage**

* Space between I/O pins is **blocked** for other cells
* Floorplan is now ready for the **Placement & Routing** stage

---

### 🧮 **19 – Steps to Run Floorplan Using OpenLANE**

After synthesis, the **next step** is floorplanning.
In this stage, we set:

* Die area & core area
* Aspect ratio
* Utilization factor
* I/O cell placement
* Power distribution
* Macro placement

> 🧱 **Standard cells are not placed here** — that’s done in the **Placement** stage.


floorplan.tcl:
<img width="1280" height="768" alt="Screenshot from 2025-11-11 17-41-20" src="https://github.com/user-attachments/assets/f2d8956e-715f-4ee7-be45-20a63e6f4696" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 17-41-43" src="https://github.com/user-attachments/assets/fc05c71d-194d-4c8a-96bc-91504490b51e" />

config.tcl
<img width="1280" height="768" alt="Screenshot from 2025-11-11 17-43-10" src="https://github.com/user-attachments/assets/c305d292-7fea-4351-82f6-755fd0471081" />

**Command:**

```bash
% run_floorplan
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 17-45-54" src="https://github.com/user-attachments/assets/ba04353b-2496-434d-8ab5-fa9cd2078b0c" />

4-ioPlacer.log
<img width="1280" height="768" alt="Screenshot from 2025-11-11 17-48-59" src="https://github.com/user-attachments/assets/476ac13e-e710-463d-a2b2-b1b24cd03238" />

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-08-58" src="https://github.com/user-attachments/assets/54752ca2-a432-4d9e-8c17-bb892cc33690" />

<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-11-11" src="https://github.com/user-attachments/assets/137fe884-90e6-4e66-92a2-4816ee09788a" />

---


### 🌐 **26 – Congestion-Aware Placement using RePlAce**
```bash
% run_placement
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-14-15" src="https://github.com/user-attachments/assets/c559d0db-ea2a-4739-82eb-9b27f5608806" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-14-26" src="https://github.com/user-attachments/assets/fb41e8cc-4e14-4fed-8efc-40d0cffe2332" />

Placement done :
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-34-01" src="https://github.com/user-attachments/assets/72707b27-27ce-4b78-ad2a-cbf125db5607" />

To view placement: 
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-42-20" src="https://github.com/user-attachments/assets/e6ceb4ce-abbf-4c56-9537-28648d9fa8bd" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-44-09" src="https://github.com/user-attachments/assets/c0543e88-cf90-4926-b9f3-e7546526a580" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 18-42-39" src="https://github.com/user-attachments/assets/42756a64-ed18-4017-badf-cf847e346a1b" />

---
ioPlacer supports 4 pin strategies we can also change it 
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-07-20" src="https://github.com/user-attachments/assets/2b5b4085-c8df-4952-8817-856cf1fc6fc9" />
here env(FP_IO_MODE) 1, Means cells are placed randomly at equidistant

to change the cell strategy :
```bash
% set ::env(FP_IO_MODE) 2
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-08-24" src="https://github.com/user-attachments/assets/482243a0-411e-4535-b86f-b19c0538bd92" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-09-37" src="https://github.com/user-attachments/assets/a0fd03c2-bac6-4a49-b940-27ace6a1e4c3" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-10-53" src="https://github.com/user-attachments/assets/de9f7abf-420e-411a-a339-269900ceba3e" />


