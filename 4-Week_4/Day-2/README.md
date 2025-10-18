# DAY 2 
## PLOTTING Id vs Vds

```bash
vim day2_nfet_idvds_L015_W039.spice
```

**Explanation:**

This command opens the **Vim text editor** to create or modify a SPICE netlist file named
`day2_nfet_idvds_L015_W039.spice`.

The file name encodes important device parameters:

* **`day2`** → Indicates this is part of the *second-day exercise* or simulation.
* **`nfet`** → Refers to the NMOS transistor type.
* **`idvds`** → Represents the **I–V characteristic simulation** (Drain current vs Drain voltage).
* **`L015_W039`** → Specifies **channel length (L = 0.15 µm)** and **width (W = 0.39 µm)**.
  These are **short-channel dimensions**, used to study advanced behavior such as velocity saturation or channel length modulation.

---

### 🧠 **Purpose of this Step**

This netlist is used to simulate **drain characteristics** of a smaller geometry NMOS transistor under the **Sky130 1.8V process**.

---
<img width="1534" height="868" alt="Screenshot from 2025-10-17 22-43-12" src="https://github.com/user-attachments/assets/5885b82e-4186-434f-aaba-9eb5d0cdf771" />

Here’s how you can document and explain this final command step in your **README.md** 👇

---

### ⚡ **Run NMOS Simulation in Ngspice**

```bash
ngspice day2_nfet_idvds_L015_W039.spice
```

**Explanation:**
This command runs the **Ngspice simulator** on the SPICE netlist file you created —
`day2_nfet_idvds_L015_W039.spice`.

When executed, Ngspice will:

1. **Parse the netlist** to identify all circuit elements (transistor, voltage sources, models, etc.).
2. **Load the Sky130 PDK model** files specified using `.include` (for example, `all.spice`).
3. **Perform the analysis** defined in the file — in this case, a **DC sweep** of the drain voltage (`Vds`) while keeping the gate voltage (`Vgs`) constant.
4. **Output simulation data** such as drain current (`Id`) vs. drain voltage (`Vds`).

---
<img width="1534" height="868" alt="Screenshot from 2025-10-17 22-53-12" src="https://github.com/user-attachments/assets/a0ff0d74-ed58-4fe8-82dc-e40758c9bf77" />

In Ngspice,
```
plot -vdd#branch
```

plots the **current flowing through the voltage source named `Vdd`**.

* The **negative sign (-)** is used because Ngspice defines current **entering the positive terminal** of the voltage source as positive.
* To get the **drain current (Id)** (flowing *out* of the transistor into Vdd), you invert the sign — hence `-vdd#branch`.

So, this plot represents **Id vs. Vds (drain current vs. drain voltage)** for the NMOS transistor.
The lower values showing quadratic behavior nad higher values showing liner behavior

---
<img width="1600" height="900" alt="Screenshot from 2025-10-17 22-54-08" src="https://github.com/user-attachments/assets/991e773f-7922-4caa-a503-2de155f88164" />
<img width="1600" height="900" alt="Screenshot from 2025-10-17 22-54-44" src="https://github.com/user-attachments/assets/c3924364-452f-4217-b5dc-0ba58177eff7" />

## PLOTTING Id vs Vgs 

<img width="1600" height="900" alt="Screenshot from 2025-10-17 22-55-39" src="https://github.com/user-attachments/assets/89d93981-ff59-4ece-9e3d-7ee6e9ef2077" />
<img width="1600" height="900" alt="Screenshot from 2025-10-17 22-56-48" src="https://github.com/user-attachments/assets/42db245b-0e1a-4f84-ae4a-1626bd18fbc8" />
<img width="1600" height="900" alt="Screenshot from 2025-10-17 22-57-52" src="https://github.com/user-attachments/assets/1543a726-a5e0-418b-b958-3c0727cbd1b8" />
📊 Observation

Since the channel length is 0.15 µm (short-channel device), the Id vs Vgs graph exhibits a linear behavior instead of the ideal quadratic relation seen in long-channel MOSFETs.
