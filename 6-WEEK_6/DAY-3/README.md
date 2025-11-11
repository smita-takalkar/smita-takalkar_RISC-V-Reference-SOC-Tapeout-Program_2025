# ⚙️ **DAY 3 – Design Library Cell using Magic Layout and ngspice Characterization**

---

## 🧪 **Labs for CMOS Inverter ngspice Simulations**

---

### 🔹 **33 – IO Placer Revision**

* Review placement of **I/O pins** in relation to core and die.
* Ensure signal integrity and minimum routing congestion.
* ioPlacer supports 4 pin strategies we can also change it 
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-07-20" src="https://github.com/user-attachments/assets/2b5b4085-c8df-4952-8817-856cf1fc6fc9" />
here env(FP_IO_MODE) 1, Means cells are placed randomly at equidistant

to change the cell strategy :
```bash
% set ::env(FP_IO_MODE) 2
```
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-08-24" src="https://github.com/user-attachments/assets/482243a0-411e-4535-b86f-b19c0538bd92" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-09-37" src="https://github.com/user-attachments/assets/a0fd03c2-bac6-4a49-b940-27ace6a1e4c3" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-10-53" src="https://github.com/user-attachments/assets/de9f7abf-420e-411a-a339-269900ceba3e" />

<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-29-25" src="https://github.com/user-attachments/assets/a4fd993b-2736-4ad3-a4a3-6461d28fe77d" />

---

### 🧾 **34 – SPICE Deck Creation for CMOS Inverter**

* A **SPICE deck** defines the circuit elements and their interconnections.
* Example includes:

  * **MOSFET models** from PDK
  * **Power supply definitions (VDD, GND)**
  * **Input stimulus (VIN)**
  * **Output node connection**

---

### ⚡ **35 – SPICE Simulation Lab for CMOS Inverter**

* Run ngspice simulation on the created CMOS inverter deck.
* Observe:

  * **Transfer characteristics (Vout vs Vin)**
  * **Switching behavior**
  * **Rise and fall delays**

**Command Example:**

```bash
ngspice inverter.spice
plot v(out) vs v(in)
```

---

### ⚙️ **36 – Switching Threshold (Vm)**

* **Switching Threshold (Vm)** = Input voltage at which **Vout = Vin**.
* It indicates the inverter’s balance point and affects **noise margin**.

**Determined by:**
Plotting Vout vs Vin and locating the intersection point.

---

### ⏱️ **37 – Static & Dynamic Simulation of CMOS Inverter**

* **Static Simulation:**

  * Used to obtain **VTC (Voltage Transfer Characteristics)**.
  * Determines **Vm**, **VOH**, **VOL**, **NMH**, **NML**.
* **Dynamic Simulation:**

  * Apply **pulsed input** to observe **rise/fall times**, **propagation delay**, and **power dissipation**.

---

### 💻 **38 – Lab Steps to Git Clone vsdstdcelldesign**

Download standard cell design repository for further layout and characterization.

```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
cd vsdstdcelldesign
```

---

## 🧱 **Inception of Layout – CMOS Fabrication Process**

---

### 🧩 **39 – Create Active Regions**

* Define **active areas** where transistors will be formed.
* Active regions are diffused regions for **NMOS** and **PMOS** creation.

---

### 🌊 **40 – Formation of N-Well and P-Well**

* **N-Well:** for PMOS transistors
* **P-Well:** for NMOS transistors
* Provides electrical isolation and biasing capability.

---

### ⚡ **41 – Formation of Gate Terminal**

* Gate terminal is formed by **polysilicon deposition** over a thin oxide layer.
* Controls the flow of carriers between source and drain.

---

### ⚛️ **42 – Lightly Doped Drain (LDD) Formation**

* **LDD regions** are added to reduce **electric field intensity** near the drain.
* Helps minimize **hot carrier effects** and device degradation.

---

### 🔋 **43 – Source–Drain Formation**

* Heavily dope the source and drain regions using **ion implantation**.
* Establishes proper transistor conductivity.

---

### 🔗 **44 – Local Interconnect Formation**

* First-level interconnects used to connect nearby devices.
* Formed using **tungsten or titanium nitride** layers.

---

### 🧱 **45 – Higher Level Metal Formation**

* Multiple **metal layers (M1, M2, M3, etc.)** connect cells and blocks across the chip.
* Separated by dielectric and connected through **vias**.

---

### 💡 **46 – Lab: Introduction to Sky130 Basic Layers, Layout & LEF using Inverter**

* Understand how **Sky130 layers** (nwell, pwell, poly, diffusion, metal layers) are defined in Magic.
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-16-21" src="https://github.com/user-attachments/assets/671d671f-cd73-4b98-889b-54187c580df6" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-19-05 (1)" src="https://github.com/user-attachments/assets/2e3388b3-1230-4762-b0b6-c5080fe13b2e" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-26-31" src="https://github.com/user-attachments/assets/b5004871-fc19-4ed3-b7d1-2b71497cc0cb" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-26-44" src="https://github.com/user-attachments/assets/07c25d56-2bd4-4c01-afe8-be7636fd3531" />
To know the name select the part and in Tkcon window
```bash
% what
```
nmos:
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-40-06" src="https://github.com/user-attachments/assets/e02dc5d8-5659-420e-be51-d8047b8b485e" />
pmos:
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-40-40 (2)" src="https://github.com/user-attachments/assets/86b123a1-228d-4031-97fe-912db2509610" />

For checking connectivity: press S 3 times, it highlghts all the connected parts
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-45-24 (1)" src="https://github.com/user-attachments/assets/4e16427a-680d-4821-b7b7-4a172f3e21c0" />
<img width="1280" height="768" alt="Screenshot from 2025-11-11 19-45-36 (1)" src="https://github.com/user-attachments/assets/ed4b3434-4b9e-4610-8775-16b364817069" />

Licon is the connect between locali and metal1 
nsubstratecontact ensures the connectivity between nwell and locali 

Steps to Check for DRC Errors:
1. Click and select any part
2. Click on DRC Tab
3. DRC Find next error
4. In Tkcon window it mentions the error if there is any
   Final design should be DRC error free 




* Generate **Layout Exchange Format (LEF)** files for cell integration.

---

### 🧰 **47 – Lab Steps to Create Standard Cell Layout & Extract SPICE Netlist**
To know the logical function of Inverter we need to extarct the design in SPICE and do simulation in SPICE
1. Create the inverter layout in Magic.
2. Label **input, output, and power pins**.
3. Extract the **SPICE netlist** for simulation.

   ```bash
   extract all
   ext2spice cthresh 0 rthresh 0
   ext2spice
   ```
<img width="1920" height="923" alt="VirtualBox_vsdworkshop_11_11_2025_21_52_28" src="https://github.com/user-attachments/assets/4c4c4b56-9cde-4510-8f70-2e17181314e8" />
<img width="1920" height="923" alt="VirtualBox_vsdworkshop_11_11_2025_22_05_38" src="https://github.com/user-attachments/assets/53cd7dac-d833-4e3e-9074-3a516e17342d" />


---

## 🧮 **Sky130 Tech File Labs**

---

### ⚙️ **48 – Lab Steps to Create Final SPICE Deck using Sky130 Tech**

* Combine the extracted layout SPICE with **Sky130 model files**.
* Ensure correct parameter mapping for **NMOS** and **PMOS** devices.

---




