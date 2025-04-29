# cs2200---project-2-interrupts-solved
**TO GET THIS SOLUTION VISIT:** [CS2200 – Project 2: Interrupts Solved](https://www.ankitcodinghub.com/product/cs2200-project-2-interrupts-solved-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;110986&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS2200 - Project 2: Interrupts Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
1 Introduction

We have spent the last few weeks implementing our 32-bit datapath. The simple 32-bit LC-22 is capable of performing advanced computational tasks and logical decision making. Now it is time for us to move on to something more advanced—the upgraded LC-22a enables the ability for programs to be interrupted. Your assignment is to fully implement and test interrupts using either the provided datapath or your project 1 datapath. You will hook up the interrupt and data lines to the new timer device, modify the datapath and microcontroller to support interrupt operations, and write an interrupt handler to operate this new device. You will also use the tiny, inexpensive LC-22a as an embedded system to monitor a kitchen appliance.

2 Requirements

Before you begin, please ensure you have done the following:

• The LC-22a assembler is written in Python. If you do not have Python 2.6 or newer installed on your system, you will need to install it before you continue.

3 What We Have Provided

• A reference guide to the LC-22a is located in Appendix A: LC-22a Instruction Set Architecture. Please read this first before you move on! The reference introduces several new instructions that you will implement for this project.

• A CircuitSim circuit (int-devices.sim) containing a timer device and toaster temperature system subcircuit that you will use for this project. You should copy and paste the contents of the new devices into subcircuits in your main circuit file.

• A new microcode configuration spreadsheet microcode.xlsx with additional bits for the new signals that will be added in this project.

• A timer device that will generate an interrupt signal at regular intervals. The pinout and functionality of this device are described in Adding an External Timer Device.

• A toaster temperature system that will generate an interrupt signal at regular intervals, and provides toaster temperature system readings. The pinout and functionality of this device are described in Adding a toaster temperature system.

• An incomplete assembly program prj2.s that you will complete and use to test your interrupt capabilities.

1

• An assembler with support for the new instructions to assemble the test program.

• A microcode file (microcode.xlsx) that meets the requirements of Project 1; however, feel free to supply your own.

4 Phase 1 – Implementing a Basic Interrupt

Figure 1: Basic Interrupt Hardware for the LC-22a Processor

For this assignment, you will add interrupt support to the LC-22a datapath. Then, you will test your new capabilities to handle interrupts using an external timer device.

Work in the LC-22a.sim file. If you wish to use your existing datapath, make a copy with this name, and add the devices we provided.

4.1 Interrupt Hardware Support

First, you will need to add the hardware support for interrupts.

You must do the following:

1. Our processor needs a way to turn interrupts on and off. Create a new one-bit “Interrupt Enable” (IE) register. You’ll connect this register to your microcontroller in a later step.

2. Create the INT line. The external device you will create in 4.2 will pull this line high (assert a ’1’) when they wish to interrupt the processor. Because multiple devices can share a single INT line, only one device can write to it at once. When a device does not have an interrupt, it neither pulls the line high nor low. You must accommodate this in your hardware by making sure that the final value going to the microcontroller always has a value (i.e. not a blue wire in CircuitSim). This can be done by using a specific gate to act like a pull-down resistor so that there is always a value asserted (See Appendix C for more information)..

3. When a device receives an IntAck signal, it will drive a 32-bit device ID onto the I/O Data Bus. To prevent devices from interfering with the processor, the I/O Data Bus is attached to the Main Bus with a tri-state driver. Create this driver and the bus, and attach the microcontroller’s DrDATA signal to the driver.

4. Modify the datapath so that the PC starts at 0x08 when the processor is reset. Normally the PC starts at 0x00, however we need to make space for the interrupt vector table (IVT). Therefore, when you actually load in the test code that you will write, it needs to start at 0x08. Please make sure that your solution ensures that datapath can never execute from below 0x08 – or in other words, force the PC to drive the value 0x08 if the PC is pointing in the range of the vector table.

5. Create hardware to support selecting the register $k0 within the microcode. This is needed by some interrupt related instructions. Because we need to access $k0 outside of regular instructions, we cannot use the Rx / Ry / Rz bits. HINT: Use only the register selection bits that the main ROM already outputs to select $k0. Notice that there is an unused input to the RegSel multiplexer.

4.2 Adding an External Timer Device

Hardware timers are an essential device in any CPU design. They allow the CPU to monitor the passing of various time intervals, without dedicating CPU instructions to the cause.

The ability of timers to raise interrupts also enables preemptive multitasking, where the operating system periodically interrupts a running process to let another process take a turn. Timers are also essential to ensuring a single misbehaving program cannot freeze up your entire computer.

You will connect an external timer device to the datapath. It is internally configured to have a device ID of 0x0 and interrupt every 2000 clock ticks.

• CLK: The clock input to the device. Make sure you connect this to the same clock as the rest of your circuit.

• INT: The device will begin to assert this line when its time interval has elapsed. It will not be lowered until the cycle after it receives an INTA signal.

• INTA IN: When the INTA IN line is asserted while the device has asserted the INT line, it will drive its device ID to the DATA line and lower its INT line on the next clock cycle.

• INTA OUT: When the INTA IN line is asserted while the device does not have an interrupt pending, its value will be propagated to INTA OUT. This allows for daisy chaining of devices.

• DATA: The device will drive its ID (0x0) to this line after receiving an INTA.

The INT and DATA lines from the timer should be connected to the appropriate buses that you added in the previous section.

4.3 Microcontroller Interrupt Support

Before beginning this part, be sure you have read through Appendix A: LC-22a Instruction Set Architecture and Appendix B: Microcontrol Unit and pay special attention to the new instructions. However, for this part of the project, you do not need to worry about the LdDAR signal or the IN instruction.

In this part of the assignment you will modify the microcontroller and the microcode of the LC-22a to support interrupts. You will need to do the following:

1. Be sure to read the appendix on the microcontroller before starting this section.

2. Modify the microcontroller to support asserting four new signals:

(a) LdEnInt &amp; EnInt to control whether interrupts are enabled/disabled. You will use these 2 signals to control the value of your interrupts enabled register.

(b) IntAck to send an interrupt acknowledge to the device.

(c) DrDATA to drive the value on the I/O Data Bus to the Main Bus.

3. Extend the size of the ROM accordingly.

4. Add the fourth ROM described in Appendix B: Microcontrol Unit to handle onInt.

5. Modify the FETCH macrostate microcode so that we actively check for interrupts. Normally this is done within the INT macrostate (as described in Chapter 4 of the book and in the lectures) but we are rolling this functionality in the FETCH macrostate for the sake of simplicity. You can accomplish this by doing the following:

(a) First check to see if the CPU should be interrupted. To be interrupted, two conditions must be true: (1) interrupts are enabled (i.e., the IE register must hold a ’1’), and (2), a device must be asserting a ’1’ on the INT signal line.

(b) If not, continue with FETCH normally.

(c) If the CPU should be interrupted, then perform the following:

i. Save the current PC to the register $k0.

ii. Disable interrupts.

iii. Assert the interrupt acknowledge signal (IntAck). Next, drive the device ID from the I/O Data Bus and use it to index into the interrupt vector table to retrieve the new PC value. The device will drive its device ID onto the I/O Data Bus one clock cycle after it receives the IntAck signal.

iv. This new PC value should then be loaded into the PC.

Note: onInt works in the same manner that CmpOut did in Project 1. The processor should branch to the appropriate microstate depending on the value of onInt. onInt should be true when interrupts are enabled AND when there is an interrupt to be acknowledged. Note: The mode bit mechanism and user/kernel stack separation discussed in the textbook has been omitted for simplicity.

6. Implement the microcode for three new instructions for supporting interrupts as described in Chapter 4. These are the EI, DI, and RETI instructions. You need to write the microcode in the main ROM controlling the datapath for these three new instructions. Keep in mind that:

(a) EI sets the IE register to 1.

(b) DI sets the IE register to 0.

(c) RETI loads $k0 into the PC, and enables interrupts.

4.4 Implementing the Timer Interrupt Handler

Our datapath and microcontroller now fully support interrupts from devices, BUT we must now implement the interrupt handler t1_handler within the prj2.s file to support interrupts from the timer device while also not interfering with the correct operation of any user programs.

In prj2.s, we provide you with a modified version of pow.s that will run while you are waiting for interrupts. For this part of the project, you need to write the interrupt handler for the timer device (device ID 0x0). You should refer to Chapter 4 of the textbook to see how to write a correct interrupt handler. As detailed in that chapter, your handler will need to do the following:

1. First save the current value of $k0 (the return address where you came from to the current handler) 2. Enable interrupts (which should have been disabled implicitly by the processor within the INT macrostate).

3. Save the state of the interrupted program.

4. Implement the actual work to be done in the handler. In the case of this project, we want you to increment a counter variable in memory, which we have already provided.

5. Restore the state of the original program and return using RETI.

The handler you have written for the timer device should run every time the device’s interrupt is triggered. Make sure to write the handler such that interrupts can be nested. With that in mind, interrupts should be disabled for as few instructions as possible within the handlers.

You will need to do the following:

1. Write the interrupt handler (should follow the above instructions or simply refer to Chapter 4 in your book). In the case of this project, we want the interrupt handler to keep time in memory at the predetermined location: 0xFFFF

2. Load the starting address of the first handler you just implemented in prj2.s into the interrupt vector table at the appropriate addresses (the table is indexed using the device ID of the interrupting device).

Test your design before moving on to the next section. If it works correctly, you should see the value at address 0xFFFF in memory increment as the program runs.

5 Phase 2 – Implementing Interrupts from Input Devices

Figure 2: Interrupt Hardware for the LC-22a with Basic I/O Support

Eager to put your newfound knowledge of device interrupts from CS2200 to good use, you decide to apply what you’ve learned to your engineering passion: toasters. You are interested to know the difference between the highest and lowest temperature of the bread in the toaster.

You’ve rigged up a device that is able to report the current temperature to an LC-22a processor via an interrupt. There’s only one issue: as of right now, your datapath can detect when an external device is ready to interrupt the processor, but it cannot retrieve data from external devices.

In this phase of the project, you will add functionality for device-addressed input. You will then make use of this functionality by adding a device simulating a toaster temperature system and writing a simple handler for the device.

5.1 Basic I/O Support

Before adding the toaster temperature system, you will first need to add support for device addressed I/O. In order to get input from a device such as a toaster temperature system, you will write a value to an Address Bus, which instructs the device with that address (which in this case is the same as the device ID) to write its output data to the I/O Data Bus.

You must do the following:

1. Create the device address register (DAR) and connect its enable to the LdDAR signal from your microcontroller. This register gets its input from the Main Bus, and its output will be directly connected to the Address Bus. It will allow us to assert a value on the Address Bus while using the Main Bus for other operations.

2. Modify the microcontroller to support a new control signal, LdDAR. This signal will be used in order to enable writing to the DAR.

3. Implement the IN instruction in your microcode. This instruction takes a device address an immediate offset (IR[19:0]), loads it into the DAR, and writes the value on the data bus into a register. When it is done, it must clear the DAR (since interrupts use the data bus to communicate device IDs). Examine the format of the IN instruction and consider what signals you might raise in order to write a constant zero into the DAR.

5.2 Adding a toaster temperature system

You will connect a toaster temperature system to your datapath that simulates a toaster temperature system by returning the current toast temperature. Its internals are similar to the timer device, meaning it asserts interrupts and handles acknowledgements in the same way. Every 1000 cycles, it will assert an interrupt signaling that a temperature value has been captured. This temperature can be fetched as a 32-bit word by writing the device’s address to the ADDR line.

The toaster temperature system is internally configured to have a device ID of 0x1.

Place the toaster temperature system in your datapath circuit. This device will share the INT and DATA lines with the timer you added previously. However, it should receive its INTA signal from the INTA OUT pin on the timer device. This ensures that if both the timer and toaster temperature system raise an interrupt at the same time, the timer will be acknowledged first, and the toaster temperature system will be acknowledged after. This is known as “daisy chaining” devices.

5.3 Implementing the Toaster Interrupt Handler

Now that your LC-22a datapath can accept data from your toaster temperature system, we need to decide what to do with the data. In this case, we want to keep track of the maximum and minimum temperatures we have seen so far in two particular memory locations, 0xFFFD and 0xFFFC. You’ll have to implement this logic in your handler, which will work similarly to the one you wrote for the timer device. However, instead of incrementing a timer at a memory location, you will be keeping track of the maximum and minimum temperatures sent from the toaster so far. Then, at the end of the handler you should calculate the difference between the max and min values and save the difference at 0xFFFE.

In addition to the usual overhead of an interrupt handler, your toaster temperature system handler must do the following:

1. Use the IN instruction to obtain the most recently captured temperature value from the toaster temperature system.

2. Write the value obtained from the toaster temperature system to the memory location with the address 0xFFFD only if the value is greater than the current maximum or the address 0xFFFC if the value is less than the current minimum.

3. Save the difference between the max and min value to address 0xFFFE

Make sure that you properly install the location of the new handler into the IVT.

The toaster temperature system hardware is designed to emit a sequence of numbers representing temperature readings. If your design is working properly, you should see the value stored in the memory location 0xFFFD increase and location 0xFFFC decrease after a few thousand clock cycles as it updates when new temperature values are pushed onto the datapath.

To validate you’re updating the temperature max and mins correctly, you can check the values that the toaster temperature system will emit by inspecting the internals of the circuit and checking the values in the ROM labeled ‘Key Buffer’.

6 Deliverables

Please submit all of the following files in a .tar.gz archive generated by one of the following:

• On Windows: Use the provided submit.bat script. Submitting through this method will require 7zip (https://www.7-zip.org/) to be installed on your system. Run submit.bat to automatically package your project into the correct archive format.

• On Mac: Use the provided Makefile. If you haven’t yet installed Command Line Tools, you’ll need to do so. If you have Xcode installed on your machine, you already have Command Line Tools. Otherwise, you can install them by either installing Xcode or installing Command Line Tools standalone from Apple’s developer site. Run make submit to automatically package your project into the correct archive format.

The generated archive should contain at a minimum the following files:

• CircuitSim datapath file (LC-22a.sim)

• Microcode file (microcode.xlsx)

• Assembly code (prj2.s)

Always re-download your assignment from Gradescope after submitting to ensure that all necessary files were properly uploaded. If what we download does not work, you will get a 0 regardless of what is on your machine.

This project will be demoed. In order to receive full credit, you must sign up for a demo slot and complete the demo. We will announce when demo times are released.

7 Appendix A: LC-22a Instruction Set Architecture

The LC-22a is a simple, yet capable computer architecture. The LC-22a combines attributes of both ARM and the LC-2200 ISA defined in the Ramachandran &amp; Leahy textbook for CS 2200.

The LC-22a is a word-addressable, 32-bit computer. All addresses refer to words, i.e. the first word (four bytes) in memory occupies address 0x0, the second word, 0x1, etc.

All memory addresses are truncated to 16 bits on access, discarding the 16 most significant bits if the address was stored in a 32-bit register. This provides 256 KB of addressable memory.

7.1 Registers

The LC-22a has 16 general-purpose registers. While there are no hardware-enforced restraints on the uses of these registers, your code is expected to follow the conventions outlined below.

Table 1: Registers and their Uses

Register Number Name Use Callee Save?

0 $zero Always Zero NA

1 $at Assembler/Target Address NA

2 $v0 Return Value No

3 $a0 Argument 1 No

4 $a1 Argument 2 No

5 $a2 Argument 3 No

6 $t0 Temporary Variable No

7 $t1 Temporary Variable No

8 $t2 Temporary Variable No

9 $s0 Saved Register Yes

10 $s1 Saved Register Yes

11 $s2 Saved Register Yes

12 $k0 Reserved for OS and Traps NA

13 $sp Stack Pointer No

14 $fp Frame Pointer Yes

15 $ra Return Address No

1. Register 0 is always read as zero. Any values written to it are discarded. Note: for the purposes of this project, you must implement the zero register. Regardless of what is written to this register, it should always output zero.

3. Register 2 is where you should store any returned value from a subroutine call.

4. Registers 3 – 5 are used to store function/subroutine arguments. Note: registers 2 through 8 should be placed on the stack if the caller wants to retain those values. These registers are fair game for the callee (subroutine) to trash.

5. Registers 6 – 8 are designated for temporary variables. The caller must save these registers if they want these values to be retained.

7. Register 12 is reserved for handling interrupts. While it should be implemented, it otherwise will not have any special use on this assignment.

8. Register 13 is your anchor on the stack. It keeps track of the top of the activation record for a subroutine.

9. Register 14 is used to point to the first address on the activation record for the currently executing process.

10. Register 15 is used to store the address a subroutine should return to when it is finished executing.

7.2 Instruction Overview

The LC-22a supports a variety of instruction forms, only a few of which we will use for this project. The instructions we will implement in this project are summarized below.

Table 2: LC-22a Instruction Set

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0000 DR SR1 unused SR2

0001 DR SR1 unused SR2

0010 DR SR1 immval20

0011 DR BaseR offset20

0100 SR BaseR offset20

0101 unused offset20

0110 RA AT unused

0111 unused

1000 SR1 SR2 offset20

1001 SR1 SR2 offset20

1010 DR unused PCoffset20

1011 unused

1100 unused

1101 unused

1110 DR 0000 addr20

ADD

NAND

ADDI

LW

SW

BR

JALR

HALT

BLT

BGT

LEA

EI

DI

RETI

IN

7.2.1 Conditional Branching

Branching in the LC-22a ISA is a bit different than usual. We have a set of branching instructions including BR, an unconditional branch, as well as BLT and BGT, which offer the ability to branch upon a certain condition being met. The BLT and BGT instructions use comparison operators, comparing the values of two source registers. If the comparisons are true (for example, with the BGT instruction, if SR1 &gt; SR2), then we will branch to the target destination of incrementedPC + offset20.

Note: The conditional branch instructions make use of the BrSel signal. Think about ways that you can use this signal to implement conditional logic.

7.3 Detailed Instruction Reference

7.3.1 ADD

Assembler Syntax

ADD DR, SR1, SR2

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0000 DR SR1 unused SR2

Operation

DR = SR1 + SR2;

Description

The ADD instruction obtains the first source operand from the SR1 register. The second source operand is obtained from the SR2 register. The second operand is added to the first source operand, and the result is stored in DR.

7.3.2 NAND

Assembler Syntax

NAND DR, SR1, SR2

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0001 DR SR1 unused SR2

Operation

DR = ~(SR1 &amp; SR2);

Description

The NAND instruction performs a logical NAND (AND NOT) on the source operands obtained from SR1 and SR2. The result is stored in DR.

HINT: A logical NOT can be achieved by performing a NAND with both source operands the same.

For instance,

NAND DR, SR1, SR1

…achieves the following logical operation: DR←SR1.

7.3.3 ADDI

Assembler Syntax

ADDI DR, SR1, immval20

Encoding

0010 DR SR1 immval20

Operation

DR = SR1 + SEXT(immval20);

Description

The ADDI instruction obtains the first source operand from the SR1 register. The second source operand is obtained by sign-extending the immval20 field to 32 bits. The resulting operand is added to the first source operand, and the result is stored in DR.

7.3.4 LW

Assembler Syntax

LW DR, offset20(BaseR)

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0011 DR BaseR offset20

Operation

DR = MEM[BaseR + SEXT(offset20)];

Description

An address is computed by sign-extending bits [19:0] to 32 bits and then adding this result to the contents of the register specified by bits [23:20]. The 32-bit word at this address is loaded into DR.

7.3.5 SW

Assembler Syntax

SW SR, offset20(BaseR)

Encoding

0100 SR BaseR offset20

Operation

MEM[BaseR + SEXT(offset20)] = SR;

Description

An address is computed by sign-extending bits [19:0] to 32 bits and then adding this result to the contents of the register specified by bits [23:20]. The 32-bit word obtained from register SR is then stored at this address.

7.3.6 BR

Assembler Syntax

BR offset20

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0101 unused offset20

Operation

PC = incrementedPC + offset20

Description

A branch is unconditionally taken. The PC will be set to the sum of the incremented PC (since we have already undergone fetch) and the sign-extended offset[19:0].

7.3.7 JALR

Assembler Syntax

JALR RA, AT

Encoding

0110 RA AT unused

Operation

RA = PC;

PC = AT;

Description

First, the incremented PC (address of the instruction + 1) is stored into register RA. Next, the PC is loaded with the value of register AT, and the computer resumes execution at the new PC.

7.3.8 HALT

Assembler Syntax

HALT

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

0111 unused

Description

The machine is brought to a halt and executes no further instructions.

7.3.9 BLT

Assembler Syntax

BLT SR1, SR2, offset20

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1000 SR1 SR2 offset20

Operation

if (SR1 &lt; SR2) {

PC = incrementedPC + offset20

}

Description

A branch is taken if SR1 is less than SR2. If this is the case, the PC will be set to the sum of the incremented PC (since we have already undergone fetch) and the sign-extended offset[19:0].

7.3.10 BGT

Assembler Syntax

BGT SR1, SR2, offset20

Encoding

1001 SR1 SR2 offset20

Operation

if (SR1 &gt; SR2) {

PC = incrementedPC + offset20

}

Description

A branch is taken if SR1 is greater than SR2. If this is the case, the PC will be set to the sum of the incremented PC (since we have already undergone fetch) and the sign-extended offset[19:0].

7.3.11 LEA

Assembler Syntax

LEA DR, label

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1010 DR unused PCoffset20

Operation

DR = PC + SEXT(PCoffset20);

Description

An address is computed by sign-extending bits [19:0] to 32 bits and adding this result to the incremented PC (address of instruction + 1). It then stores the computed address into register DR.

7.3.12 EI

Assembler Syntax

EI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1011 unused

Operation

IE = 1;

Description

The Interrupts Enabled register is set to 1, enabling interrupts.

7.3.13 DI

Assembler Syntax

DI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1100 unused

Operation

IE = 0;

Description

The Interrupts Enabled register is set to 0, disabling interrupts.

7.3.14 RETI

Assembler Syntax

RETI

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1101 unused

Operation

PC = $k0;

IE = 1;

Description

The PC is restored to the return address stored in $k0. The Interrupts Enabled register is set to 1, enabling interrupts.

7.3.15 IN

Assembler Syntax

IN DR, DeviceADDR

Encoding

31302928272625242322212019181716151413121110 9 8 7 6 5 4 3 2 1 0

1110 DR 0000 addr20

Operation

DAR = addr20;

DR = DeviceData;

DAR = 0;

Description

The value in addr20 is sign-extended to determine the 32-bit device address. This address is then loaded into the Device Address Register (DAR). The processor then reads a single word value off the device data bus, and writes this value to the DR register. The DAR is then reset to zero, ending the device bus cycle.

8 Appendix B: Microcontrol Unit

Figure 3: Three ROM Microcontrol Unit

The outputs of the FSM control which signals on the datapath are raised (asserted). Here is more detail about the meaning of the output bits for the microcontroller:

Table 3: ROM Output Signals

Bit Purpose Bit Purpose Bit Purpose Bit Purpose Bit Purpose

0 NextState[0] 7 DrMEM 14 LdA 21 ALULo 28 IntAck

1 NextState[1] 8 DrALU 15 LdB 22 ALUHi 29 DrData

2 NextState[2] 9 DrPC 16 LdCmp 23 OPTest 30 LdDAR

3 NextState[3] 10 DrOFF 17 WrREG 24 ChkCmp

4 NextState[4] 11 LdPC 18 WrMEM 25 BrSel

5 NextState[5] 12 LdIR 19 RegSelLo 26 LdEnInt

6 DrREG 13 LdMAR 20 RegSelHi 27 EnInt

Table 4: Register Selection Map

RegSelHi RegSelLo Register

0 0 RX (IR[27:24])

0 1 RY (IR[23:20])

1 0 RZ (IR[3:0])

1 1 $k0 (1100)

Table 5: ALU Function Map

ALUHi ALUlLo Function

0 0 ADD

0 1 SUB

1 0 NAND

1 1 A + 1

9 Appendix C: Pull Down and Pull Up Resistors

9.1 Intro

In CS 2200 and CS 2110, you’ve built functional logic gates that don’t need to consider the physical variables of real circuit logic. There is another way that only needs half the number of transistors. This method works best with discrete components (but our two-transistor style is better with integrated circuits as the transistors takes less chip space overall).

9.2 How we build our logic gates

We build our gates so that the output is either connected to Vcc or Ground depending on the calculated output value. What we could do is build the gate so that the output is connected to one side of the power bus (either Vcc or Ground) when the output should be that value. When the output is the opposite value, we leave the output floating. This by itself would give us an unpredictable output value, but not if we connect a small resistor (known as a pull-up or pull down resistor depending on whether it is connected to Vcc or Ground, respectively) between the gate’s output line and the opposite side of the power bus.

See http://www.cs.unca.edu/brock/classes/Fall2012/csci255/labs/lab05.html for a more thorough explanation of the different methods for building gates.

9.3 Why are we telling you this?

Because the INT line is one of the very few situations that we can’t handle with our two-transistor logic style. We need to combine several different signals on the INT line (which are connected by tri-state buffers) that are either 1 or floating (we can’t allow devices to assert a 0 on the INT line because it will cause a short circuit when one of our devices asserts a 1 signal to signal an interrupt).

The way we would handle this in a real circuit would be to simply add a pull-down resistor from the INT line to Ground so that if none of the tri- state buffers are open to assert an interrupt 1 signal, the INT line will reliably read as 0. The immediate issue is that CircuitSim doesn’t understand pull-up and pulldown resistors, so it instead has a reality-distorting ”feature” that allows us to implement the interrupt line without pull-down resistors. The feature is this: A CircuitSim OR gate will consider a floating input line to be a 0.

This is not guaranteed in real life, but it is in CircuitSim. To implement the INT line, you can connect a signal line that is either 1 or floating to one side of an OR gate and connect a 0 to the other input. The output of the OR gate will be 1 if the first input is 1. If the first input is floating (or 0), the output will definitely be 0. The diagram below shows an implementation of the INT line circuit for 3 devices:
