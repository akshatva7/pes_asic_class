# VLSI Physical Design for ASICs

## Objective

The objective of VLSI physical design for ASICs is to convert a logical RTL design into a physical layout suitable for fabrication. This process ensures the circuit's functionality aligns with design constraints, performance goals, and manufacturing standards.

## Skill Outcomes

Participants in this course will gain expertise in the following areas:

- **Architectural Design**: Understanding the overall structure and organization of integrated circuits.
- **RTL Design / Behavioral Modeling**: Creating a Register Transfer Level (RTL) description of a digital circuit's behavior.
- **Floorplanning**: The initial phase of physical design where the locations of major components are planned.
- **Placement**: Determining the precise locations of cells or modules on the chip.
- **Clock Tree Synthesis**: Building a clock distribution network to ensure synchronous operation.
- **Routing**: Establishing interconnections between different parts of the design.



## Installation

To get started with the VLSI Physical Design for ASICs workshop, follow these steps:

1. Download the `run.sh` script from the [GitHub repository](https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh).

2. Open a terminal on your system.

3. Navigate to the directory where you downloaded the `run.sh` script. For example, if it's in your Downloads folder, use the following command:

    ```sh
    cd Downloads
    ```

4. Execute the script by running the following command:

    ```sh
    ./run.sh
    ```

This will initiate the installation process and set up the necessary environment for the workshop.



# Table of Contents

## DAY 1
  
## Introduction to RISC-V ISA and GNU Compiler Toolchain

### Introduction to Basic Keywords
- Introduction
- From Apps to Hardware
- Detail Description of Course Content

### Labwork for RISC-V Toolchain
- C Program
- RISC-V GCC Compiler and Disassemble
- Spike Simulation and Debug

### Integer Number Representation
- 64-bit Unsigned Numbers
- 64-bit Signed Numbers
- Labwork For Signed and Unsigned Numbers

## DAY 2

## Introduction to ABI and Basic Verification Flow

### Application Binary Interface
- Introduction to ABI
- Memory Allocation for Double Words
- Load, Add and Store Instructions
- 32-Registers and their ABI Names

### Labwork using ABI Function Calls
- Algorithm for C Program using ASM
- Review ASM Function Calls
- Simulate C Program using Function Call

## DAY 3
### Introduction to Verilog RTL design and Synthesis
- Introduction to Open-Source Simulator iVerilog
	- Introduction to iVerilog Design Testbench
  
- Labs using iVerilog and GTKwave
	- Introduction to Lab
	- iVerilog GTKwave Part-1
	- iVerilog GTKwave Part-2

- Introduction to Yosys and Logic synthesis
	- Introduction to Yosys
	- Introduction to Logic Synthesis

- Labs using Yosys and Sky130 PDKs
	- Yosys good mux

## DAY 4

### Timing Libs, Hierarchical vs Flat Synthesis and Efficient Flop Coding Styles

- Introduction to Timing Dot Libs
  	- Introduction to Dot Lib

- Hierarchical vs Flat Synthesis
	- Hierarchical Synthesis Flat Synthesis

- Various Flop Coding Styles and Optimization
	- Why Flops and Flop Coding Styles
	- Lab Flop Synthesis Simulations
	- Interesting Optimisations

## DAY 5

### Combinational and Sequential Optmizations

- Introduction to Optimisations
- Combinational Logic Optimisations
- Sequential Logic Optimisations
- Sequential Optimisations for Unused Outputs

## DAY 6

### GLS, Blocking vs Non-Blocking and Synthesis-Simulation Mismatch

- GLS Synthesis-Simulation Mismatch and Blocking Non-Blocking Statements

- GLS Concepts And Flow Using Iverilog
	- Synthesis Simulation Mismatch
	- Blocking And Non Blocking Statements In Verilog
	- Caveats With Blocking Statements


- Labs on GLS and Synthesis-Simulation Mismatch
- Labs on Synth-Sim Mismatch for Blocking Statement

# DAY 1
# Introduction to Basic Keywords
<details>
<summary>Introduction</summary>
<br>

## ISA (Instruction Set Architecture)

ISA defines the interface between a computer's hardware and its software, specifically how the processor and its components interact with the software instructions that drive the execution of tasks. It encompasses a set of instructions, addressing modes, data types, registers, memory organization, and the mechanisms for executing and managing instructions.

## [RISC-V (Reduced Instruction Set Computing - Five)](https://www.riscv.org/)

