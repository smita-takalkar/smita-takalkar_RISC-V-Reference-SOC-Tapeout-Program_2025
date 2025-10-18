## ⚙️ **Day 3 – SPICE Simulation for CMOS**

---

### 📉 **Plotting VTC Characteristics**

```bash
vim day3_inv_vtc_Wp084_Wn036.spice
ngspice day3_inv_vtc_Wp084_Wn036.spice
plot out vs in
```
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-11-03" src="https://github.com/user-attachments/assets/0e9d4299-6d51-4c60-9f3e-e898e8b15c64" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-13-03" src="https://github.com/user-attachments/assets/17ac210b-1575-451b-a8d8-4f00bff2c25b" />
In the **VTC (Voltage Transfer Characteristic)** graph, the **switching threshold voltage** is the point where
`Vin = Vout`, which occurs approximately at **(0.876 V, 0.876 V)**.
Graph:

### ⏱️ **Plotting Transient Analysis**

```bash
vim day3_inv_tran_Wp084_Wn036.spice
ngspice day3_inv_tran_Wp084_Wn036.spice
plot out vs time in
```

<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-16-02" src="https://github.com/user-attachments/assets/360e1404-5bf6-4c5b-9879-0be46c3e2f7a" />
<img width="1534" height="868" alt="Screenshot from 2025-10-18 00-17-29" src="https://github.com/user-attachments/assets/d1fb8ce9-50a2-4c49-a11c-12a347f3eff8" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-18-55" src="https://github.com/user-attachments/assets/0987c37d-46f2-45cc-a017-e3e5965af353" />
<img width="1600" height="900" alt="Screenshot from 2025-10-18 00-20-07" src="https://github.com/user-attachments/assets/3a05092c-896e-4cf4-9845-7bb94b78cbe6" />

From the **transient waveform**, we can determine the **rise delay** and **fall delay** of the CMOS inverter.

---
