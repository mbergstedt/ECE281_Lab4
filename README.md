ECE281_Lab4
===========

####Design
ALU Modifications: I used a process to get the final assignment value.  I used the following schematic to
determine how to assign the result with each selector value.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/ALU_Schematic.JPG?raw=true)

The values for result were taken from either the accumulator or data and had an operation performed on them, or
they were just copied.  For NEG, convert the inverse of the accumulator to a number, then add one and revert to a
standard logic vector.  ADD follows similar logic, but the accumulator is not inverted and the number form of data
is added.  With ROR, each value of the result is set to the value one location higher in accumulator.

ALU Test and Debug: The simulation ran without any issues on the first try.  The results are below.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/ALU_screenshot.JPG?raw=true)

Each of the values in the result matched what was expected with the given operations selector, accumulator value,
and data value.  For example, when the selector was 011, the code for rotate right, the accumulator had values of
1001, 1010, and 1011, for which the values in result matched as 1100, 0101, and 1101.

Datapath Modifications: I copied over the ALU declaration by using the view HDL instatiation option in
implementation.  Then, using the schematic given in the lab document, I filled in the code for the Instruction
Register, the Memory Address Registers, Hi and Lo, the Address Selector, and the Accumulator.  Before the
Accumulator, I included the instantiation for the ALU.  Data is given the value on the accumulator when the value
to enable it is on, otherwise data is given the value of all Z.  The value that shows if the accumulator is less
than zero was set to the most significant bit in the accumulator, and the value that shows if the accumulator is
zero was set to one if the accumulator contains all zeros, otherwise it is a zero.

Datapath Test and Debug: A semicolon needed to be removed in the component declaration of the datapath and a comma
needed to be removed in the instantiation of the datapath.  The results are below.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/Datapath_screenshot.JPG?raw=true)

Other results at lower zooms are also included in the repository.  When I first wrote the program, I had when the
reset is 1 set the accumulator to zeros, while all of the others were only set to zeros when the reset was 0, thus
when I did step 11 and I looked at my simulation, the value in accumulator never changed.  When I changed this,
the accumulator value changed as it should.  The testbench screenshots for this part were not affected because
they did not display the accumulator.

##Lab Functionality
-ALU Simulation
-Datapath Simulation Demo

####Reverse Engineering
Simulation Analysis: The analysis of the 50 ns to 100 ns time is below.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/50to100_analysis_shot.JPG?raw=true)

The analysis of the jump instruction at 225 ns is below.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/225_jump_analysis.JPG?raw=true)

PRISM Program: Below is a screenshot of the PRISM simulator running a program that takes the same actions as the 
VHDL program.
![alt text](https://github.com/mbergstedt/ECE281_Lab4/blob/master/PRISM_screenshot.JPG?raw=true)
