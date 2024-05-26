# *NASSCOM-VSD SOC DESIGN AND PLANNING*
# Contents 
 <div class="unit1">
  <ul>
    <li><a href="#header-1">Day 1 - Inception of open-source EDA, OpenLANE and sky130 PDK</a></li>
	<ul>
        <li><a href="#header-1_1"> How to talk to computers</a></li>
		<ul>
			<li><a href="#header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_2">Introduction to RISC-V</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_3">From Software Applications to Hardware</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-1_2">Soc design and OpenLANE</a></li>
	      <ul>
			<li><a href="#header-1_2_1">Introduction to all components of open-source digital asic design</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_2"> Simplified RTL2GDS flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_3">Introduction to OpenLANE and Strive chipsets</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-1_3">(LAB WORK)Get familiar to open-source EDA tools</a></li>
		<ul>
			<li><a href="#header-1_3_1">OpenLANE Directory structure in detail</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_2">Design Preparation Step</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_3">Review files after design prep and run synthesis</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_5">Steps to characterize synthesis results</a></li>
		</ul>
      </ul>
   </div>

# <h1 id="header-1">Day 1 -Inception of open-source EDA, OpenLANE and sky130 PDK</h1>	 
## <h1 id="header-1_1">How to talk to computers?</h1>
### <h1 id="header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>
#### Difference between chip and package
>* The chip is the core component where the actual processing happens.The package is the external enclosure that facilitates the chip’s use in electronic systems.Chip is the brain of the operation, while the package is the body that allows the brain to function in a practical and durable manner within electronic devices.

![Screenshot (571)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/12a15dbd-84c8-4d19-9a47-e8db57caddaf)


>*Packages are much larger than the chip itself and come in various forms, such as Dual In-line Package (DIP), Quad Flat Package (QFP), Ball Grid Array (BGA), etc. They are designed to provide a standardized way to connect the chip to the rest of the electronic system.
>*the connections from package is fed to the chip by WIRE BOUND method which is none other than basic wired connection.

![Screenshot (570)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/171f8fc9-f8cb-40b2-8f25-c448d0c3e80a)


#### Components 
(1) **Pads:** Pads are used to connect the internal circuitry of the chip to external circuits.Pads are used to send the signal inside the chip.</br>
(2) **Core:** The core is the heart of the chip, where the main processing or operational functions are performed. It contains the functional elements of the chip, such as the CPU, memory cells, logic gates, etc.</br>
(3) **Die:** The die encompasses the entire functional circuit and serves as the foundational piece that is packaged to create a usable component for electronic devices.</br>

![Screenshot (573)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/f9eae00f-b6d5-47b7-b39e-a3e27669147a)


#### RISC-V SOC
>* It consist of SRAM,SOC,ADC,DAC,SPI these all are called foundry IP's.All devices depends upon foundry where all chips are fabricated using deposition and lithography techniques and so on.

**Foundary:**  Foundry refers to a company or facility that specializes in the fabrication of semiconductor devices. It turns designs into physical chips. This includes photolithography, doping, etching, deposition, and other steps necessary to build the intricate structures of transistors and circuits on a silicon wafer.</br>

**Difference between macros and Foundry IPs:** FOUNDRY IP's are Intellectual Properties whereas MACROS are repeatable digital logic blocks.</br>
<b>Macros: </b>Optimized for general use within digital designs and may be reused across different projects and technologies.</br>
<b>Foundry IPs:</b> Optimized for specific foundry processes, ensuring they meet the process specifications and performance criteria of the foundry.</br>

![Screenshot (575)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/864b1cb4-0d54-4da5-aab0-564478de52da)

### <h1 id="header-1_1_2">Introduction to RISC-V</h1>
<b> ABOUT RISC-V ARCHITECTURE </b>

>* RISC-V is an open, versatile instruction-set architecture supporting diverse implementations.</br>
RISC-V is the first widely accepted open-source RISC processor.</br>
It features a base integer ISA, optional extensions, 32/64-bit variants, IEEE-754 floating-point support, and facilitates experimentation with privileged architectures, hypervisors, and parallel computing.

#### Intruction Set Architecture
To implement a C program on a specific hardware layout.<br>
**Compilation to Assembly Language:** The C program is initially compiled into an assembly language program using the RISC-V ISA (Reduced Instruction Set Computing - V Instruction Set Architecture).
<br>

