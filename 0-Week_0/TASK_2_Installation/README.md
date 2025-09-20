
# Task 2: Tools Installation

This document provides the steps to install and verify essential tools required for VLSI design and simulation.

---

## 📌 System Requirements

* **Operating System**: Ubuntu 20.04 or higher
* **Memory**: 6 GB RAM
* **Storage**: 50 GB HDD
* **CPU**: 4 vCPUs

---

## 🔧 Tool Installation

### 1. Yosys

**Description**: Yosys is an open-source framework for Verilog RTL synthesis.

**Installation Steps**:

```bash
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make   # Install make if not already installed
sudo apt-get install build-essential clang bison flex \
libreadline-dev gawk tcl-dev libffi-dev git \
graphviz xdot pkg-config python3 libboost-system-dev \
libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make
sudo make install
```

**Verification**:

```bash
yosys --version
```
📸 Snapshot:
<img width="866" height="629" alt="YOSYS_Screenshot from 2025-09-20 11-16-43" src="https://github.com/user-attachments/assets/9502190d-39aa-4392-8242-8ca8576b4e6c" />


---

### 2. Icarus Verilog (Iverilog)

**Description**: Icarus Verilog is a Verilog simulation and synthesis tool.

**Installation Steps**:

```bash
sudo apt-get update
sudo apt-get install iverilog
```

**Verification**:

```bash
iverilog -v
```
📸 Snapshot:
<img width="1214" height="768" alt="IVerilog_Screenshot from 2025-09-20 11-36-29" src="https://github.com/user-attachments/assets/10f9c7c8-2528-4d15-8906-819ef40e551d" />




---

### 3. GTKWave

**Description**: GTKWave is a waveform viewer for simulation output.

**Installation Steps**:

```bash
sudo apt-get update
sudo apt install gtkwave
```

**Verification**:

```bash
gtkwave --version
```
📸 Snapshot:<img width="1280" height="800" alt="GTKWave_Screenshot from 2025-09-20 11-38-17" src="https://github.com/user-attachments/assets/dfc0f4e9-684d-4d67-a256-2da09e8e06e0" />



---

### 4. NgSpice

**Description**: NgSpice is an open-source circuit simulator.

**Installation Steps**:

1. Download the latest tarball from: [NgSpice SourceForge](https://sourceforge.net/projects/ngspice/files/)
2. Extract and build:

```bash
tar -zxvf ngspice-37.tar.gz
cd ngspice-37
mkdir release
cd release
../configure --with-x --with-readline=yes --disable-debug
make
sudo make install
```

**Verification**:

```bash
ngspice -v
```
📸 Snapshot:
<img width="1214" height="768" alt="NgSpice_Screenshot from 2025-09-20 12-10-36" src="https://github.com/user-attachments/assets/20658229-466e-4988-bd52-3997ed86ca14" />


---

### 5. Magic VLSI Layout Tool

**Description**: Magic is an open-source VLSI layout tool.

**Installation Steps**:

```bash
sudo apt-get install m4
sudo apt-get install tcsh
sudo apt-get install csh
sudo apt-get install libx11-dev
sudo apt-get install tcl-dev tk-dev
sudo apt-get install libcairo2-dev
sudo apt-get install mesa-common-dev libglu1-mesa-dev
sudo apt-get install libncurses-dev

git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
sudo make install
```

**Verification**:

```bash
magic -v
```
📸 Snapshot:
<img width="1280" height="800" alt="Magic_Screenshot from 2025-09-20 12-20-55" src="https://github.com/user-attachments/assets/37c4c23e-f971-4431-8335-5033e3323407" />


---
## 6. OpenLane Installation         

### Step 1: Update System
```bash
sudo apt-get update
sudo apt-get upgrade
````

---

### Step 2: Install Essential Packages

```bash
sudo apt install -y build-essential python3 python3-venv python3-pip make git
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

---

### Step 3: Install Docker

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o \
/usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

---

### Step 4: Verify Docker Installation

```bash
sudo docker run hello-world
```


---

### Step 5: Manage Docker Permissions

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
```

After reboot:

```bash
docker run hello-world
```

📸 *Snapshot: Docker hello-world *
<img width="866" height="629" alt="DOCKER_Screenshot from 2025-09-20 18-54-50" src="https://github.com/user-attachments/assets/08e4a9c0-d337-4a05-873f-a42bd4fca492" />


---

### Step 6: Verify Dependencies

Run the following commands to confirm installation:

```bash
git --version
docker --version
python3 --version
python3 -m pip --version
make --version
python3 -m venv -h
```

📸 *Snapshots for each version check output*
<img width="1214" height="768" alt="Dependencies_Screenshot from 2025-09-20 18-59-11" src="https://github.com/user-attachments/assets/44234805-5b32-4536-be82-59238c66ff6b" />


---

### Step 7: Install OpenLane, PDKs, and Tools

```bash
cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test
```

📸 *Snapshot: 
<img width="866" height="670" alt="OpenLane_Screenshot from 2025-09-20 20-38-13" src="https://github.com/user-attachments/assets/699fd607-e366-45e2-afce-2143ec928089" />

---





   
