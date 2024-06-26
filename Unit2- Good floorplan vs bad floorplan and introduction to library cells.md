<div class="day2">
  <ul>
    <li><a href="#header-2">Day 2 - Good floor planning considerations</a></li>
	<ul>
        <li><a href="#header-2_1"> Chip Floor planning consideration</a></li>
		<ul>
			<li><a href="#header-2_1_1">Utilization factor and aspect ratio</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_2">Concept of pre-placed cells</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_3">De-coupling capacitors</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_1_4">Power planning</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_5">Pin placement and logical cell placement blockage</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_6">Steps to run floorplan using OpenLANE</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_7">Review floorplan files and steps to view floorplan/a></li>
		</ul>
	      <ul>
		      <li><a href="#header-2_1_8">Review floorplan layout in Magic</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-2_2">Library building and Placement</a></li>
	      <ul>
			<li><a href="#header-2_2_1">Netlist binding and initial place design</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_2">Optimize placement using estimated wire-length and capacitance</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_3">Final placement optimization</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_2_4">Need for libraries and characterization</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-2_3">Cell design and characterization flows</a></li>
		 <ul>
			<li><a href="#header-2_3_1">Inputs for cell design flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_2">Circuit design steps</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_3">Layout design step</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_3_4">Typical characterization flow</a></li>
		</ul>
      </ul>
	  <ul>
        <li><a href="#header-2_4">General timing characterization parameters</a></li>
		   <ul>
			<li><a href="#header-2_4_1"> Timing threshold definitions</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_4_2">Propagation delay and transition time</a></li>
		</ul>
      </ul>
</div>

# <h2 id="header-2">Day 2 - Good floor planning considerations</h2>	 
## <h2 id="header-2_1">Chip Floor planning consideration</h2>
### <h2 id="header-2_1_1">Utilization factor and aspect ratio</h2>
In  order to define width and height of core and die we take example of a simple netlist.Netlist is basically connectivities.The dimensions of the chip depends upon the dimensions of the logic gate.
![Screenshot (601)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/663797e9-06d9-4153-9135-371a8b379ca6)

we are interested in the dimensions of the standard cell so lets take a rough dimension.
![Screenshot (603)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/642fa305-060e-4b99-b1d0-846487b2ba07)

* **Die** which consists of core, is small semicondcutor material  specimen on which the fundamental circuit is fabricated.
* **Core** is the section of the chip where the fundamental logic of the design is placed.
 <b>UTILISATION FACTOR</b>
  
 ```
Utilization Factor = Area occupied by netlist / Total area of the core
```
Now, Let's try to place that particular logic inside the core. The netlist will occupy the whole area inside the core it means it utilizes the core 100%.The leftover area can be used to placed some additional cells like buffers, something else or for optimatisation.It can also be used for routing.
<b>ASPECT RATIO</b>
```
Aspect Ratio = Height /  width
```
If Aspect Ratio is 1 it signifies that chip is square shaped. If it is not 1 it means the chip is in rectangular shape.

### <h2 id="header-2_1_2"> Concept of pre-placed cells</h2>

>  preplaced cells are specific instances of cells or blocks that are manually positioned in the layout before the automatic placement of standard cells.
![Screenshot (605)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/78fa8d54-06d1-454d-88b5-5735b3ddede7)

Lets take a combinational logic which does some amount of function and assume its a huge circuit having some N Logic gates so let's divide it into some small numbers of gates. We will cut the whole circuit into two parts, and separate both of them into two blocks and both block will be implemented seperately.
![Screenshot (605)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/bcda07d6-9b85-4b9e-8aa3-89f50dd0c77d)

We can implement it once only but can use it multiple times. Similary there are other IP's also available for eg. Memory, Clock-gating cell, Comporator, MUX  all of these are part of the top level netlist.They recieve some signals and perform functions and deliver the outputs but the functionality of the cell is implemented only once. 
* The arrangement of these IP's in a chip is referd as **floorplanning**.
* These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called **"pre-placed cells"**. 
* These cells are placed in such a way that, the placement and routing tool do not touch the location of the cell.

### <h2 id="header-2_1_3">De-coupling capacitors</h2>
> Decoupling capacitors (decaps) play a critical role in ensuring stable and reliable operation of the integrated circuit. They are strategically placed around preplaced cells and throughout the chip to mitigate the effects of noise and voltage fluctuations.

