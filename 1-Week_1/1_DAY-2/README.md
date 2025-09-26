# Day 2: Timing Libraries, Hierarchical vs Flat Synthesis, and Efficient Flop Coding Styles

## 1. Introduction to Timing Libraries (`.lib`)
 

### What is a `.lib`?
A `.lib` file (timing library) is a **collection of standard cells** characterized for different process, voltage, and temperature (PVT) conditions.  

**Example library name:**  
```

sky130_fd_sc_hd_tt_025c_1v80

```

- **Technology node**: 130 nm  
- **Process corner**: `tt` → typical (can also be `ss` for slow, `ff` for fast)  
- **Temperature**: `025c` → 25°C  
- **Voltage**: `1v80` → 1.8V  

Thus, `tt_025c_1v80` represents the **operating conditions**.

---

### PVT: Key Design Parameters
- **Process (P)** → Variations due to fabrication  
- **Voltage (V)** → Variations in supply voltage  
- **Temperature (T)** → Variations in operating temperature  

A design must function correctly across these variations.

---

### Additional Information
- **Technology**: CMOS  
- **Delay model**: Lookup table (LUT)  
- **Units**:  
  - Time → 1 ns  
  - Voltage → 1 V  
  - Power → 1 nW  
  - Current → 1 mA  
  - Resistance → 1 kΩ  
  - Capacitance → 1 pF  

Libraries are pre-characterized to capture these variations.

To inspect the behavior of a specific cell:  
```

../my_lib/verilog_model/sky130_fd_sc_hd_a2111o.behavioral.v

```

---

## 2. Hierarchical vs Flat Synthesis


### Flat Synthesis
- Entire design is flattened into a **single module**.  
- Provides **better optimization** opportunities for synthesis tools.  
- Debugging is **harder** due to loss of module boundaries.
Flat module representation:
<img width="1534" height="868" alt="Day2_16_flatten_module" src="https://github.com/user-attachments/assets/f09d319f-5ee8-4a61-bd17-0781e4919afb" />


### Hierarchical Synthesis
- Design is preserved in **submodules**.  
- Useful when:
  - Multiple instances of the same module exist.  
  - Design size is very large.  
- Enables **submodule-level synthesis**, followed by combining results into a top-level netlist.  
- **Debugging and reuse** are much easier compared to flat synthesis.
Hierarchical representation:  <br/>
<img width="1600" height="900" alt="Day2_15_hierarchical_module" src="https://github.com/user-attachments/assets/533f6c2c-a19b-4899-953a-49f44386251d" />

Submodule level representation:
<img width="1534" height="868" alt="Submodule_level synth" src="https://github.com/user-attachments/assets/2a6d1c75-99b8-4f98-bcd8-cfe4adfd15c9" />

---

## 3. Flop Coding Styles and Optimization

### Why Flip-Flops?
- **Glitch**: A small pulse of incorrect logic output due to differences in data arrival times.  
- **Solution**: Flip-flops capture inputs at clock edges and **filter glitches**, ensuring stable outputs.  

These stable outputs are then passed on to subsequent stages in the digital circuit.

---

### Flip-Flop Features
- **SET/RESET pins** control the output.  
- Can be:
  - **Synchronous** → Controlled by clock edge.  
  - **Asynchronous** → Controlled immediately, independent of clock.  

---

### Common Flop Coding Styles
- D Flip-Flop with **asynchronous reset**
  <img width="1600" height="900" alt="dff_asyncres_synth" src="https://github.com/user-attachments/assets/15e6c364-dd34-4960-939e-91b749933866" />
 # Waveform:
 <img width="1534" height="868" alt="asynres_gtkwave" src="https://github.com/user-attachments/assets/4a48234b-4c90-4aab-a293-50921ade9959" />

  
- D Flip-Flop with **asynchronous set**
  <img width="1600" height="900" alt="dff_async_set_synth" src="https://github.com/user-attachments/assets/9fe3a1dd-62ff-4a7c-aa53-8f8410e9d965" />
 # Waveform:
 <img width="1600" height="900" alt="async_set_gtkwave1" src="https://github.com/user-attachments/assets/dd50e8b6-b73b-4672-96b9-729cd8b4d207" />


- D Flip-Flop with **synchronous reset**
  <img width="1600" height="900" alt="dff_syncres_synth" src="https://github.com/user-attachments/assets/47c8d2d9-d88f-4c8b-8c12-2bc343ccbdf8" />
 
 # Waveform:
 <img width="1534" height="868" alt="sync_set_gtkwave" src="https://github.com/user-attachments/assets/479f7a5c-09c6-4caf-ba14-4fada790b2bd" />

- Other variations depending on design requirements


---

## Summary
On **Day 2**, we explored:
1. **Timing Libraries** (`.lib`) → Structure, PVT variations, and units.  
2. **Hierarchical vs Flat Synthesis** → Trade-offs between optimization and modularity.  
3. **Flop Coding Styles** → Handling glitches and coding different reset/set configurations.  


