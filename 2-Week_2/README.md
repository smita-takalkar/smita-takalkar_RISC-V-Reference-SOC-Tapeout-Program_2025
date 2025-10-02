# Week 2 – BabySoC Fundamentals & Functional Modelling

## My Notes

### 🔹 What is SoC?

* A **System-on-Chip (SoC)** = complete computing system packed inside a single chip.
* Combines **CPU + Memory + Peripherals + Interconnect**.
* Advantage → smaller, faster, consumes less power compared to separate components.
* Examples → processors inside smartphones, IoT devices, embedded boards.

---

### 🔹 Components of a Typical SoC

1. **CPU (Core)** → executes instructions, brain of the chip.
2. **Memory** → program + data storage (SRAM/DRAM/Flash).
3. **Peripherals** → UART, GPIO, timers etc. for external communication.
4. **Interconnect/Bus** → backbone for CPU ↔ Memory ↔ Peripherals communication.

---

### 🔹 Why BabySoC?

* It’s a **learning-friendly version** of SoC.
* Has **minimal blocks** (small CPU, simple memory, basic I/O).
* Helps me:

  * Understand **block-level interactions** clearly.
  * Trace **data flow** without too much complexity.
  * Build a strong **foundation before diving into real SoCs**.

So, BabySoC is like the **training wheels** for SoC design 🚲.

---

### 🔹 Functional Modelling – Role in Design Flow

* Comes **before RTL and Physical Design**.
* Purpose:

  * Check **basic functionality** of the SoC.
  * Validate that CPU, memory, and peripherals interact as expected.
  * Find design-level mistakes early (cheaper to fix now than later).
* Tools:

  * **Icarus Verilog (iverilog)** → simulate the Verilog code.
  * **GTKWave** → visualize waveforms, debug signal transitions.

Basically → **functional model = reference blueprint** before jumping into actual RTL implementation.

---

### 🔹 SoC Design Flow (big picture)

1. **Functional Modelling** → BabySoC stage, check high-level behavior.
2. **RTL Design** → describe actual logic in Verilog/VHDL.
3. **Synthesis** → convert RTL to gate-level netlist.
4. **Physical Design** → layout, placement, routing → chip ready for fabrication.

BabySoC = Step 1 → gives me clarity & confidence before deeper RTL work.

---

## Quick Block View (BabySoC Idea)

```
   +---------+       +---------+       +------------+
   |  CPU    | <---> | Memory  | <---> | Peripherals|
   +---------+       +---------+       +------------+
          \__________________  __________________/
                           |  Interconnect/Bus  |
                           +--------------------+
```

---

## ✅ Key Takeaways

* SoC = CPU + Memory + Peripherals + Interconnect → all in 1 chip.
* BabySoC is a **minimal learning SoC**, easy to simulate & debug.
* Functional modelling = **first step** in SoC design flow.
* Tools: **iverilog + GTKWave** = simulate + view waveforms.
* BabySoC learning prepares me for **real SoC RTL + VLSI flow**.

---