<b>Function of Decoupling Capacitors</b>
* **1.Stabilizing Voltage Supply**
* When a gate, such as an AND gate, switches from 0 to 1 or 1 to 0, it requires a certain amount of switching current due to the capacitance associated with it. This capacitance must be fully charged to represent a logic '1' and completely discharged to represent a logic '0'.
* During switching, the instantaneous current demand causes a voltage drop across the resistive (Rdd) and inductive (Ldd) components of the power delivery network. This results in the supply voltage at the gate (Vdd') being lower than the intended Vdd, potentially causing the logic level to drop below the threshold required for a reliable logic '1'.
   ![Screenshot (606)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/ffb5ded2-49a2-4150-a65b-bdc18179b9ac)
> Above figure shows the problem of voltage drop in absence of decoupling capacitors.

* For example, if the ideal logic '1' is 1 volt, due to the voltage drop it gets less. This deviation can lead to unreliable operation if the voltage falls outside the noise margin.
 ![Screenshot (607)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5fd861c6-6952-4651-8fe6-897bf0e397af)

  * **2.Providing Instantaneous Current:**
  * Decoupling capacitors are placed in parallel with the circuit to provide the necessary instantaneous current when the circuit switches. This helps maintain the voltage at the required level.
![Screenshot (608)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/624c8870-9048-4b4f-aee7-e340ec58f274)

  * When the circuit switches, it draws current from the decoupling capacitor (Cd), which can supply the current quickly due to its low impedance. The main RL network replenishes the charge in Cd over time.
![Screenshot (609)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/cfa0ac00-7ed9-4501-bb92-8a02c4369a14)
> In the chip layout, decoupling capacitors are placed between Block A, Block B, and Block C to ensure a stable power supply. This strategic positioning provides the necessary instantaneous current during switching events, maintaining voltage stability. Consequently, local power distribution and communication within the chip are effectively managed.

### <h2 id="header-2_1_4">Power planning</h2>
<b>Problem:</b>

* Consider a local circuit as a black box that can be replicated multiple times, with logic present at its boundaries. The current demand problem is resolved using decoupling capacitors. However, a new problem arises when a signal is sent from a driver to a load, transitioning from logic 0 to logic 1. It is essential to maintain the integrity of this signal along the entire path so that the load receives it correctly.
![Screenshot (610)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/b413529b-1c5c-4d19-b662-2fec4ca14313)

* Assume a 16-bit bus that needs to retain the same signal from the driver to the load, requiring sufficient power from the supply. Since it is not feasible to place decoupling capacitors everywhere, and the power supply is distant from the bus, a voltage drop inevitably occurs.
  ![Screenshot (611)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/dc1a9bcb-20a1-460d-9a66-982e0ffead67)

> When one line of the 16-bit bus is logic 1, the capacitor is charged to Vdd. Conversely, when the line is logic 0, the capacitor is discharged to ground. Consider this 16-bit bus connected to an inverter, causing all initially charged capacitors to discharge and vice-versa. The issue arises because all capacitors connect to a single ground, leading to a bump in the 'ground' tap point during discharging, known as Ground Bounce.

> If the bump size exceeds the noise margin level, it may enter an undefined state, making the signal unpredictable. Similarly, when capacitors charged to 0 volts must charge to V volts through a single Vdd tap point, it lowers the voltage at the Vdd tap point. As long as this voltage drop stays within the noise margin, it's acceptable, but if it enters an undefined region, it becomes unpredictable.

<b>Solution:</b>
* The problem of lowering supply voltage occurs because power is applied at only one point. The solution is to use multiple power supplies. This approach ensures that every block draws power from the nearest supply and dumps charge to the nearest ground, reducing voltage drops and ground bounces. It is mess power supply distribution.
  ![Screenshot (612)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/f9135d5b-4401-4cd2-9bfd-23735cbca55a)
  
So the final power planning with the mesh solution would look like:-
![Screenshot (613)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/00ab18bf-4bbf-4e24-b488-d7f3bc38517d)

### <h2 id="header-2_1_5">Pin placement and logical cell placement blockage</h2>
In chip design, pin placement and logical cell placement blockage are critical steps in the floor planning process.
<b>Example Design Overview</b>

> Consider a design with two circuits driven by different clocks, clk1 and clk2, with inputs Din1 and Din2 and outputs Dout1 and Dout2. There are also preplaced cells, BlockA and BlockB.
* BlockA receives inputs from Din1 and Din2.
* BlockB receives inputs from clk1 and clk2 and provides a clock output (clkOut).
This design has:
* 4 input ports: Din1, Din2, clk1, clk2
* 3 output ports: Dout1, Dout2, clkOut
Additionally, a more complex design with 6 input ports and 5 output ports is mentioned, demonstrating the need for careful pin placement and connectivity.
<b>Netlist and Core Integration</b>
> The connectivity information between the gates is coded in VHDL/Verilog, forming the netlist. This netlist is then placed within the core of the chip design. The area between the core and the die (the chip’s boundary) needs to be filled with pin information.
![Screenshot (616)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/ae96c131-4901-4af5-b047-50636823da1a)

<b>Pin Placement</b>
Pin placement is a collaborative effort:
* The frontend team designs the netlist and determines the connectivity of inputs and outputs.
* The backend team handles the physical pin placements on the chip.
Pins need to be placed strategically:
* Preplaced blocks (BlockA and BlockB) should be located near their respective input pins (Din1, Din2, clk1, clk2) for efficient signal routing.
* Clock pins (clk1, clk2, clkOut) are larger than other pins because they need to provide continuous signals with minimal resistance. Larger pins reduce resistance, ensuring faster and more reliable signal transmission.
  ![Screenshot (617)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5b77c186-a8dc-49d5-b928-40764769d56b)

<b>Logical Cell Placement Blockage</b>
> When placing pins, it’s essential to block certain areas to prevent routing and cell placements in these regions. This is known as logical cell placement blockage:

* The area around pin placements is blocked to ensure that routing and cell placement do not interfere with the signal paths.
* This blockage ensures that the signal paths for critical connections, like clock signals, remain unobstructed and efficient.
  ![Screenshot (618)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/4fb2b2eb-8cb8-4fca-9344-59b388e925b3)
### <h2 id="header-2_1_6">Steps to run floorplan using OpenLANE</h2>
Before run the floorplanning, we require some switches for the floorplanning. these we can get from the configuration from openlane.
* In order to do that we open README file of configuration folder,we will see the variables which are required at each step.
  by entering
  ```
  less README.md
  ```
  ![soc22](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/fbc6e285-096f-42f1-8b39-f4bf624ebb94)

* We can also see the synthesis ,library files,global variables,constraints set.These variables are switches
* We have FP_CORE_UTL set as 0.5 and FP_ASPECT_RATIO set as 1 by default,similiarly we have defined margined value,vertcal,horizontal etc.
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/0bdb634b-8a9d-4976-8858-029c50fb5b69)
  Now we will see where are these switches set so if we will do
