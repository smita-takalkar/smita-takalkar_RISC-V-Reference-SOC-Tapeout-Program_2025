# DAY 1 -Lab 1 SPICE SIMULATION WITH SKY130

### 🔧 **Commands and Explanation**

```bash
cd vsdtapeout/
```

Navigate into the **VSDTapeout** workspace directory.
This is the main working folder where you’ll set up and run all design-related commands.

---

```bash
git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
```

Clone the **Sky130 Circuit Design Workshop** repository from GitHub.
This repository contains design examples, SPICE netlists, and model files needed for transistor-level simulation using the **SkyWater SKY130 PDK**.

> 📁 After cloning, a new folder named `sky130CircuitDesignWorkshop` will be created inside `vsdtapeout`.

---

```bash
cd sky130CircuitDesignWorkshop/design/sky130_fd_pr/cells/nfet_01v8/
```

Navigate to the **NMOS device cell directory** within the cloned repository.
This path contains **device model files** for the **1.8V NMOS transistor (`nfet_01v8`)** — including its SPICE model definitions and corner files used for simulation across different process variations.

> 📂 `sky130_fd_pr` → Standard device library from the SkyWater PDK
>
> 📂 `cells/nfet_01v8` → Directory containing NMOS device SPICE definitions

---
<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-00-18" src="https://github.com/user-attachments/assets/fa98e074-41ba-48ee-82e1-26951d2b14b9" />


```bash
less sky130_fd_pr__nfet_01v8__tt.pm3.spice
```

Open the **TT (Typical-Typical) process model file** for the NMOS device in a scrollable viewer (`less`).
This `.pm3.spice` file defines the **physical and electrical parameters** used by Ngspice for simulations under the **typical process corner**, such as:

* Threshold voltage
* Mobility parameters
* Capacitances
* Channel length modulation, etc.

These parameters are crucial for **accurate device-level simulation** in the 130nm process node.

> The `less` command is used here because model files are long and read-only — it allows easy scrolling and searching without accidentally modifying the file.

---

```bash
less sky130_fd_pr__nfet_01v8__tt.corner.spice
```

View the **corner configuration file** for the same NMOS device.
This file references the `.pm3.spice` model and specifies **corner-based simulation conditions** (TT, SS, FF, etc.), defining how the device behaves under **process variations** like faster or slower transistor characteristics.
<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-06-23" src="https://github.com/user-attachments/assets/fd72e8e1-f613-43be-aad4-31122f76be5a" />

```bash
less all.spice
```
* The file `all.spice` is typically a **consolidated SPICE file** that includes **all device models, corners, and library references** needed for circuit simulations.
* Unlike `sky130.lib.spice`, which mainly references other model files, `all.spice` often **combines multiple `.spice` files** into a single file for convenience. This is useful for:

  * Running **Ngspice simulations** without repeatedly including multiple files
  * Having a **ready-to-use library** with all NMOS, PMOS, and other device parameters
  * Ensuring all **corner models** are available in one file
 <img width="1600" height="900" alt="Screenshot from 2025-10-17 17-31-33" src="https://github.com/user-attachments/assets/48fb93f8-432e-48fb-b4d0-b772f404fd64" />
 


```bash
cd ../../models/
less sky130.lib.spice
```

   * Opens the **master library file** for the PDK in a scrollable viewer.
   * This file organizes references to **process corner model files** (TT, FF, SS, FS, SF) and serves as the main include file for Ngspice simulations.

This tells Ngspice which SPICE files to use for each corner, allowing accurate simulation of NMOS, PMOS, and other devices under **typical and extreme fabrication conditions**.
<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-01-42" src="https://github.com/user-attachments/assets/e4aa2a14-8a5f-46e3-afe3-a9e258ceac1e" />

<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-06-11" src="https://github.com/user-attachments/assets/b094f304-8729-4ebf-8197-3841f7ae6b42" />

<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-08-08" src="https://github.com/user-attachments/assets/8c49e86f-c1ef-410a-8a10-084aa574754d" />
<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-08-35" src="https://github.com/user-attachments/assets/68aadaba-1a60-4f76-aa3a-55c010278313" />

Here’s how you can document and explain this next step in your **README.md**:

---

### ✏️ **Create or Edit a SPICE Netlist**

```bash
cd ../../
vim day1_nfet_idvds_L2_W5.spice
```
   * Opens the **Vim editor** to **create or edit** a SPICE netlist file named `day1_nfet_idvds_L2_W5.spice`.
   * The filename suggests the simulation goal:

     * `nfet` → NMOS transistor
     * `idvds` → I–V curve (Drain current vs. Drain voltage)
     * `L2_W5` → Transistor dimensions (Length = 2 units, Width = 5 units)
> After saving this file, you can run the simulation in Ngspice with:

```bash
ngspice day1_nfet_idvds_L2_W5.spice
```
This will generate the **I–V curve** for the NMOS transistor with the given dimensions.

<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-10-23" src="https://github.com/user-attachments/assets/5393c823-4b0f-42fb-8d4b-611be48bd613" />
<img width="1534" height="868" alt="Screenshot from 2025-10-17 17-21-46" src="https://github.com/user-attachments/assets/12dcad79-4966-4b4a-95b1-005d1ba616e5" />
<img width="1600" height="900" alt="Screenshot from 2025-10-17 17-22-51" src="https://github.com/user-attachments/assets/8c5b4a9c-4d33-45db-9315-fc9f31c6bb10" />


