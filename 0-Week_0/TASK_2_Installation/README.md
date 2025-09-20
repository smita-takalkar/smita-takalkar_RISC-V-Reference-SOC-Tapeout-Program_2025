
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

---

## ✅ Summary

After following the above steps, you should have the following tools successfully installed and verified on your system:

* [x] Yosys
* [x] Icarus Verilog
* [x] GTKWave
* [x] NgSpice
* [x] Magic

---


   
