# Part 2 – Fundamentals of STA (Static Timing Analysis)

## Notes STA Fundamentals – Udemy

- Timing path has start point (flop clk pin/ input ports) and end point (flop d pin/output ports)
  Identify the end points first 

- **Arrival Time** : Time required by the signal to arrive/reach at the end point
- **Required time** : defines design requirements
- **Slack** : Difference between arrival and expected time

- Max difference/max slack is also known as setup slack, setup timing, setup analysis
- Min difference/min. Slack is also known as hold slack, hold timing, hold analysis
  
## Types of setup/hold analysis
**1. Reg2reg: **

- Setup analysis (single clock)
Cell delays, wire delays, signal arrival time at inputs

To build timing report: 

1. Ckt. Is converted into Directed acyclic graph(DAG)( timing graph in sta world)
2. Input pins, latches all are converted into nodes
3. **Actual arrival time (AAT):** time at any node where we see latest transition after first rise clk edge
   Calculated from launch flop to the capture flop
   
       **Arrival time at any node(with one input)= sum of delays**

For nodes having multiple nodes calculate AAT for each branch then depending on analysis choose the correct one 

** Required arrival time (RAT):** time at any node where we expect latest transition within clock cycle 
      -Constraints are taken into consideration 
      -Calculated from capture flop to launch flop (opp to aat)

    **RAT= substraction of delays **

    **Slack = RAT-AAT**
  AAT is expected to be less than RAT at every node for meeting design expectations 

**GBA(graph based analysis)**- worst case path , results into negative slack 

**PBA (path based analysis)** - real path which is traced on silicon, results in positive slack , needs more time for calculations 

**Pin node analysis: ** AAT, RAT, slack calculation is same 

2. In2Reg
3. Reg2Out
4. In2Out
5. Clock gating
6. Recovery/removal 
7. Data to data
8. Latch (time borrow/time given)
   
## Slew/transitions analysis - these checks ensures that the slew /transition is in between min and max value at every point

Divided into two parts:

1. Data(max/min)
2. Clock(max/min)

   
## Load analysis:
1. Fanout (max/min)
2. Capacitance (max/min)


## Clock analysis:
**1. Skew :** Latency difference (L1, L2,..) 

L1 , L2 : latencies from clk to flop ports 

Affects setup/hold analysis 

**2. Pulse width**




### Transistor level ckt timing analysis:      Combinational delay(theta)+Buffer delay(delta 1) <Clock period (T) + Capture clk delay (delta 2)

    **|Delta1- Delta2| = skew**

* Mux level implementation of capture flop
  
**+ve latch :**  operates on the positive edge of clk
**-ve latch:**  operates on the negative level of clk 
Combination of both forms the flip flop
