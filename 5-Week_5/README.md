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

---

