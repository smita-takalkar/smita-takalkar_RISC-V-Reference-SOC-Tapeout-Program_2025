# 🧭 Week 5 Task – OpenROAD Flow Setup and Floorplan + Placement  

### 🎯 **Objective**
To set up the **OpenROAD Flow Scripts** environment and execute the **Floorplan** and **Placement** stages of the physical design flow.

This task transitions from **SPICE-level transistor design (Week 4)** to **backend implementation**, where logical design is converted into its physical layout on silicon.

---

## 💡 **Importance**
After analyzing timing from transistor-level circuits, this task demonstrates how those circuits are physically implemented on silicon.  
It introduces the **OpenROAD** toolchain — an open-source, fully automated **RTL-to-GDSII** flow widely used in academic and industrial research.

Floorplanning and placement are key backend stages that define:
- Design constraints before routing  
- Standard cell arrangement to optimize delay, area, and congestion  
- Physical design factors that affect timing and manufacturability  

---

## ⚙️ **Task Procedure**

### 1. **Environment Setup**
- Install required dependencies and tools for OpenROAD Flow Scripts.  
- Clone the reference repository and verify installation using a sample design.  

### 2. **Floorplanning**
- Define core area, aspect ratio, and utilization.  
- Initialize power and ground rings.  
- Generate floorplan reports and visual checks through OpenROAD GUI (optional).  

### 3. **Placement**
- Execute global and detailed placement stages.  
- Generate placement results and verify congestion and timing data.  
- Save reports and logs for documentation and analysis.  

# 🧩 ** OpenROAD Flow Scripts Installation**

## 📘 **Objective**

This task focuses on installing and setting up **OpenROAD Flow Scripts** for end-to-end physical design automation. The goal is to prepare the environment for running the OpenROAD flow on a given design and understand its flow structure.

---

## ⚙️ **Task Components**

### **1️⃣ Install OpenROAD Flow Scripts**



### **🔹 Step 1: Clone the Repository**

```bash
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
cd OpenROAD-flow-scripts
```
![WhatsApp Image 2025-10-25 at 11 25 37 PM](https://github.com/user-attachments/assets/9be1516c-233f-4f5b-846f-b2155d50b243)


---

### **🔹 Step 2: Install Prerequisites**

Before building OpenROAD, ensure the following dependencies are installed:

```bash
sudo apt update
sudo apt install -y build-essential cmake python3 python3-venv \
tcl-dev tk-dev swig bison flex libreadline-dev gawk \
libffi-dev git
```

> 💡 *Refer to the [reference repository prerequisites](https://github.com/spatha0011/spatha_vsd-hdp/blob/main/Day14/README.md) for detailed dependency versions.*

---

### **🔹 Step 3: Initialize Submodules**

```bash
git submodule init
git submodule update
```

---

### **🔹 Step 4: Build OpenROAD**

Use the flow’s built-in script to build the complete toolchain:

```bash
make
```



### **🔹 Step 5: Verify Installation**

To verify successful installation:

```bash
./flow.tcl -help
```




## 📂 **Reference**

🔗 [OpenROAD Reference – spatha_vsd-hdp Day 14](https://github.com/spatha0011/spatha_vsd-hdp/blob/main/Day14/README.md)
🔗 [Official OpenROAD GitHub Repository](https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts)

---


