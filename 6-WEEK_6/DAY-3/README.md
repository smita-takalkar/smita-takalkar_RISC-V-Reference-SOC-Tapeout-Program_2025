# ⚙️ **DAY 3 – Design Library Cell using Magic Layout and ngspice Characterization**

---

## 🧪 **Labs for CMOS Inverter ngspice Simulations**

---

### 🔹 **33 – IO Placer Revision**

* Review placement of **I/O pins** in relation to core and die.
* Ensure signal integrity and minimum routing congestion.

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
* Generate **Layout Exchange Format (LEF)** files for cell integration.

---

### 🧰 **47 – Lab Steps to Create Standard Cell Layout & Extract SPICE Netlist**

1. Create the inverter layout in Magic.
2. Label **input, output, and power pins**.
3. Extract the **SPICE netlist** for simulation.

   ```bash
   extract all
   ext2spice cthresh 0 rthresh 0
   ext2spice
   ```

---

## 🧮 **Sky130 Tech File Labs**

---

### ⚙️ **48 – Lab Steps to Create Final SPICE Deck using Sky130 Tech**

* Combine the extracted layout SPICE with **Sky130 model files**.
* Ensure correct parameter mapping for **NMOS** and **PMOS** devices.

---




