# <h1 id="header-1">Day 1 -Inception of open-source EDA, OpenLANE and sky130 PDK</h1>	 
## <h1 id="header-1_1">How to talk to computers?</h1>
### <h1 id="header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>
#### Difference between chip and package
>*The chip is the core component where the actual processing happens. The package is the external enclosure that facilitates the chip’s use in electronic systems.Chip is the brain of the operation, while the package is the body that allows the brain to function in a practical and durable manner within electronic devices.

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


