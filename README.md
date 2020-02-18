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

**`wpfet Sweep`**

![sweep](https://user-images.githubusercontent.com/16707828/74693034-005abb80-51b8-11ea-8756-d85e28ec282e.png)

**`Propogation Delay Time`**
In ideal case, if there was no propagation delay, effect of the input signal would have been instantaneously seen at the output of an inverter. In other words, a rising edge at the input of an inverter would cause falling edge at the output without any delay. In reality, there is a finite time needed to charge up all capacitances inside the inverter, and to change all electromagnetic fields of all conductors carrying fast switching current. Therefore, the propagation delay time of an inverter is the time difference between the moment when the input edge shows up, and the time when the corresponding output edge shows up as shown in the figure below. 

<img width="522" alt="graph" src="https://user-images.githubusercontent.com/16707828/74693410-c4c0f100-51b9-11ea-865d-c61aac20c0b4.png">

This delay usually vary depending on whether the output is changing high-to-low or vice versa. The propagation delay should be measured at the cross-over point, i.e. at half of the supply voltage (in this case at 0.6V). The propagation delay is then calculated as average value of these two cases: tpd=(tpdr+tpdf)/2. Where tpdr is propagation delay of low-to-high transition, and tpdf is propagation delay of high-to-low transition.

<img width="259" alt="tpd" src="https://user-images.githubusercontent.com/16707828/74693429-dc987500-51b9-11ea-9afc-c4b22e27a3b1.png">


### `NAND Design`

A NAND is one of the most fundamental logic gates in the computer industry, with the ability to perform complex logical expression while minimizing the cost of production for that piece. It is often use as a universal logical gate to build complex and simple circuits.

![Picture1](https://user-images.githubusercontent.com/16707828/74693258-ff765980-51b8-11ea-9281-6db94cd0ef73.png)

**`NAND Schematic`**

<img width="517" alt="schematic" src="https://user-images.githubusercontent.com/16707828/74693288-26349000-51b9-11ea-9251-6fdd0739357d.png">

**`NAND Symbol`**

![symbol](https://user-images.githubusercontent.com/16707828/74693562-49137400-51ba-11ea-8ad5-6e398f1cd747.png)

**`NAND TestBench`**
![nandtestbench](https://user-images.githubusercontent.com/16707828/74693563-4a44a100-51ba-11ea-9b4f-cc8861613100.png)

**`wpfet Sweep`**

<img width="505" alt="wpfetsweep" src="https://user-images.githubusercontent.com/16707828/74693566-4c0e6480-51ba-11ea-91b3-39060a43c101.png">

### `NOR Design`
A Nor gate which is also known as an inverted OR gate only outputs true when both inputs are zero.  
![Picture1](https://user-images.githubusercontent.com/16707828/74693672-c939d980-51ba-11ea-8337-0f28e9a0f0e4.png)


**`NOR Schematic`**

![Picture2](https://user-images.githubusercontent.com/16707828/74693694-e8d10200-51ba-11ea-8e2e-572572d0333f.png)


**`NOR Symbol`**

![schematic](https://user-images.githubusercontent.com/16707828/74693699-ef5f7980-51ba-11ea-95d0-368c5ef9a4ea.png)


**`NOR TestBench`**

![test](https://user-images.githubusercontent.com/16707828/74693709-f8504b00-51ba-11ea-91fa-c10509e7cea4.png)

**`wpfet Sweep`**

![wpfetsweep](https://user-images.githubusercontent.com/16707828/74693717-fdad9580-51ba-11ea-8313-36163a798710.png)

## Schematic Designs to Layouts

Analog and custom IC design is completed in Virtuoso Layout XL Layout tool. During this stage, schematic designs will be transferred into layouts using specific design rules and layers. The layout design stage is extremely important as it reflects what will be manufactured by the fab. 

To check the layout for manufacturability, the DRC tool is used. DRC stands for Design Rule Check. The rules that the DRC tool uses are specific to a particular technology process, in our case we are using a 90nm process, therefore the DRC rules are specific to that process. The setup required for the particular technology is chosen at the moment when Cadence is started with the source ”Start Cadence AMS.csh” switch specified.

To ensure your layout is electrically correct LVS (Layout vs Schematic) tools are used. More info on these tools later in this document.

The steps required to complete a effective layout of the schematic design are listed below: 
An outline of this document is provided below:

+ Creation of the gate layout.
+ Verification of the gate layout with Design Rule Checker (DRC) for manufac-
turability.
+  Verification of electrical equivalence between the layout and schematic views of the gate.
+ Creation of extracted view of the gate layout using layout extractor tool to include all parasitic capacitances.
+ Creation of Configuration View (analog extracted)needed for the layout simu- lation
+ Simulation of the extracted layout view.

## Design Rules
This laboratory had to meet various industry standards; moreover, it taught many pertinent skills that are beneficial for computer hardware engineers, such as minimizing the amount of materials used and matching the schematic design. The tools used to ensure that the designs follow industry standards are explained below.

**`Design Rule Check`**
The next step after designing the layout is to perform the Design Rule Check (DRC). Although it is expected that the students are designing the gates while keeping in mind the design rules, the DRC is the last step in order to verify that the layout does in fact follow design rules. It is important to note that without this tool, any violation of these design rules would certainly resulted into a fabricated chip that does not work as desired. However, this test does not check if the layout represents accurately the schematic, this is where the Layout Versus Schematic Check (LVS) comes in.

**`Design Rule Check`**
The Layout Versus Schematic software recognizes the layout of the components of the circuit as well as the connections between them. The LVS software uses three steps:

1. Extraction: It extracts all the layers drawn, checks the wiring between locations of pins.
2. Reduction: In this part of the software, LVS combines the extracted components into series
and parallel combinations if possible.
3. Comparison: The extracted layout compares the netlist taken from the schematic and the netlist taken from the layout, if the netlists match, then the circuits passes the LVS check.


## Screenshots

**`Inverter`**

<img width="475" alt="inveter" src="https://user-images.githubusercontent.com/16707828/74694103-bf18da80-51bc-11ea-8bd2-c58b7293d7c0.png">


**`2-Input NAND`**

<img width="465" alt="NAND" src="https://user-images.githubusercontent.com/16707828/74694104-bfb17100-51bc-11ea-9cc0-29a976f3848d.png">


**`2-Input NOR`**
<img width="407" alt="NOR" src="https://user-images.githubusercontent.com/16707828/74694106-c04a0780-51bc-11ea-87ae-a11a861980c5.png">


