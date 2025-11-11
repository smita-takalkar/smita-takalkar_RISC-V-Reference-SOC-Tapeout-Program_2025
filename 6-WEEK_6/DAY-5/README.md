## 🧩 **DAY 5 – Final Steps for RTL to GDS using TritonRoute and OpenSTA**

---

# 🧱 **Routing and Design-Rule Check (DRC)**

---

### 🔹 **78 – Maze Routing: Lee’s Algorithm**

* Finds the **shortest routing path** between source and target.
* Expands wavefront grid until target reached.

---

### ⚙️ **79 – Lee’s Algorithm Conclusion**

* Guarantees optimal route but is computationally heavy.
* Forms the foundation of modern routing algorithms (e.g., A* search).

---

### 🧾 **80 – Design Rule Check (DRC)**

* Ensures layout obeys **foundry spacing, width, and enclosure rules**.
* DRC clean layout = ready for fabrication.

---

# 🔋 **Power Distribution Network (PDN) and Routing**

---

### ⚡ **81 – Build Power Distribution Network**

* Create horizontal and vertical **power straps (VDD/VSS)**.
* Ensures uniform current delivery to all cells.

---

### 🔌 **82 – From Power Straps to Standard-Cell Power**

* Connect global straps to **standard-cell rails** using **vias**.
* Verify connectivity using DRC and LVS.

---

### 🧭 **83 – Global & Detailed Routing (TritonRoute Config)**

* **Global Routing:** coarse path planning between blocks.
* **Detailed Routing:** precise wire placement respecting design rules.

```bash
run_routing
```

---

# 🧮 **TritonRoute Features**

---

### ⚙️ **84 – Feature 1: Honors Pre-Processed Route Guides**

* Uses **FastRoute** generated guides to minimize detours.

---

### 🔧 **85 – Feature 2 & 3: Inter-Guide Connectivity & Inter-/Intra-Layer Routing**

* Handles connection across multiple routing layers.
* Ensures signal continuity and minimal via usage.

---

### 🧩 **86 – Routing Topology & Connectivity Handling**

* Chooses optimal **topology** (L-shape, Z-shape, Manhattan).
* Balances wirelength vs. timing vs. crosstalk.

---

### 📁 **87 – Final Files Post-Route**

* **DEF:** Routed design
* **SPEF:** Parasitic info
* **GDSII:** Final layout for fabrication
* **Reports:** DRC / LVS / Timing summaries

---