**Conversion to Machine Language:** The assembly language program is then converted into a machine language program, which is in binary (logic 0 and 1). This binary code is what the hardware of the computer understands.
<br>

**RTL Implementation:** After obtaining the machine language program, we need to implement the RISC-V specification using an RTL (Register-Transfer Level) hardware description language. For example, we can use picorv32, which is an open-source implementation of the RISC-V ISA.
<br>

**RTL to Layout Flow:** The RTL code is then processed through a standard PnR (Place and Route) flow, often referred to as RTL to GDSII (Graphic Data System II). This flow typically involves synthesis, placement, routing, and other steps to generate the physical layout of the chip.
<br>
![Screenshot (576)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/6cf92767-7918-4e38-b09e-4c906e03388d)

### <h1 id="header-1_1_3">From Software Applications to Hardware</h1>

To run an application software on hardware, several processes take place involving both system software and hardware interaction. Here's a detailed step-by-step explanation of the process:

#### Application Software to Hardware Execution Flow
>* **1.Application Software Entry:-** The application software, written in a high-level language (e.g., C, C++, VB, or Java), enters the system software layer.

>* **2.System Software Components:-** The major components of system software involved in this process are the Operating System (OS), Compiler, and Assembler.

>* **3.Operating System (OS) Role:-** The OS manages the execution of application software and outputs small functions written in high-level languages (C, C++, VB, Java).
These functions are then handed over to the respective compiler.

>* **4.Compiler's Job:-** The compiler translates the high-level language code into assembly language instructions.
The syntax and structure of these instructions vary depending on the hardware architecture (e.g., x86, ARM, RISC-V) on which the system is implemented.
The output is often an executable file (.exe) that contains the compiled instructions.


>* **5.Assembler's Role:-** The assembler takes the assembly language instructions and converts them into binary format, known as machine language.
This machine language program is a sequence of binary codes (0s and 1s) that the hardware can understand.

>* **6.Binary Code Execution:-** The binary code is fed into the hardware, where it is executed. The hardware performs specific functions based on the binary instructions it receives.

![Screenshot (577)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/c1dd5aa6-c5bb-4891-a8dc-986f89ef0026)

#### EXAMPLE
* Suppose we have a C function to stop a stopwatch. This function enters the system software layer.
* The OS outputs this C function, and the compiler converts it into assembly language instructions tailored for the RISC-V architecture.
* The assembler then translates these RISC-V assembly instructions into binary machine code.
* This binary code is loaded into the chip (hardware), where it controls the stopping of the stopwatch.

![Screenshot (578)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/84210e79-b69d-4a65-9181-17cdac3062aa)

>* **1.Instruction Set Architecture (ISA):-** Instructions act as an abstract interface between the high-level language (C, C++) and the hardware.
In this case, the RISC-V Instruction Set Architecture (ISA) defines the instructions that the RISC-V hardware understands.

>* **2.Hardware Description Language (HDL) and RTL:-** To implement the RISC-V specifications on hardware, an HDL (e.g., Verilog) is used at the Register-Transfer Level (RTL).
The RTL code describes the hardware behavior.
>* The RTL code is then synthesized into a gate-level netlist, which describes the actual logic gates and connections required to perform the specified functions.
This netlist is used to fabricate the chip, ensuring the hardware performs the intended functions based on the binary instructions it receives.

![Screenshot (579)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/326ad533-edd7-4f37-8cf1-fb646cd1cc0b)


## <h1 id="header-1_2">Soc design and OpenLANE</h1>
### <h1 id="header-1_2_1">Introduction to all components of open-source digital asic design</h1>

Designing an ASIC (Application-Specific Integrated Circuit) involves several critical steps and the use of various tools and components.They are as follows:-
* **1.RTL (Register-Transfer Level) IPs:-** RTL is a level of abstraction used in describing the behavior of a digital circuit. RTL IPs (Intellectual Properties) are pre-designed, reusable blocks of RTL code that perform specific functions (e.g., memory controllers, communication interfaces, processors).
Example: A picorv32 core, which is an RTL implementation of a RISC-V processor.

