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
<img width="1534" height="868" alt="Screenshot from 2025-10-25 18-09-26" src="https://github.com/user-attachments/assets/02af9591-9879-49f2-9543-aee789cf4b8a" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 18-11-02" src="https://github.com/user-attachments/assets/82c685b2-bcde-4c26-9347-f2cb93ff997c" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 18-11-29" src="https://github.com/user-attachments/assets/081194a6-cd3b-43f1-9dd6-33957125a826" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 18-19-44" src="https://github.com/user-attachments/assets/32da1b53-831c-442c-ab74-4a5672d0d53d" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 18-27-31" src="https://github.com/user-attachments/assets/06230d29-e4e6-4e18-bced-0654feaf8dc6" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-20-03" src="https://github.com/user-attachments/assets/ab9a4c68-a281-4d3f-9a8b-f2a1d4b893e5" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-28-21" src="https://github.com/user-attachments/assets/17477cad-34f1-41ce-9f4d-1a878695256c" />

Compiler ERROR:
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-33-10" src="https://github.com/user-attachments/assets/1c8f2e22-212e-452c-979f-f48acc727227" />
Solution:
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-53-14" src="https://github.com/user-attachments/assets/c9512bcd-8165-4425-a961-4cbe70ec1224" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-54-39" src="https://github.com/user-attachments/assets/129ef076-2c19-4157-9b50-3c937ce3cf6c" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 20-59-36" src="https://github.com/user-attachments/assets/50a31e8e-ba9d-4b5c-9c9f-7e7e8a600a65" />
<img width="1534" height="868" alt="Screenshot from 2025-10-25 21-08-20" src="https://github.com/user-attachments/assets/04bf99c6-45e9-415b-b56f-e8c9053000e7" />
<img width="1600" height="868" alt="Screenshot from 2025-10-25 21-42-33" src="https://github.com/user-attachments/assets/c1b954e0-3baf-4059-82d8-6102f8deb81d" />


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


