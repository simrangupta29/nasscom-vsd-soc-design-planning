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
**Pin Placement**
