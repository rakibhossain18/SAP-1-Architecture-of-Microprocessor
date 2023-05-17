# Designing and Implementing a SAP-1 Computer

The SAP-1 computer, which represents the first stage in this progression, is equipped with all of the necessary components to work. The main goal of the course is to give students a fundamental grasp of how computers operate, interact with memory, and connect with other system components like input and output. The instruction set is relatively small and straightforward.

## Table of Content

1. [SAP-1 Architecture](#sap-1-architecture)
   - [SAP-1 Components](#sap-1-components)
2. [Design Process](#design-process)
   - [Logisim Design Images](#logisim-design-images)
<!-- 3. [Implementation Process](#implementation-process)
4. [Results](#results)
   - [Programmed FPGA](#programmed-fpga)
   - [Operation Codes](#operation-codes)
5. [Learn More](#learn-more)
   - [Reference 1](#reference-1)
   - [Reference 2](#reference-2)
   - [Reference 3](#reference-3)
   - [Reference 4](#reference-4) -->

## SAP-1 Architecture

The SAP-1 computer utilizes Von-Neumann architecture and is bus-organized. It contains ten major components and an 8-bit core bus. Below is a picture of the building's architecture. The description of each component that makes up this computer follows.


![SAP-1 Computer Architecture](./Components/sap_1.jpeg)


### SAP-1 Components

1. **Program Counter**: The function of the program counter is to send and save the memory address of the subsequent instruction that has to be retrieved and executed. The control unit's program counter, which counts from 0000 to 1111, is a component. The program counter delivers the next address, 0001, to the memory once the first instruction has been fetched and performed, and it is then incremented once more. The program counter maintains track of the following instruction that needs to be fetched and performed in this manner.

2. **Input and Memory Address Register (MAR)**: The 4-bit address of data or instructions stored in memory is kept in the Memory Address Register (MAR). The 4-bit address is obtained from the Program Counter through the bus and then stored when the SAP-1 is executing. The RAM is where data or instructions are read from when this stored address is sent there.

3. **Random-Access Memory (RAM)**: The 4-bit address of data or instructions stored in memory is kept in the Memory Address Register (MAR). The 4-bit address is obtained from the Program Counter through the bus and then stored when the SAP-1 is executing. The RAM is where data or instructions are read from when this stored address is sent there.

4. **Instruction Register**: The instruction takes the instruction from the RAM that was put on the bus and stores it. The instruction register's contents are then divided into two bits. The bottom nibble is a three-state output that is read off the bus as necessary, while the top nibble is a two-state output that goes into the Controller-sequencer.

5. **A-Register**: The A-register is a buffer register used store 8-bit data. It supplies the data to the Arithmetic Logic Unit (ALU) to add/subtract. 

6. **B-Register**: This is same as ***A-Register***

7. **Arithmetic Logic Unit (ALU)**: The Arithmetic Logic Unit (ALU) asynchronously adds or subtracts a value from the A-Register and B-Register. To do this, it makes advantage of the complement of 2. The output of the ALU is the sum of these values when Su is low, and the subtraction of these values when Su is high.


## Design Process


<!-- ![Instruction Register](./images/IR.png)
<br>
_Instruction Register_

<hr> -->

Circuit schematics were created for each part of the microprocessor used to form the SAP-1 architecture. Using buses, these components were subsequently combined into a single system. Using Logisim, a program for creating and simulating logic circuits, each circuit diagram was created and tested.


### Program Counter
This counter stores the current step to be processed from the RAM. Basically, this counts the lines of our program. So, at 0000, first line of the program is executed and at 0001 the second line is executed. The output can be enabled using “pc_en” pin. This is made using cascaded master-slave JK flip-flops. 

![Program Counter](./Components/program_counter.JPG)
<br>
_Program Counter_
<hr>