* **2.EDA tools:-** EDA tools are software tools used to design and verify electronic systems such as ICs. They include various types of tools for different stages of the design process like Design Entry Tools,simulation tools,synthesis tools.
* **3.PDK Data:-** PDK (Process Design Kit) is a set of files and documentation provided by a semiconductor foundry that describes the manufacturing process and contains the necessary data to design and fabricate chips using that process.
 It includes design rules, device models, standard cell libraries, IO libraries, and technology files.
<br>
![Screenshot (585)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/681c7f48-734e-40dd-9dc7-664db53a65ad)

<b>SkyWater 130nm PDK</b>
Google has collaborated with SkyWater Technology, a semiconductor foundry, to provide open-source PDKs.The SkyWater 130nm PDK is a part of this initiative, offering designers access to a mature, reliable process technology that balances performance, power, and cost.Example: Intel Pentium 4 Extreme Edition (P4EE) @ 3.46GHz
![Screenshot (586)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/70df4495-3fc2-44f3-a6c5-3c12a699e389)
### <h1 id="header-1_2_2"> Simplified RTL2GDS flow</h1>
The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.<br>
The ASIC design flow is a complex and iterative process involving several stages, each critical to the successful creation of a functional integrated circuit (IC).
![Screenshot (587)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/de1f82c8-0361-4bf1-87b3-23ffa9ea80ef)
<b>1.SYNTHESIS</b>
* **Objective:** Convert the RTL code into a gate-level netlist.
* **Tools:** Use synthesis tools (e.g., Synopsys Design Compiler) to optimize the design for performance, area, and power.
* **Output:** A gate-level netlist that describes the logic gates and their interconnections.

![Screenshot (588)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/41535158-cac3-4e3a-b816-71eca7a968fe)
![Screenshot (589)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/1f9e8f3f-3f0a-43ef-ab54-c128b2d33776)

<b>2.Floor Planning</b>
* **Objective:** Organize the layout of the chip, determining the placement of macros, I/O pads, and standard cells.
Types:<br>
* **Macro Floorplanning:** Define dimensions and positions of large blocks (macros), as well as the routing paths.
* **Chip Floorplanning:** For full-chip implementation, considering power distribution, signal integrity, and clock distribution.

![Screenshot (591)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/73c3e60c-d072-4d3b-8419-2d614011a870)

<b>3.POWER PLANNING</b>
* **Objective:** Design the power distribution network to supply adequate power to all parts of the chip.
Steps:<br>
* **Construct Power Network:** Design power grids and straps to minimize resistance and ensure uniform power distribution.
* **Use Upper Metal Layers:** Thicker metal layers (e.g., M8) are used for power distribution to reduce resistance and improve reliability.

  ![Screenshot (590)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3585f003-8021-4407-8c2a-b3104b7f2557)
  
<b>4.PLACEMENT</b>
* **Objective:** Position the standard cells on the chip to minimize interconnect delay and optimize performance.
Types:<br>
* **Global Placement:** Find an optimal approximate position for cells without concern for legal placement. Ensures cells are close to minimize interconnect lengths.
* **Detailed Placement:** Adjust the positions from global placement to ensure all cells are legally placed without overlaps.

  ![Screenshot (592)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/299e9b01-30ef-4535-b73a-e73ea8494644)
  
<b>5.Clock Tree Synthesis (CTS)</b>
* **Objective:** Distribute the clock signal uniformly across the chip to minimize clock skew (differences in clock arrival times at different components).
Steps:<br>
* Design a clock tree structure that ensures balanced and synchronized clock distribution.
* Minimize skew and optimize for power and timing.

  ![Screenshot (594)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/7e8b6be9-29c0-48a5-a95b-ef90c8801ed9)
  
<b>6.ROUTING</b>
* **Objective:** Connect all the placed cells according to the netlist.
Types:<br>
* **Global Routing:** Plan the general routes for connections, focusing on optimal pathfinding without detailed geometric considerations.
* **Detailed Routing:** Finalize the exact geometric paths for all connections, ensuring they adhere to design rules and manufacturing constraints.
* skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.
![Screenshot (595)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/15a27333-1383-44cc-ac0f-fc292c618ece)

