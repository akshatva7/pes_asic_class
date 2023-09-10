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

<img align="right" src="https://github.com/akshatva7/pes_asic_class/assets/135726741/dab7b772-c655-4bed-b5d6-76a3ceef1c1c">

<img align="right" src="https://github.com/akshatva7/pes_asic_class/assets/135726741/9a084202-508c-4cc9-8919-3f245b8f7e08">

</details>
	
<details>
<summary> iVerilog GTKwave Part-2  </summary>
<br>

- In order to view the contents in the files,
- ```gvim tb_good_mux.v -o good_mux.v```

<img align="right" src="https://github.com/akshatva7/pes_asic_class/assets/135726741/9ad0b2e4-23ae-4897-9919-e2651fe2c4f9">
  
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
![Screenshot from 2023-09-03 22-39-53](https://github.com/akshatva7/pes_asic_class/assets/135726741/1d17be0d-3819-48be-bbb0-0479471af78d)


 - Design and .lib files are fed to the synthesizer to get a netlist file.
 - **Netlist** is the representation of the design in the form of standard cells in the .lib
 - Commands used to perform different opertions:
 	- ```read_verilog``` to read the design
  	- ```read_liberty``` to read the .lib file
   	- write_verilog to write out the netlist file
   	  
- To verify the synthesis
![Screenshot from 2023-09-03 22-40-05](https://github.com/akshatva7/pes_asic_class/assets/135726741/228ddac5-78f2-4d05-96aa-1aa885e7bc92)

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
![Screenshot from 2023-09-03 22-40-20](https://github.com/akshatva7/pes_asic_class/assets/135726741/8b764103-c7aa-4a49-aeff-b51c327f0aa9)

- In a sequential circuit, clock period depends on:	
	- Clock to Q of flip-flop A.
	- Propagation delay of combinational circuit.
	- Setup time of flip-flop B.
 - 
![Screenshot from 2023-09-03 22-43-29](https://github.com/akshatva7/pes_asic_class/assets/135726741/5719ecaf-2b5c-4bd3-b137-28c0822a744c)

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
![Screenshot from 2023-09-03 22-50-37](https://github.com/akshatva7/pes_asic_class/assets/135726741/98c24bea-0558-416c-b725-8efaa1e13aa2)


- To read the library
 ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- To read the design
```read_verilog good_mux.v```
- To syntheis the module
``` synth -top good_mux```
![Screenshot from 2023-09-03 22-54-32](https://github.com/akshatva7/pes_asic_class/assets/135726741/28461c0e-377b-4e77-b236-d70a088e2ad9)
![Screenshot from 2023-09-03 23-05-58](https://github.com/akshatva7/pes_asic_class/assets/135726741/f49a801a-4904-4728-895d-65d7422de924)


- To generate the netlist
```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
![Screenshot from 2023-09-03 23-08-00](https://github.com/akshatva7/pes_asic_class/assets/135726741/10d301a6-7f1c-4755-bb5f-4bc6dae8d46e)

It gives a report of what cells are used and the number of input and output signals.
- To see the logic realised
```show```
![Screenshot from 2023-09-03 23-10-40](https://github.com/akshatva7/pes_asic_class/assets/135726741/5c0c8f35-c912-4c29-97e8-8b32cba8c304)

The mux is completely realised in the form of sky130 library cells.

- To write the netlist
	- ```Write_verilog good_mux_netlist.v```
	- ```!gvim good_mux_netlist.v```
- To view a simplified code
  - ```write_verilog -noattr good_mux_netlist.v```
  - ```!gvim good_mux_netlist.v```

![Screenshot from 2023-09-03 23-12-37](https://github.com/akshatva7/pes_asic_class/assets/135726741/50afb721-8c94-406a-a7fb-be11307c9f78)

</details>

# Day 4

## Introduction to Timing Dot Libs

<details>
<summary>  Introduction to Dot Lib  </summary>
<br>


- To view the contents in the .lib
```gvim ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```

![Screenshot from 2023-09-03 23-31-59](https://github.com/akshatva7/pes_asic_class/assets/135726741/09dcbef0-8d7e-4d0b-a55b-ace0702ab8c0)

	- The first line in the file ```library ("sky130_fd_sc_hd__tt_025C_1v80")```  :
		- tt : indicates variations due to process and here it indicates Typical Process.
		- 025C : indicates the variations due to temperatures where the silicon will be used.
		- 1v80 : indicates the variations due to the voltage levels where the silicon will be incorporated.
- It also displays the units of various parameters.
- It gives the features of the cells
- To enable line number ```:se nu```
- To view all the cells ```:g//```
- To view any instance ```:/instance```
- Since there are 5 inputs, for all the 32 possible combinations, it gives the delay, power and all the other parameters for
 each cell.
- The below image shows the power consumption and area comparision.

</details>

## Hierarchical vs Flat Synthesis
<details>
<summary> Hierarchical Synthesis Flat Synthesis  </summary>
<br>
	
**Hierarchical synthesis** is an approach in digital design and logic synthesis where complex designs are broken down into smaller, more manageable modules or sub-circuits, and each module is synthesized individually. These synthesized modules are then integrated back into the overall design hierarchy. This approach helps manage the complexity of large designs and allows designers to work on different parts of the design independently.

- The file we used in this lab is ```multiple_modules.v```
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```gvim multiple_modules.v```
- ```multiple_modules``` instantiates ```sub_module1``` and ```sub_module2```
- Launch ```yosys```
- Read the library file  ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- Read the verilog file  ```read_verilog multiple_modules.v```
- ```synth -top multiple_modules``` to set it as top module
- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- To view the netlist ```show multiple_modules```
- Here it shows ```sub_module1``` and ```sub_module2``` instead of AND gate and OR gate.
- ```write_verilog -noattr multiple_modules_hier.v```
- ```!gvim multiple_modules_hier.v```

**Flattened Synthesis**

It is the opposite of hierarchical synthesis. Instead of maintaining the hierarchical structure of the design during synthesis, flattened synthesis combines all modules and sub-modules into a single, flat representation. This means that the entire design is synthesized as a single unit, without preserving the modular organization present in the original high-level description.

- Launch ```yosys```
- read the library file ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- read the verilog file ```read_verilog multiple_modules.v```
- ```synth -top multiple_modules``` to set it as top module
- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- ```flatten``` to write out a flattened netlist
- ```show```
- ```write_verilog -noattr multiple_modules_flat.v```
- ```!gvim multiple_modules_flat.v```
  
</details>


## Various Flop Coding Styles and Optimization

<details>
<summary> Why Flops and Flop Coding Styles </summary>
<br>
	
**Why do we need a Flop?**

- A flip-flop (often abbreviated as "flop") is a fundamental building block in digital circuit design.
- It's a type of sequential logic element that stores binary information (0 or 1) and can change its output based on clock signals and input values.
- In a combinational circuit, the output changes after the propagation delay of the circuit once inputs are changed.
- During the propagation of data, if there are different paths with different propagation delays, then a glitch might occur.
- There will be multiple glitches for multiple combinational circuits.
- Hence, we need flops to store the data from the combinational circuits.
- When a flop is used, the output of combinational circuit is stored in it and it is propagated only at the posedge or negedge of the clock so that the next combinational circuit gets a glitch free input thereby stabilising the output.
- We use control pins like set and reset to initialise the flops.
- They can be synchronous and asynchronous.

**D Flip-Flop with Asynchronous Reset**

- When the reset is high, the output of the flip-flop is forced to 0, irrespective of the clock signal.
- Else, on the positive edge of the clock, the stored value is updated at the output.
```gvim dff_asyncres_syncres.v```

**D Flip-Flop with Asynchronous Set**

- When the set is high, the output of the flip-flop is forced to 1, irrespective of the clock signal.
- Else, on positive edge of the clock, the stored value is updated at the output.
```gvim dff_async_set.v```

**D Flip_Flop with Synchronous Reset**

When the reset is high on the positive edge of the clock, the output of the flip-flop is forced to 0.

Else, on the positive edge of the clock, the stored value is updated at the output.

```gvim dff_syncres.v```

**D Flip-Flop with Asynchronous Reset and Synchronous Reset**
- When the asynchronous resest is high, the output is forced to 0.
- When the synchronous reset is high at the positive edge of the clock, the output is forced to 0.
- Else, on the positive edge of the clock, the stored value is updated at the output.
- Here, it is a combination of both synchronous and asynchronous reset DFF.
```gvim dff_asyncres_syncres.v```

</details>

<details>
<summary> Lab Flop Synthesis Simulations </summary>
<br>
	
**D Flip-Flop with Asynchronous Reset**
- Simulation
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```iverilog dff_asyncres.v tb_dff_asyncres.v```
	- ```./a.out```
	- ```gtkwave tb_dff_asyncres.vcd```
- Synthesis
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```yosys```
	- ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```read_verilog dff_asyncres.v```
	- ```synth -top dff_asyncres```
	- ```dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```show```
 
**D Flip_Flop with Asynchronous Set*

- Simulation
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```iverilog dff_async_set.v tb_dff_async_set.v```
	- ```./a.out```
	- ```gtkwave tb_dff_async_set.vcd```
- Synthesis
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```yosys```
	- ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```read_verilog dff_async_set.v```
	- ```synth -top dff_async_set```
	- ```dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```show```

**D Flip-Flop with Synchronous Reset**

- Simulation

	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```iverilog dff_syncres.v tb_dff_syncres.v```
	- ```./a.out```
	- ```gtkwave tb_dff_syncres.vcd```

- Synthesis
	- ```cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files```
	- ```yosys```
	- ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```read_verilog dff_syncres.v```
	- ```synth -top dff_syncres```
	- ```dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
	- ```show```
</details>


<details>
<summary> Interesting Optimisations </summary>
<br>
	
- ```gvim mult_2.v```
- ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- ```read_verilog mult_2.v```
- ```synth -top mul2```
- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- ```show```
- ```write_verilog -noattr mul2_netlist.v```
- ```!gvim mul2_netlist.v```
- ```gvim mult_8.v```
- ```read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- ```read_verilog mult_8.v```
- ```synth -top mult8```
- ```abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib```
- ```show```
- ```write_verilog -noattr mult8_netlist.v```
- ```!gvim mult8_netlist.v```
</details>

# Day 5

## Introduction to Optimisations
<details>
<summary> Combinational Optimisation </summary>
<br>
	
**Combinational Optimisation**	
- Combinational optimization focuses on problems with discrete variables and no time dependence, seeking the best solution from a finite set of options.
- Combinational logic circuits have outputs determined solely by current inputs, without considering previous states.
- Optimizing combinational logic circuits aims to create efficient digital designs, emphasizing area and power efficiency.
- Techniques for optimization include constant propagation, which replaces variables with their constant values, and Boolean logic optimization, which simplifies logic circuits.
- Boolean logic optimization reduces the complexity of Boolean expressions, minimizing terms, literals, and gates needed for logical functions.

</details>
	
<details>
<summary> Sequential Logic Optimisations </summary>
<br>

**Sequential Optimisation**
- Sequential logic optimizations enhance digital circuits with memory elements (e.g., flip-flops) for efficiency, performance, and resource usage.
-  Optimization ensures meeting timing requirements, minimal power consumption, and compact circuit area while maintaining functionality.
- Techniques include sequential constant propagation (propagating constant values in sequential elements), state optimization (reducing FSM states), sequential logic cloning (introducing pipeline stages), and retiming (repositioning flip-flops for shorter clock periods).
- Sequential constant propagation replaces variables with known constant values to enhance performance and resource utilization.
- State optimization reduces FSM states, sequential logic cloning introduces pipeline stages, and retiming balances timing paths without changing circuit functionality.
  
</details>


## Combinational Logic Optimisations

<details>
<summary> opt_check </summary>	
	
+ `gvim opt_check.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check.v`
+ `synth -top opt_check`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

  
</details>

<details>
<summary> opt_check2 </summary>	
	
+ `gvim opt_check2.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check2.v`
+ `synth -top opt_check2`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> opt_check3 </summary>	
	
+ `gvim opt_check3.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check3.v`
+ `synth -top opt_check3`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> opt_check4 </summary>
	
+ `gvim opt_check4.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog opt_check4.v`
+ `synth -top opt_check4`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> multiple_module_opt </summary>
	
+ `gvim multiple_module_opt.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog multiple_module_opt.v`
+ `synth -top multiple_module_opt`
+ `opt_clean -purge`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

## Sequential Logic Optimisations

<details>
<summary> dff_const1 </summary>	

+ `gvim dff_const1.v`

**Simulation**

+ `iverilog dff_const1.v tb_dff_const1.v`
+ `/a.out`
+ `gtkwave tb_dff_const1.vcd`

**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const1.v`
+ `synth -top dff_const1`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> dff_const2 </summary>	

+ `gvim dff_const2.v`

**Simulation**

+  `iverilog dff_const2.v tb_dff_const2.v`
+ `/a.out`
+ `gtkwave tb_dff_const2.vcd`

 **Synthesis**
 
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const2.v`
+ `synth -top dff_const2`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> dff_const3 </summary>

+ `gvim dff_const3.v`

**Simulation**

+ `iverilog dff_const3.v tb_dff_const3.v`
+ `/a.out`
+ `gtkwave tb_dff_const3.vcd`

**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const3.v`
+ `synth -top dff_const3`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> dff_const4 </summary>	

+ `gvim dff_const4.v`

**Simulation**

+ `iverilog dff_const4.v tb_dff_const4.v`
+ `/a.out`
+ `gtkwave tb_dff_const4.vcd`

**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const4.v`
+ `synth -top dff_const4`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> dff_const5 </summary>	

+ `gvim dff_const5.v`

**Simulation**

+ `iverilog dff_const4.v tb_dff_const4.v`
+ `/a.out`
+ `gtkwave tb_dff_const5.vcd`

**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog dff_const4.v`
+ `synth -top dff_const4`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib `
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

## Sequential Optimisations for Unused Outputs
<details>
<summary> counter_opt </summary>

+ `gvim counter_opt.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog counter_opt.v`
+ `synth -top counter_opt`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

<details>
<summary> counter_opt2 </summary>	

+ `gvim counter_opt2.v`
+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog counter_opt2.v`
+ `synth -top counter_opt2`
+ `dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

</details>

# Day 6
## GLS Synthesis-Simulation Mismatch and Blocking Non-blocking Statements

<details>
<summary> GLS Concepts And Flow Using Iverilog </summary>	

 + **Gate Level Simualtion**
   - Gate-level simulation is a technique used in digital design and verification to validate the functionality of a digital circuit at the gate-level implementation.
   - It involves simulating the circuit using the actual logic gates and flip-flops that make up the design, as opposed to higher-level abstractions like RTL (Register Transfer Level) descriptions.
   - This type of simulation is typically performed after the logic synthesis process, where a high-level description of the design is transformed into a netlist of gates and flip-flops.
   - We perform this to verify logical correctness of the design after synthesizing it. Also ensuring the timing of the design is met.
  

+ **Synthesis-Simulation Mismatch**
  - A synthesis-simulation mismatch refers to a situation in digital design where the behavior of a circuit, as observed during simulation, doesn't match the expected or desired behavior of the circuit after it has been synthesized.
  - This discrepancy can occur due to various reasons, such as timing issues, optimization conflicts, and differences in modeling between the simulation and synthesis tools.
  - This mismatch is a critical concern in digital design because it indicates that the actual hardware implementation might not perform as expected, potentially leading to functional or timing failures in the fabricated chip.

+ **Blocking Statements**
  - Blocking statements are executed sequentially in the order they appear in the code and have an immediate effect on signal assignments.
  - Example:

  ``` v
   module BlockingExample(input A, input B, input C, output Y, output Z);
    wire temp;

    // Blocking assignment
    assign temp = A & B;

    always @(posedge C) begin
        // Blocking assignment
        Y = temp;
        Z = ~temp;
    end
   endmodule
  ```

+ **Non-Blocking Statements**
  - Non-blocking assignments are used to model concurrent signal updates, where all assignments are evaluated simultaneously and then scheduled to be updated at the end of the time step.
  - Example:
   ``` v
    module NonBlockingExample(input clock, input D, input reset, output reg Q);

    always @(posedge clock or posedge reset) begin
        if (reset)
            Q <= 0;  // Reset the flip-flop
        else
            Q <= D;  // Non-blocking assignment to update Q with D on clock edge
    end
  endmodule
   ```

+ **Caveats with Blocking Statements**
  + Blocking statements in hardware description languages like Verilog have their uses, but there are certain caveats and considerations to be aware of when working with them. Here are some important caveats associated with using blocking statements:
    - Procedural Execution: Blocking statements are executed sequentially in the order they appear within a procedural block (such as an always block). This can lead to unexpected behavior if the order of execution matters and is not well understood.
    - Lack of Parallelism: Blocking statements do not accurately represent the parallel nature of hardware. In hardware, multiple signals can update concurrently, but blocking statements model sequential behavior. As a result, using blocking statements for modeling complex concurrent logic can lead to incorrect simulations.
    - Race Conditions: When multiple blocking assignments operate on the same signal within the same procedural block, a race condition can occur. The outcome of such assignments depends on their order of execution, which might lead to inconsistent or unpredictable behavior.
    - Limited Representation of Hardware: Hardware systems are inherently concurrent and parallel, but blocking statements do not capture this aspect effectively. Using blocking assignments to model complex combinational or sequential logic can lead to models that are difficult to understand, maintain, and debug.
    - Combinatorial Loops: Incorrect use of blocking statements can lead to unintentional combinational logic loops, which can result in simulation or synthesis errors.
    - Debugging Challenges: Debugging code with many blocking assignments can be challenging, especially when trying to track down timing-related issues.
    - Not Suitable for Flip-Flops: Blocking assignments are not suitable for modeling flip-flop behavior. Non-blocking assignments (<=) are generally preferred for modeling flip-flop updates to ensure accurate representation of concurrent behavior.
    - Sequential Logic Misrepresentation: Using blocking assignments to model sequential logic might not capture the intended behavior accurately. Sequential elements like registers and flip-flops are better represented using non-blocking assignments.
    - Synthesis Implications: The behavior of blocking assignments might not translate well during synthesis, leading to potential mismatches between simulation and synthesis results.

</details>

## Labs on GLS and Synthesis-Simulation Mismatch
<details>
<summary> ternary_operator_mux </summary>	

+ `gvim teranry_operator_mux.v`

**Simulation**

+ `iverilog ternary_operator_mux.v tb_ternary_operator_mux.v`
+ `./a.out`
+ `gtkwave tb_ternary_operator_mux.vcd`


**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog ternary_operator_mux.v`
+ `synth -top ternary_operator_mux`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`


**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`


</details>

<details>
<summary> bad_mux </summary>	

 + `gvim bad_mux.v`

 
**Simualtion**

+ `iverilog bad_mux.v tb_bad_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`


**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog bad_mux.v`
+ `synth -top bad_mux`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v`
+ `./a.out`
+ `gtkwave tb_bad_mux.vcd`

</details>

## Labs on Synth-Sim Mismatch for Blocking Statement

<details>
<summary> blocking_caveat </summary>	

+ `gvim blocking_caveat.v`


**Simualtion**

+ `iverilog blocking_caveat.v tb_blocking_caveat.v`
+ `./a.out`
+ `gtkwave tb_blocking_caveat.vcd`

**Synthesis**

+ `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog blocking_caveat.v`
+ `synth -top blocking_caveat`
+ `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `show`

**GLS to Gate-Level Simulation**

+ `iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v`
+ `./a.out`
+ `gtkwave tb_blocking_caveat.vcd`

</details>