```
less floorplan.tcl
```
we can see the switches set in the floorplan.tcl.
* Here FP_IO_MODE says how we want our pin configuration to be around.0 means pin positioning is random but it is on equal distance.
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/d0c3a636-5ad8-43e4-ba08-d9d49951b759)
In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).<br>

Now we see, with this settings how floorplan run.<br>
Give the following command
```
run_flooplan
```
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3969cf04-3fc8-4fe4-923f-a7f04dd2f6ca)

### <h2 id="header-2_1_7">Review floorplan files and steps to view floorplan</h2>
In the run folder, we can see the config.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.
The runs folder will contain the latest folder by today's date so let's open config.tcl of runs 
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/8d7771cb-f27a-4b7d-9305-bfb2841ce222)
> The latest runs config.tcl shows utilisation factor as 35 whereas in sky130A_sky130_fd_sc_hd_config.tcl of picorv32a we have utitisation factor as 35. so latest uf is overwritten by confif.tcl ,which is then overwritten by sky130A_sky130_fd_sc_hd_config.tcl.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/d8a11c03-63ae-432d-8936-03001e395d20)

To watch how floorplane looks, we have to go in the results. in the result, one def( design exchange formate) file is available.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/e7c59925-10ff-43f3-9637-0364d9e64ed1)
if we open this file, we can see all information about die area (0 0) (660685 671405), unit distance in micron (1000). 
* It means 1 micron means 1000 databased units. so 660685 and 671405 are databased units. and if we divide this by 1000 then we can get the dimensions of chips in micrometer.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/8209085a-1cd9-4f8b-977c-393ff704c9b4)

