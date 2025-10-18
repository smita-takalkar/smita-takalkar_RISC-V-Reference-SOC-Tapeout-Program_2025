# 📊 **Day 4 – Sky130 Noise Margin Lab**

---

### 🔹 **Plotting Noise Margin**

```bash
vim day4_inv_noisemargin_wp1_wn036.spice
ngspice day4_inv_noisemargin_wp1_wn036.spice
plot out vs in
```

* The **Vout vs Vin graph** is used to determine the **noise margins** of the CMOS inverter.
* **Measured points from the curve:**

  * **High logic range:** Vin ≈ 1.6 – 1.7 V → `(V_IL, V_OH) = (0.7, 1.7)`
  * **Low logic range:** Vin ≈ 0 – 0.2 V → `(V_IH, V_OL) = (0.97, 0.11)`

---

### 🔹 **Calculating Noise Margins**

* **High Noise Margin (NMH):**

```
NMH = V_OH - V_IH
```

* **Low Noise Margin (NML):**

```
NML = V_IL - V_OL
```

These values indicate the **tolerance of the CMOS inverter to noise** at the high and low logic levels.

---

<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-27-16" src="https://github.com/user-attachments/assets/5aa97e36-8f5e-459a-b56e-cd39826c5982" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-27-28" src="https://github.com/user-attachments/assets/4380ca06-b40e-4e59-af91-8844f5338602" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-28-29" src="https://github.com/user-attachments/assets/a6cb2f5a-3e24-4516-abd6-a6a27d8e8669" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-33-10" src="https://github.com/user-attachments/assets/f91a671c-1152-4d7b-80a5-af9bdd59910a" />