RISC-V is an open-source Instruction Set Architecture (ISA) that has gained significant attention and adoption in the world of computer architecture and semiconductor design. RISC architectures simplify the instruction set by focusing on a smaller set of instructions, each of which can be executed in a single clock cycle. This approach usually leads to faster execution of individual instructions.
</details>

<details>
<summary>From Apps to Hardware</summary>
<br>

- **Apps**: Application software, often referred to simply as "applications" or "apps," is a type of computer software that is designed to perform specific tasks or functions for end-users.

- **System software**: System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs. System software plays a critical role in maintaining the overall functionality, security, and performance of a computer system.

- **Operating System**: The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction. Examples of operating systems include Microsoft Windows, macOS, Linux, and Android.

- **Compiler**: A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.

- **Assembler**: An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.

- **RTL**: RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.

- **Hardware**: Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.
</details>

<details>
<summary>Detail Description of Course Content</summary>
<br>

### Pseudo Instructions

Pseudo-instructions are used to simplify programming, improve code readability, and reduce the number of explicit instructions a programmer needs to write. They are especially useful for common programming patterns that involve multiple instructions. Ex: li, mv.

### Base Integer Instructions

The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations. Ex: add, sub, and, or, xor, sll.

### Multiply Extension Instructions

The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations. Ex: mul, mulh, mulhu, mulhsu.

### Single and Double Precision Floating Point Extension

The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.

### Application Binary Interface (ABI)

ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.

### Memory Allocation and Stack Pointer

Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks. The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack.
</details>



# Labwork for RISCV Toolchain

<details>
<summary>C Program</summary>
<br>

We wrote a C program ```p1.c```for calculating the Sum from 1 to n using a text editor, `gedit`.

```c
#include<stdio.h>

int main(){
	int i, sum=0, n=111;
	for (i=1;i<=n; ++i) {
	sum +=i;
	}
	printf("Sum of numbers from 1 to %d is %d \n",n,sum);
	return 0;
}
```
Using the gcc compiler, we compiled the program to get the output.
```
gcc p1.c
./a.out
```

