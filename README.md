ECE281_Lab5
===========

More PRISM


# Functionality

I got full functionality of Part 1 for this lab on Friday, 18 APR at 1045. I demonstrated this functionality to Dr. Neeble.

I demonstrated full functionality, on the FPGA, for part 2 to Capt Silva on Friday 25 APR at 1030. This is one calender day late from the due date.




# Discussion

I had some trouble with the first program, in the Nexys2 top shell. I had to change Clockbus_sig from 19 to 20. 

First program Operation:
  This program loads a value and then adds one to it until the value in the accumulator reaches '0' and the program ends. In this case, the initial value that is loaded into the accumulator is 8, so the count goes: 0, 8, 9, a, b, c, d, f, 0. The count stops after the value reaches '0'. The reason that the count stops is because '0' is not a negative number, which is the condition for the jump to occur. The program wouldn't work if it initally loaded values 0-7 because those are positive numbers and the program would end after only counting up once. 
  
First program instruction cycles:
  1. Fetch - get the opcode and put it into the IR (IRLD is high)
  2. Decode - get the operands, set up datapath to execute
  3. Execute - tell computer what it needs to perform the operation
  

Answer to PRISM Questions:
1. When the controller's current state is "FETCH", what is the status of the following control lines:
    a. PCLd - high
    b. IRLd - high
    c. ACCLd - low

2. The current state is Decode LoAddr and the IR contains "OUT." What are the control signals asserted, and what will the next state be?
    Next state is "Direct 10 Execute"
    asserted: marlold, pcld, memsel_l

3. What are the three status signals sent from the PRISM datapath to the PRISM controller?



4. Why is it important that ACCLd signal be active during the execute state for the ADDI instruction?
    When ACCLd is active, the value in the accumulator will change. In this case, it needs to be active so that the new value from the addition is put into the accumulator.

5. What changes are necessary to the PRISM datapath to add another instruction (SUBI, which would subract an immediate value from the accumulator) to the instruction set?
    If you wanted more instructions, you would have to add another bit so that it could store the instruction the databus would have to become larger for the extra bit. So would every other 4-bit register. The address locations can still be referenced with 8 bits.