<b>7.SIGN OFF</b>
* **Objective:** Ensure the design meets all functional, timing, and manufacturing requirements before tape-out.
Steps:<br>
* **Design Rule Checking (DRC):** Verify that the layout adheres to the foundry's manufacturing rules.
* **Layout Versus Schematic (LVS):** Ensure the final layout matches the original gate-level netlist.
* **Static Timing Analysis (STA):** Confirm that all timing constraints are satisfied and that the circuit will run at the designated frequency.

### <h1 id="header-1_2_3">Introduction to OpenLANE and Strive chipsets</h1>
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

<b>Strive SoC Family</b>
Strive is a family of open everything SoCs.
* Open PDKs, Open EDA, Open RTL
![Screenshot (599)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/67b2b4c5-b397-4085-9ce4-e3b21404eb30)

The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop).

* No LVS violations
* No DRC Violations
* No timing Violations
OPENLANE is tuned for skyWter130nm open PDK. It can be used to harden Macros and chips.
It has two modes of operation:-
* Autonomus : Tt is the push botton flow due to this push botton, we get final GDSII
* Interactive : In this we can run commands and steps one by one.
It has large number of design examples(43 designs with their best configurations).

### <h1 id="header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</h1>

OpenLANE provides a comprehensive ASIC design flow that includes various stages from design entry to physical verification. Let's break down the detailed flow, incorporating each stage and how OpenLANE addresses them:
![Screenshot (598)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/56e7947c-e0a0-493b-9460-0824af666067)

The design exploration utility is also used for regression testing(CI).
<b>1. DFT (Design for Test)</b>
* **Objective:** Ensure the ASIC design is testable and can be reliably manufactured.
* **Scan Insertion:** Integrate scan chains into the design to facilitate testability.
* **Automatic Test Pattern Generation (ATPG):** Generate test patterns to detect and diagnose faults in the design.
* **Test Patterns Compaction:** Optimize test patterns for efficient testing and fault coverage.
* **Fault Coverage and Simulation:** Assess the effectiveness of test patterns in detecting faults and simulating various fault scenarios.

<b>2.Physical Implementation with OpenROAD</b>
* **Objective:** Transform the logical design into a physical layout.
* **Floor/Power Planning:** Organize the layout to optimize power distribution and signal routing.
* **End Decoupling Capacitors and Tap Cells Insertion:** Integrate decoupling capacitors and tap cells for stable power distribution and signal integrity.
* **Placements (Global and Detailed):** Place cells on the chip, optimizing for performance and minimizing wirelength.
* **Post Placement Optimization:** Refine placement to improve timing, area, and power.
* **Clock Tree Synthesis (CTS):** Generate a clock distribution network to ensure synchronous operation.
* **Routing (Global and Detailed):** Connect placed cells with wires, optimizing for signal integrity and manufacturability.
  
<b>Verification and Antenna Rules Violation Handling</b>
* **LCE (Yosys):** Formally confirm that design function remains unchanged after netlist modifications.
* **Antenna Rules Violation Handling:** Preventive approach by adding fake antenna diode cells and replacing them with real ones if violations occur during routing.
  
<b>3. Static Timing Analysis (STA)</b>
* **Objective:** Assess the timing performance of the design.
* **Interconnect RC Extraction (DEF2SPEF):** Extract resistance and capacitance information from the routed layout.
* **STA (OpenSTA):** Analyze timing constraints and identify violations, if any, to ensure timing closure.
  
<b>4. Physical Verification (DRC and LVS)</b>
* **Objective:** Ensure the design meets manufacturing requirements and is free from errors.
* **Design Rule Checking (DRC):** Verify layout against design rules to ensure manufacturability.
* **SPICE Extraction from Layout: Generate SPICE netlists from layout for detailed analysis.
* **Layout Versus Schematic (LVS): Compare layout against schematic to ensure functional correctness and electrical connectivity.

> OpenLANE provides a comprehensive ASIC design flow, addressing various stages from design entry to physical verification. By incorporating DFT techniques, physical implementation with OpenROAD, verification, and static timing analysis, designers can ensure their designs meet functional, timing, and manufacturing requirements. Additionally, the handling of antenna rules violations and thorough physical verification further enhance the reliability and manufacturability of the ASIC design.

## <h1 id="header-1_3">(LAB WORK)Get familiar to open-source EDA tools</h1>
### <h1 id="header-1_3_1">OpenLANE Directory structure in detail</h1>
