## ⚡ **Day 5 

### Lab 1– Sky130 Supply Variation Lab**

---

### 🔹 **SPICE Simulation for Supply Variation**

```bash
vim day5_inv_supplyvar_Wp1_Wn036.spice
ngspice day5_inv_supplyvar_Wp1_Wn036.spice
plot out vs in
```

* The **VTC (Voltage Transfer Characteristic) curves** are plotted for **different supply voltages** (`VDD`).
* Each curve is represented with a **different color** for clarity.

---

### 🔹 **Calculating Gain**

The **gain** of the CMOS inverter under supply variation is determined as:

```
Gain = ΔVout / ΔVin
```

Where:

* `ΔVout` → Change in output voltage
* `ΔVin` → Change in input voltage

This helps analyze how the inverter **response changes with varying supply voltage**, which is critical for **robust design** in digital circuits.

---
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-36-49" src="https://github.com/user-attachments/assets/873ccc12-5d71-4a55-8889-0de2d6b6c507" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-36-57" src="https://github.com/user-attachments/assets/a0ceee0b-872c-4ebf-b486-94ab59d7b60e" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-38-52" src="https://github.com/user-attachments/assets/85a6b39e-d2cf-4146-9fa8-368b8ffcf75d" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-42-04" src="https://github.com/user-attachments/assets/2ca50bbf-987e-4365-a7ce-311dd26a7a41" />


## 🏗️ **Lab 2 – Sky130 Device Variation Labs**

---

### 🔹 **Observing VTC Curve for Device Variation**

```bash
vim day5_inv_devicevariation_wp7_wn042.spice
ngspice day5_inv_devicevariation_wp7_wn042.spice
plot out vs in
```

* In this lab, the **PFET size** is significantly larger compared to the **NFET**.
* The **VTC (Voltage Transfer Characteristic) curve** is analyzed to observe the effect of device sizing on inverter behavior.

---

### 🔹 **Observations from the Graph**

* **Output holds high longer** due to the larger PFET compared to the NFET.
* **Switching threshold shifts to the right**, indicating the PFET is stronger and NFET is weaker.
* The **threshold voltage difference** is approximately `0.988 – 0.9 ≈ 0.088 V`, showing robust CMOS operation.

---

### 🔹 **Conclusion**

* A **larger PFET** increases the strength of the pull-up network.
* The CMOS inverter remains **robust**, with clear logic levels and strong noise margins.
* Proper device sizing ensures **balanced performance and reliable switching**.

---
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-47-25" src="https://github.com/user-attachments/assets/5123fae3-cfb7-445e-b6d3-89df8465f3bc" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-47-58" src="https://github.com/user-attachments/assets/3d6cc0ab-bd12-4797-bfde-f1325de49e13" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-53-24" src="https://github.com/user-attachments/assets/6f5a04ba-e8ea-423f-b18f-4413fed62219" />
