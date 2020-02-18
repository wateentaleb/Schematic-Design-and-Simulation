# Schematic Design and Simulation

## Overview

In this project the objective is to design and simulate schematic view of three basic digital gates: INV, NAND2 and NOR2. This part of the design flow includes the following steps:
+ Create circuit schematics
+ Create the symbol view
+ Create simulation test-benches for typical model parameters

Using the theoretical width-ratio between PMOS and NMOS transistors (approximately two) as a starting point, resize and re-simulate the transistor sizes so that: 

+ Approximately equal rise and fall times of the signal pulses at the outputs are achieved, i.e. the cross-over point at around VDD/2.
+ Gate propagation delay and power dissipation of the gates can be measured.
+ The gate performance can be measured as a function of varying the load capacitance.

The Cadence technology will be used for the entirity of this project. 

## Gates

### `Inverter Design`

An inverter is also known as a **not** gate, will flip the value of any value inputted, 
If x is 0 the output will be 1 and vise versa. Nonetheless, the gate was also used as a buffer for other components such as NAND and NOR. 
![not-gate](https://user-images.githubusercontent.com/16707828/74692910-698dff00-51b7-11ea-9db3-26b9601d9550.png)

For the transistor parameters, enter the information shown in the table below. It is assumed that for digital logic gates design the minimum allowed gate length is used for all transistors. That leaves manipulation of the gate width as the only design parameter. While working on design in progress it is useful to use variables instead of fixed numbers. This approach allows designer to easily optimize the design by varying the gate widths using a parametric analysis tool.

We must add pins to the design to allow signals to enter into the cell view from other circuits.Four pins are required for this design: 
+VDD 
+VSS
+In
+Out

**`The Inverter Schematic`**

<img width="636" alt="inverter-schematic" src="https://user-images.githubusercontent.com/16707828/74692758-a86f8500-51b6-11ea-82cd-267bddd78f22.png">

**`Recommended Paramaters for the nmos and pmos Transistors`**

<img width="238" alt="recommended paramaters for the transistors" src="https://user-images.githubusercontent.com/16707828/74692796-db197d80-51b6-11ea-8946-7e5b2a74c682.png">


**`Symbol View of the Inverter`**

![symbol-inverter](https://user-images.githubusercontent.com/16707828/74692892-511de480-51b7-11ea-9b07-bd93336da010.png)

**`Test Bench for the Inverter`**
![Testbench-inverter](https://user-images.githubusercontent.com/16707828/74692986-b671d580-51b7-11ea-9bab-787fbd3809fc.png)
