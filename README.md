ECE281_Lab3
===========

#####Elevator Controller
#####C3C Kevin Cabusora
#####ECE 281
#####Dr. Neebel, M6

#Prelab

![Prelab3Schematic](https://github.com/KevinCabusora/ECE281_Lab3/blob/master/Prelab3Schematic.png?raw=true "Prelab3Schematic")

![alt text](Nexys2_top_shell.vhd)

![alt text](nexys2_sseg.vhd)

![alt text](Clock_Divider.vhd)

![alt text](pinout.ucf)

![alt text](nibble_to_sseg.vhd)

#Code Critique
===============
##Bad Code
===============
In the main lab, I had both the Moore and Mealy controllers running, but had assigned the same switches to both, and could not figure out why a .bit file would not process.
```
  Moore_ElevatorController : MooreElevatorController_Shell PORT MAP(
		clk => ClockBus_sig(25),
		reset => switch(7),
		stop => switch(0),
		up_down => switch(1),
		floor => floor_signal
	);

	Mealy_ElevatorController : MealyElevatorController_Shell PORT MAP(
		clk => ClockBus_sig(25),
		reset => switch(7),
		stop => switch(0),
		up_down => switch(1),
		floor => floor_signal,
		nextfloor => next_floor
		);
```
##Good Code
=============
I fixed the problem by commenting out the Moore_ElevatorController code I processed before the Mealy, and removed the Moore Controller from the Hiearchy.  This fixed my problem.
```
  --Moore_ElevatorController : MooreElevatorController_Shell PORT MAP(
		--clk => ClockBus_sig(25),
		--reset => switch(7),
		--stop => switch(0),
		--up_down => switch(1),
		--floor => floor_signal
	--);

	Mealy_ElevatorController : MealyElevatorController_Shell PORT MAP(
		clk => ClockBus_sig(25),
		reset => switch(7),
		stop => switch(0),
		up_down => switch(1),
		floor => floor_signal,
		nextfloor => next_floor
		);
```
#Demo
========
##Basic
- Moore: Yes (commented out to allow for Mealy)
- Mealy: Yes

##B Functionality
- More Floors (Prime Numbers): No
- Change Imputs (7 Floors): Yes

##Video for Proof
- Would not upload to GitHub successfully; if you would like to see proof I could show it to you on my phone.

Documentation
===========
I received help from C3C Jonas, who pointed out syntax errors in my code (i.e. a missing semicolon in the line before, designating output of nextfloor different to input next_floor)








