


#  VSDBabySoC – Functional Modelling, Synthesis & Simulation  

This document explains how to clone, simulate, synthesize, and analyze the **VSDBabySoC** project using **open-source tools** such as Icarus Verilog, GTKWave, SandPiper-SaaS, and Yosys.  

---

## 📥 Step 1 – Clone the Repository  
Clone the BabySoC GitHub repo:  
```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC/
````

---

## 🔄 Step 2 – TLV to Verilog Conversion

The RVMYTH core is written in **TL-Verilog (TLV)**, so we must first convert it to **SystemVerilog/Verilog** using **SandPiper-SaaS**.

### Install Required Tools

```bash
sudo apt update
sudo apt install python3-venv python3-pip -y
```

### Create Python Virtual Environment

```bash
python3 -m venv sp_env
source sp_env/bin/activate
```

### Install SandPiper-SaaS

```bash
pip install pyyaml click sandpiper-saas
```

### Convert TLV → Verilog

```bash
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```

* `-i ./src/module/*.tlv` → Input TLV files
* `-o rvmyth.v` → Output Verilog file name
* `--bestsv` → Optimize for SystemVerilog
* `--noline` → Remove line markers
* `-p verilog` → Set output format as Verilog
* `--outdir ./src/module/` → Output directory

---

## 🧪 Step 3 – Pre-Synthesis Simulation

Run the testbench before synthesis to check correctness.

```bash
cd VSDBabySoC
make pre_synth_sim
```

* The result `pre_synth_sim.vcd` will be generated in:

  ```
  output/pre_synth_sim/
  ```

### View Waveforms

```bash
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```
<img width="1600" height="900" alt="pre_synth_sim" src="https://github.com/user-attachments/assets/02a72c4b-ae1f-4147-b8f6-2ca916cf98e8" />

**Signals Observed:**

* **CLK** → Input clock to RVMYTH core (from PLL).
* **reset** → Reset signal from external source.
* **OUT** → Output of VSDBabySoC module (digital representation of DAC).
* **RV_TO_DAC[9:0]** → 10-bit output of RVMYTH core (register #17).
* **OUT (real)** → DAC output as real (simulated analog).

---

## ⚙️ Step 4 – Synthesizing using Yosys

**Yosys** is used for RTL synthesis, **ABC** for technology mapping, and **OpenSTA** for timing analysis.

### Yosys Commands

```tcl
yosys
yosys> read_liberty -lib ./src/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
yosys> read_liberty -lib ./src/lib/avsddac.lib
yosys> read_liberty -lib ./src/lib/avsdpll.lib
yosys> synth -top vsdbabysoc
yosys> write_verilog vsdbabysoc.synth.v
yosys> abc -liberty ./src/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
yosys> show vsdbabysoc
```
<img width="1600" height="900" alt="vsdbabysoc_yosys_synth" src="https://github.com/user-attachments/assets/4fe22d74-d681-4e34-aba3-707c1fc3d941" />


---

## 🔁 Step 5 – Post-Synthesis Simulation (GLS)

Run gate-level simulation (GLS) using the synthesized netlist.

```bash
cd ~/VSDBabySoC
make post_synth_sim
```

* The result `post_synth_sim.vcd` will be stored in:

  ```
  output/post_synth_sim/
  ```

### View Waveforms

```bash
gtkwave output/post_synth_sim/post_synth_sim.vcd
```
<img width="1600" height="900" alt="post_synth_sim" src="https://github.com/user-attachments/assets/5ba0437b-4da9-4292-a635-5b138094cfeb" />


**Signals Observed:**

* **\core.CLK** → Input clock signal of RVMYTH (from PLL).
* **reset** → External reset input.
* **OUT** → Output of VSDBabySoC (digital DAC representation).
* **\core.OUT[9:0]** → 10-bit output of RVMYTH core (register #17).
* **OUT (real)** → DAC analog output (simulated as real datatype).

---

🚀 This completes the **BabySoC functional modelling → synthesis → GLS flow**.

```