So, the width of chip is 660.685 micrometer and height of the chip is 671.405 micrometer.
#### TASK2
```
Area of the chip = width*height
Area = 660.685*671.405 square micronmeter.
Area = 443,587.212425  square micronmeter.
```
To see the actual layout after the flow, we have to open the magic tech file by adding the command
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def
```
 Magic file will open. <br>
 Now we can see the layout.
 
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5fc71de7-650e-4814-9eba-deefd5d03621)

### <h2 id="header-2_1_8">Review floorplan layout in Magic</h2>
To place the layout in center
* press S for selecting and then "V".
  ![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/7e6aaaa4-d4ee-4577-a91e-6d63b8b7262d)

In the layout we can see that, input output pins are at equal distance.

after selecting (To select object, first click on the object and then press 's' from keyboard. the object will hightlited. to zoom in the object, click on the object and then press 'z' and for zoom out press 'sft+z') one input pin, if we want to check the location or to know at on which layer it is available, we have to open tkcon window and type "what". it will shows all the details about that perticular pin.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/eb60644a-3e04-40a5-ada7-f272ffc3dfb6)
It shows that selected subcell is in the topmost section of picorv32a.

![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/51ea395e-95d5-495d-bee5-e66daca72a38)

> The pin at the end  is in the metal 3.similarly doing for the vertical pins, we find that this pin is at metal 2.

Along with the side rows,the Decap cells are arranged at the border of the side rows.<br>
here we can see that first standerd cells is for buffer 1. similarly other cells are for buffer 2, AND gate etc.<br>
* At the lower end standard cells are present.
![image](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/4277ecd5-07ea-4909-a590-5827a1356a97)

## <h2 id="header-2_2">Library building and Placement</h2>
### <h2 id="header-2_2_1">Netlist binding and initial place design</h2>

![Screenshot (620)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/0b683bb3-52a8-4519-bde3-5c4cac8155da)

<b> Netlist and Gate Shapes:</b><br>

* A netlist contains the logic gates and their connections. Each gate, such as a NOT gate or an AND gate, has a specific shape representing its functionality.
* In practice, these gates are not just symbolic shapes but have physical dimensions—width and height. For example:
A NOT gate may be symbolically a triangle, but in reality, it's a rectangular box.
* Similarly, AND gates and flip-flops are also represented as rectangular boxes.
* Each component in the netlist is assigned a physical shape with specific dimensions. This transformation from symbolic shapes to physical dimensions is necessary for real-world implementation.

![Screenshot (621)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/e8d083dd-61b8-4bda-b7f5-22ff0508e2ac)

<b>Library Concept:</b><br>
* A library is like a repository where all types of gates and flip-flops (represented as books) are stored.
* This library includes not only the shapes and sizes of these components but also their timing information, such as gate delays.
* Libraries can be divided into sub-libraries:
* One sub-library for physical dimensions (shapes and sizes).
* Another sub-library for timing information (delays and performance characteristics).
* Different flavors of each cell might exist, allowing choices based on size and timing requirements. Larger cells have lower resistance and delay but occupy more space.

  ![Screenshot (622)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/5d211fac-cdd7-4532-a8a9-4b758a5e876d)

#### Placement
<b>Floorplan Setup:</b><br>
* Once shapes and sizes are assigned to all gates, the next step is to place these physical shapes onto the chip's floorplan.
* The floorplan includes the positions of input and output ports and the preplaced cells (previously determined blocks that should not be moved).
  
<b>Placing Components:</b><br>
* With the netlist, physical dimensions, and floorplan in hand, the next task is to place the gates according to their logical connections.
* The placement process ensures that preplaced cells remain in their designated locations and no new cells overlap these areas.
* The goal is to maintain logical connectivity while minimizing the distance between connected components to reduce delay.

### <h2 id="header-2_2_2">Optimize placement using estimated wire-length and capacitance</h2>

#### Optimize Placement
* **1.Problem of Distance:**
* In chip design, components (like flip-flops, FF1) need to be placed close to their inputs (like Din2) to minimize delays. If the distance between these components is too large, it creates significant issues due to increased wire length and capacitance.
  
* **2.Estimating Capacitance and Resistance:**
* Before the actual routing of wires, we can estimate the capacitance and resistance based on the wire length. Longer wires have higher capacitance and resistance, making it difficult for signals to travel efficiently.

![Screenshot (623)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/3efbe642-43cb-408c-906e-14e717b13019)

* **3.Impact on Signal Integrity:**
* If the signal has to travel a long distance from Din2 to FF1, it might degrade and become difficult for FF1 to process. This degradation happens because the signal loses strength over long distances due to high capacitance and resistance.
  
* **4.Using Repeaters:**
* To maintain signal integrity, repeaters (buffers) are used.
* Repeaters refresh the signal, restoring it to its original strength and sending it forward. This process repeats until the signal reaches its destination.
* The use of repeaters ensures that the signal maintains its integrity throughout its journey from the input to the desired component.
  
* **5.Placement of Repeaters:**
* Repeaters are strategically placed along the path from Din2 to FF1. These intermediate steps ensure that the signal is successfully driven to FF1 without degradation.
* While repeaters solve the problem of signal integrity, they do consume additional area on the chip. Hence, their use needs to be balanced with available space on the floorplan.
 
* **6.Stages of Placement:**
* Stage 1: If the components are close enough, there may be no need for repeaters, as the signal can travel directly without significant degradation.
* Stage 2: For longer distances, repeaters are essential to ensure the signal reaches its destination without losing strength. This is particularly important for maintaining performance in high-speed circuits.

### <h2 id="header-2_2_3">Final placement optimization</h2>

<b>Stage 3&4  Optimization:</b><br>
* Similar to stage 2, stage 3 also necessitates the use of a buffer. For instance, placing a buffer between gate2 and FF2 ensures that the signal does not degrade due to the long distance between these components.
* Stage 4 is more complex compared to stages 2 and 3. It involves a careful analysis to ensure the correctness of our optimizations. This is achieved through timing analysis.

![Screenshot (625)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/e4a32374-6acc-46e5-80b9-771e54d99220)

* **Timing Analysis:**
* Timing analysis involves evaluating the design with ideal clocks to check if the placement of components and the use of repeaters are correct.
* By analyzing the timing data, we can determine whether the signals reach their destinations within the required time constraints. This helps in verifying the overall correctness of the placement and ensures that the design meets the necessary performance criteria.

### <h2 id="header-2_2_4">Need for libraries and characterization</h2>

> Every IC design flow stage relies heavily on libraries and characterization. Libraries offer the building blocks for the design, while characterization ensures that these blocks perform correctly and efficiently. Together, they enable designers to create reliable and high-performance integrated circuits.

<b>Libraries:</b><br>
* Contain standard cells (gates, flip-flops, buffers, etc.) with defined physical and electrical properties.
* Provide the necessary information for logic synthesis, placement, CTS, and routing.
* Include multiple versions of each cell, optimized for different performance and area requirements

![Screenshot (626)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/cbc73691-3d05-4cd0-9a7b-4fdf57f7fd30)

<b>Need of libraries in various steps:-</b><br>

![Screenshot (629)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/9fc239f0-25f3-47ac-adc0-31e77b43d2d8)

* **1.Need for Libraries in logic synthesis**: Libraries provide the standard cells (gates and flip-flops) used in logic synthesis. Each cell in the library has defined electrical characteristics and physical dimensions.
* **2.Need for Libraries in floor planning:** Libraries help determine the physical dimensions and placement constraints of each cell, which are essential for effective floorplanning.
* **3.Need for Libraries in placement:** Libraries provide the physical dimensions and placement rules for each cell, ensuring that they are placed correctly to meet timing requirements.
* **4.Need for Libraries in CTS:** Libraries include detailed timing information for clock buffers and other cells, which is crucial for designing an effective clock tree.
* **5.Need for Characterization in Routing:** Characterization data for each cell, such as delay, capacitance, and resistance, helps in accurate routing and ensures signal integrity.

  ![Screenshot (630)](https://github.com/simrangupta29/nasscom-vsd-soc-design-planning/assets/130252328/4596083e-43f1-4930-b6fc-40a4e784f20b)

* **6.Need for Characterization:** Characterization provides the timing parameters for each cell, which are essential for accurate timing analysis.

  ### <h2 id="header-2_2_5">Congestion aware placement using RePlAce</h2>
Currently, our primary concern is not timing, but congestion. We aim to minimize congestion during placement.
> Placement occurs in two stages: global and detailed. In global placement, legalization does not take place; it happens after detailed placement.When we run the placement, global placement happens first.