![1](https://github.com/akshatva7/pes_asic_class/assets/135726741/753b4fde-d1c4-4b9c-b256-6dc3f0ef9fa7)


# RISCV GCC Compiler and Disassemble

Using the RISC-V GCC compiler, we compiled the C program.
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o p1.o p1.c
```
Using ```ls -ltr p1.c``` we can check that the object file is created.
![2](https://github.com/akshatva7/pes_asic_class/assets/135726741/e42a34de-c687-4a3e-855d-43e84ecd6e57)

To get the dissembled ALP code for the C program,

```riscv64-unknown-elf-objdump -d p1.o | less ```

In order to view the main section, type ```/main```
![4](https://github.com/akshatva7/pes_asic_class/assets/135726741/44b0cbfb-5d8c-4af7-ba8e-ea229a312bef)


Here, since we used -O1 optimisation, the number of instructions are 26.

![Screenshot from 2023-08-20 22-34-30](https://github.com/akshatva7/pes_asic_class/assets/135726741/684258c6-c347-465c-8804-eef593c15d45)


When we use -Ofast optimisation, we can see that the number of instructions have been reduced to 12.

Onumber: level of optimization required
mabi: specifies the ABI (Application Binary Interface) to be used during code generation according to the requirements
march: specifies the target architecture

In order to view the different options available for these fields, use the following commands:

Go to the directory where riscv64-unknown-elf is present.

* O1:``` riscv64-unknown-elf --help=optimizer```
* mabi: ```riscv64-unknown-elf-gcc --target-help```
* march: ```riscv64-unknown-elf-gcc --target-help```

For different instances,

Use the command ```riscv64-unknown-elf-objdump -d p1.o | less```
Use ```/instance``` to search for an instance
Press ENTER
Press ```n``` to search for the next occurrence
Press ```N``` to search for the previous occurrence.
Use esc ```:q``` to quit

</details>

<details>
<summary> Spike Simulation and Debug </summary>
<br>

```spike pk p1.o ```is used to check whether the instructions produced are right to give the correct output.

```spike -d pk p1.c``` is used for debugging.

The contents of the registers can also be viewed.

Press ENTER : to show the first line and successive ENTER to show successive lines
reg 0 a2 : to check content of register a2 0th core
q : to quit the debug process

</details>

# Integer Number Representation

<details>
<summary>Unsigned Numbers</summary>
<br>
	
* Unsigned numbers, also known as non-negative numbers, are numerical values that represent magnitudes without indicating direction or sign.
* Range: [0, (2^n)-1 ]
</details>

<details>
<summary>Signed Numbers</summary>
<br>

* Signed numbers are numerical values that can represent both positive and negative magnitudes, along with zero.
* Range : Positive : [0 , 2^(n-1)-1] Negative : [-1 to 2^(n-1)]
</details>

<details>
<summary>Labwork</summary>
<br>

We wrote a C program ```p2.c```that shows the maximum and minimum values of 64bit Signed numbers.

```c
#include <stdio.h>
#include <math.h>

int main(){
	long long int max = (long long int) (pow(2,63) -1);
	long long int min = (long long int) (pow(2,63) *(-1));
	printf("lowest number represented by signed 64-bit integer is %lld\n",min);
	printf("highest number represented by signed 64-bit integer is %lld\n",max);
	return 0;
}
```
![6](https://github.com/akshatva7/pes_asic_class/assets/135726741/6a85ec2f-b6a4-4ea8-af39-ca292370fde1)

We wrote a C program ```p3.c```that shows the maximum and minimum values of 64bit Unsigned numbers.

```c
#include <stdio.h>
#include <math.h>

int main(){
	unsigned long long int max = (unsigned long long int) (pow(2,64) -1);
	unsigned long long int min = (unsigned long long int) (pow(2,64) *(-1));
	printf("lowest number represented by unsigned 64-bit integer is %llu\n",min);
	printf("highest number represented by unsigned 64-bit integer is %llu\n",max);
	return 0;
}
```
![7](https://github.com/akshatva7/pes_asic_class/assets/135726741/6f1ea5b2-49dd-4afc-b1d9-80516056f9a8)

</details>

# DAY 2

# Application Binary Interface

<details>
<summary>Introduction to ABI</summary>
<br>

An Application Binary Interface (ABI) is a set of rules and conventions that dictate how binary code interacts with and communicates with other binary code, typically at the level of machine code or compiled code. In simpler terms, it defines the interface between two software components or systems that are written in different programming languages, compiled by different compilers, or running on different hardware architectures.
The ABI is crucial for enabling interoperability between different software components, such as different libraries, object files, or even entire programs. It allows components compiled independently and potentially on different platforms to work seamlessly together by adhering to a common set of rules for communication and data representation.
</details>


<details>
<summary>Memmory Allocation for Double Words</summary>
<br>

64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly

* Little-Endian: In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.
* Big-Endian: In big-endian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.
</details>

<details>
<summary>Load, Add and Store Instructions</summary>
<br>

Load, Add, and Store instructions are fundamental operations in computer architecture and assembly programming. They are often used to manipulate data within a computer's memory and registers.

Load Instructions**: Load instructions are used to transfer data from memory to registers. They allow you to fetch data from a specified memory address and place it into a register for further processing.

Example ```ld x6, 8(x5)```

In this Example

* ```ld``` is the load double-word instruction.
* ```x6``` is the destination register.
* ```8(x5)``` is the memory address pointed to by register ```x5``` (base address + offset).

Store Instructions: Store instructions are used to write data from registers into memory.They store values from registers into memory addresses

Example ```sd x8, 8(x9)```

In this Example

* ```sd``` is the store double-word instruction.
* ```x8``` is the source register.
* ```8(x9)``` is the memory address pointed to by register ```x9``` (base address + offset).

Add Instructions: Add instructions are used to perform addition operations on registers. They add the values of two source registers and store the result in a destination register.

Example ```add x9, x10, x11```

In this Example

* ```add``` is the add instruction.
* ```x9``` is the destination register.
* ```x10``` and ```x11``` are the source registers.

</details>
	
<details>
<summary>32-Registers and their ABI Names</summary>
<br>

The choice of the number of registers in a processor's architecture, such as the RISC-V RV64 architecture with its 32 general-purpose registers, involves a trade-off between various factors. While modern processors can have more registers but increasing the number of registers could lead to larger instructions, which would take up more memory and potentially slow down instruction fetch and decode.

## ABI Names

ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components.

![9](https://github.com/akshatva7/pes_asic_class/assets/135726741/0cf843d9-8f69-41a5-ac00-fd92d6f0928d)

</details>

# Labwork using ABI Function Calls

<details>
<summary>Algorithm for C Program using ASM</summary>
<br>

Incorporating assembly language code into a C program can be done using inline assembly or by linking separate assembly files with your C code.

When you call an assembly function from your C code, the C calling convention is followed, including pushing arguments onto the stack or passing them in registers as required.

The program executes the assembly function, following the assembly instructions you've provided.

</details>

<details>
<summary>Review ASM Function Calls</summary>
<br>

We wrote C code in one file and your assembly code in a separate file.
In the assembly file, we declared assembly functions with appropriate signatures that match the calling conventions of your platform.

### C Program - Sum of numbers from 1 to 9
```p4.c```
```c
#include <stdio.h>

extern int load(int x, int y);

int main()
{
  int result = 0;
  int count = 9;
  result = load(0x0, count+1);
  printf("Sum of numbers from 1 to 9 is %d\n", result);
}
```
### Assembly File 
```load.s```

```s
.section .text
.global load
.type load, @function

load:

add a4, a0, zero
add a2, a0, a1
add a3, a0, zero

loop:

add a4, a3, a4
addi a3, a3, 1
blt a3, a2, loop
add a0, a4, zero
ret
```
</details>


<details>
<summary>Simulate C Program using Function Call</summary>
<br>

**Compilation:** To compile C code and Asseembly file use the command

```riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o p3.o p3.c load.s```

this would generate object file ```p3.o```

**Execution:** To execute the object file run the command

```spike pk p3.o```

![8](https://github.com/akshatva7/pes_asic_class/assets/135726741/55f2d630-e640-4633-81ae-4d4a14218977)

![Screenshot from 2023-08-20 22-01-13](https://github.com/akshatva7/pes_asic_class/assets/135726741/d20630e3-9bf5-4f96-a916-31655534aa09)

![Screenshot from 2023-08-20 22-01-35](https://github.com/akshatva7/pes_asic_class/assets/135726741/8861a8bc-256d-47da-93b4-7492a3a5a1ed)

</details>

# Day 3

## Introduction to Open-Source Simulator iVerilog

<details>
<summary>Introduction to iVerilog Design Testbench </summary>
<br>

- **Simulator**
	- It is a tool used for simulating the design. It looks for the changes on the input signals to evaluate the outputs.
	- If there is no change in the inputs, the simulator doesn't evaluate the outputs.
	- RTL is checked for adherence to the spec by simulating the design.
	- The tool used here is iverilog.
- **iVerilog**
  	- It is an open-source Verilog simulator used for testing and simulating digital circuit designs described in the Verilog hardware description language (HDL).
	- Both the design and the testbench are fed to the simulator and it produces a vcd (value change dump) file.
   	- In order to view the vcd file, we use the GTKwave where we can see the wave forms.
 
   	- 
<img align="right" src="https://github.com/akshatva7/pes_asic_class/assets/135726741/90619323-cca4-458a-b1df-8b9597a4312d">


- **Design**
	- It is the actual verilog code or set of verilog codes which ahs the intended functionality to meet with the required specifications.
	- Verilog is used to describe the behavior and structure of digital circuits at different levels of abstraction, from high-level system descriptions down to low-level gate-level representations.

- **Testbench**
  
	- A testbench is a specialized Verilog module or program used to verify the functionality and behavior of another Verilog module, circuit, or design. Testbenches are essential for testing and simulating digital designs before they are synthesized or manufactured as physical chips.
	- It is a setup to apply stimulus to the design to check its functionality.

<img align="right" src="https://github.com/akshatva7/pes_asic_class/assets/135726741/8e307f40-bb60-4342-a076-13c378e6f5f7">
</details>

## Labs using iVerilog and GTKwave

<details>
<summary>Introduction to Lab </summary>
<br>

- Make a directory named vsd ```mkdir vsd```
- ```cd vsd```
- ```git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git```
- Creates a folder called ```sky130RTLDesignAndSynthesisWorkshop``` in the vsd directory.
	- my_lib : contains all the library files
	- lib : contains sky130 standard cell library used for our synthesis
	- verilog_model : contains all the standard cell verilog modules of the standard cells contained in the .lib 
	- verilog_files : contains all the verilog source files and testbench files which are required for labs

</details>

<details>
<summary> iVerilog GTKwave Part-1  </summary>
<br>
	
- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
- We have loaded the source code along with the testbench code into the iverilog simulator
- ```iverilog good_mux.v tb_good_mux.v```
- We can see that an output file ```a.out``` has been created.
- ```./a.out``` To execute it
- The output of the iverilog, a vcd file,  is created which is loaded into the simualtor gtkwave.
- ```gtkwave tb_good_mux.vcd```

2 pictures to be added

</details>
	
<details>
<summary> iVerilog GTKwave Part-2  </summary>
<br>

- In order to view the contents in the files,
- ```gvim tb_good_mux.v -o good_mux.v```
  
</details>

## Introduction to Yosys and Logic Synthesis
	
<details>
<summary>  Introduction to Yosys </summary>
<br>
	
 - **Synthesizer**
	- It is a tool used for converting RTL design code to netlist.
	- Here, the synthesizer used is Yosys.
- **Yosys**
	- It is an open-source framework for Verilog RTL synthesis and formal verification.
	- Yosys provides a collection of tools and algorithms that enable designers to transform high-level RTL (Register Transfer Level) descriptions of digital circuits into optimized gate-level representations suitable for physical implementation on hardware.
 - Design and .lib files are fed to the synthesizer to get a netlist file.
 - **Netlist** is the representation of the design in the form of standard cells in the .lib
 - Commands used to perform different opertions:
 	- ```read_verilog``` to read the design
  	- ```read_liberty``` to read the .lib file
   	- write_verilog to write out the netlist file
   	  
- To verify the synthesis
- Netlist along with the tesbench is fed to the iverilog simulator.
- The vcd file generated is fed to the gtkwave simulator.
- The output on the simulator must be same as the output observed during RTL simulation.
- Same RTL testbench can be used as the primary inputs and primary outputs remain same between the RTL design and synthesised netlist.

</details>

<details>
<summary>  Introduction to Logic Synthesis  </summary>
<br>
	
- Logic Synthesis
	- Logic synthesis is a process in digital design that transforms a high-level hardware description of a digital circuit, typically in a hardware description language (HDL) like verilog or VHDL, into a lower-level representation composed of logic gates and flip-flops.
	- The goal of logic synthesis is to optimize the design for various criteria such as performance, area, power consumption, and timing.
- .lib
	- It is a collection of logical modules like And, Or, Not etc.
	- It has different flavors of same gate like 2 input AND gate, 3 input AND gate etc with different performace speed.
- Why different flavors  of gate?
	- In order to make a circuit faster, the clock frequency should be high.
	- For that, the time period of the clock should be as low as possible.
- In a sequential circuit, clock period depends on:	
	- Clock to Q of flip-flop A.
	- Propagation delay of combinational circuit.
	- Setup time of flip-flop B.

- Why need fast and slow cells?
	- To ensure that there are no HOLD issues at flip-flop B, we require slow cells.
	- For a smaller propagation time, we need faster cells.
	- The collection forms the .lib

- Faster Cells vs Slower Cells

	- Load in digital circuit is of Capacitence.
	- Faster the charging or dicharging of capacitance, lesser is the cell delay.
	- However, for a quick charge/ discharge of capacitor, we need transistors capable of sourcing more current i.e, we need wide transistors.
	- Wider transistors have lesser delay but consume more area and power.
	- Narrow transistors have more delay but consume less area and performance.
	- Faster cells come with a cost of area and power.

- Selection of the Cells
  	- We have to guide the Synthesizer to choose the flavour of cells that is optimum for implementation of logic circuit.
  	- More use of faster cells leads to bad circuit in terms of power and area and also hold time violations.
  	- More use of slower cells leads to sluggish circuits amd may not meet the performance needs.
  	- Hence the guidance is offered to the synthesiser in the form of constraints.
  	  
</details>

## Labs using Yosys and Sky130 PDKs
<details>
<summary>   Yosys good_mux  </summary>
<br>
	
- To invoke **yosys**
- ```cd```
- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
- Type ```yosys```
- To read the library
 ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- To read the design
```read_verilog good_mux.v```
- To syntheis the module
``` synth -top good_mux```
- To generate the netlist
```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```

It gives a report of what cells are used and the number of input and output signals.
- To see the logic realised
```show```

The mux is completely realised in the form of sky130 library cells.

- To write the netlist
	- ```Write_verilog good_mux_netlist.v```
	- ```!gvim good_mux_netlist.v```
- To view a simplified code
  - ```write_verilog -noattr good_mux_netlist.v```
  - ```!gvim good_mux_netlist.v```

</details>


