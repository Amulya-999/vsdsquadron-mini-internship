# vsdsquadron-mini-internship

## TASK-1
### Task is to install RISC-V toolchain and refer to C based and RISC-V based videos and to compile the c program using gcc and RISC-V simulator


## C LANGUAGE BASED LAB
#### 1. After installing the RISC-V toolchain , the task is to compile a C program which calculates the sum of numbers from 1 to n using GCC Compiler.
#### 2. The command 'leafpad sum1ton.c &' is used to open a text editor called Leafpad with the file name sum1ton.c for editing in which the c program to find the sum of numbers from 1 to n is written.
#### 3. The command 'gcc sum1ton.c' is used to compile the C program which is in file sum1ton.c  into an executable program
#### 4. The command './a.out' is used to execute the compiled program.
#### As  the code is written to find the sum of numbers from 1 to 5,by following the above commands this code is compiled and output is produced as 15.


![VirtualBox_vsdworkshop_23_05_2024_17_44_22](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/deb28ef8-428b-4f8a-8ae4-c5b42a1e821d)



## RISC-V BASED LAB
#### Now,the task is to compile the same C program using RISC-V simulator
#### 1. we use the command 'cat sum1ton.c' to view the code on the terminal
#### 2. To compile the code we use the command 'riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c'
#### Here, -mabi=lp64 flag in the RISC-V compiler command specifies the ABI (Application Binary Interface) and the data model for our compiled program
#### '-mabi': This flag specifies the ABI to use , 'lp64': This part defines the data model used for the ABI.
#### RISC-V supports different ABIs depending on the specific requirements of our application.so,'lp64'denotes the long integer pointer that is it signifies that pointers are 64 bit wide.
#### -o is the currently using optimization level.
#### sum1ton.o is the output file and sum1ton.c is the input file.
#### It generates a file sum1ton.c

![1](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/fbaa359a-49a4-474c-a2a4-40792fce564e)

#### 3. Open a new tab terminal and see the assembly code for c code,command to see the assembly code of c code is 'riscv64-unknown-elf-objdump -d sum1ton.o'
 'objdump': This is the specific command within the toolchain used to disassemble object files.
#### 4. This gives bunch of assembly codes,to reduce the code we use the command 'riscv64-unknown-elf-objdump -d sum1ton.o '| less'

![2](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/732c1d66-59d5-4199-aca3-331e1ea4e693)

#### We get a huge section of code but we are interested in main section of the code so type '/main'.

![3](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/7b016ed8-493a-4247-b1bc-6d70b9fc9541)

#### 5. Now,press n we get the main section with its address.

![4](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/f41828e6-cebf-4651-b5c4-ea3ad1b18fd2)

#### so we see that there are 35 instructions in main section.
#### 6. Repeat the same from the starting with higher optimization level -ofast in the command as shown in below picture.

![5](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/46bf9785-68c7-462f-b8fb-3e734918c72c)

#### here also we get 35 instructions

![6](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/61ad25f5-3adf-46ad-a38c-d92e87015519)

#### - As the task is simple, The no.of instructions didnot change because for simple tasks,the optimization applied at -o1 may already be sufficient to achieve the most efficient code.higher level of optimization (-ofast) might not find additional way to reduce the instruction count and also instruction count can vary from one machine to other machine based on several factors like different machines may have different microarchitectures and small differences in compilers implementation can affect the change in instruction count.
#### - For complex tasks,instruction count reduces in -ofast level of optimization


## TASK -2 

### Task is to identify various RISC-V instruction type and exact 32-bit instruction code in instruction type format for few RISC-V instructions

#### WHAT IS RISC-V ?

![RISCV](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/edbd60ad-1bf8-4b08-9a05-68414ff0a26e)

1 . RISC-V stands for reduced instruction set computing fifth generation.<br>
2 . It is a open source instruction set architecture used to develop custom processors for variety of applications.<br>
3 . The customization of RISC-V allows chip designers to create processors for specific tasks like low-power applications or high performance computing instead of one-size-fits-all approach.<br>
4 . RISC-V has steamlined instruction set making it easier to learn,develop and more effient in terms of power consumption and performance.<br>

#### INSTRUCTION SET OF RISC-V 

1 . Instruction set in RISC-V or any other computer architecture refers to the collection of instructions that a processor can execute.<br>
2 . These instructions are the commands that tell the processor what operation to perform such as arithmetic operations,data movement,control flow and other functions.<br>
3 . RISC-V instruction set focusses on basic operations like loading data into registers , performing arithmetic calculations and storing results.<br>
4 . This simpler approach can make RISC-V  processor easier to design and potentially more efficient than processors with complex instruction sets.<br>
5 . RISC-V supports 16 bit(RVC) , 32 bit(RV32I) and 64 bit(RV64I).<br>

#### 32 BIT INSTRUCTION SET OF RISC-V

1 . 32 Bit instruction set of RISC-V includes several types of instructions each serving different purposes.<br>
Types of 32 bit instructions in RISC-V is
* R-TYPE
* I-TYPE
* S-TYPE
* B-TYPE
* U-TYPE
* J-TYPE
  
![INSTRUCTION SET](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/999f2eca-827b-47d8-885f-7e85e84e87c7)

#### R-TYPE INSTRUCTION
1 . R-TYPE is Register type instructions.<br>
2 . They are fundamental for performing operations such as addition,subtraction,bitwise operations and shifts.<br>
 #### FORMAT OF R-TYPE INSTRUCTIONS

| funct7 (7 bits) | rs2 (5 bits) | rs1 (5 bits) | funct3 (3 bits) | rd (5 bits) | opcode (7 bits) |

1 . opcode (7 bits):This field is of 7bits.it Specifies the operation type and indicates that this is an R-type instruction. For R-type instructions, the opcode is typically 0110011.

2 . rd (5 bits): This field is of 5 bits.The destination register. It specifies which register will receive the result of the operation.

3 . funct3 (3 bits): This field is of 3 bits.it Further specifies the operation to be performed. It differentiates between different operations that share the same opcode.

4 . rs1 (5 bits): This field is of 5 bits.It is the first source register. It specifies the register containing the first operand.

5 . rs2 (5 bits): This field is of 5 bits.It is the second source register. It specifies the register containing the second operand.

6 . funct7 (7 bits): This field is of 7 bits.It Provides additional opcode extension for more fine-grained operation control. It helps to distinguish between different operations that share the same opcode and funct3 values.<br>
7 . Other Common R-Type Instructions
* SUB (Subtract) : <br>
funct7: 0100000 <br>
funct3: 000<br>
Example: SUB x10, x1, x2<br>
* AND (Bitwise AND) :<br>
funct7: 0000000<br>
funct3: 111<br>
Example: AND x10, x1, x2<br>
* OR (Bitwise OR) :<br>
funct7: 0000000<br>
funct3: 110<br>
Example: OR x10, x1, x2<br>
* SLL (Shift Left Logical) :<br>
funct7: 0000000<br>
funct3: 001<br>
Example: SLL x10, x1, x2<br>
* SLT (Set Less Than) :<br>
funct7: 0000000<br>
funct3: 010<br>
Example: SLT x10, x1, x2<br>

 #### I-TYPE INSTRUCTION
 1 . I-TYPE is immediate type instruction format in 32 bit RISC-V ISA.<br>
 2 . It is used for operations that involve an immediate value,which is a constant encoded directly within the instruction itself.<br>
 3 . This immediate value is used in various operations specified by the instruction, such as arithmetic, logical operations, memory accesses, or branching.<br>

 #### FORMAT OF I-TYPE INSTRUCTION

  | immediate(16 bits) | rs1(5 bits) | funct3(3 bits)| rd(5 bits) | opcode(16 bits) |

1 . Opcode (6 bits): The opcode field specifies the operation to be performed by the instruction. It indicates the type of instruction, such as arithmetic, logical, or memory-related operation.it is of 6 bits.<br>

2 . Source Register (rs1) (5 bits): This field identifies the source register from which data will be read for the operation. In some cases, this might be the base register for memory operations.it is of 5 bits.<br>

3 . Destination Register (rd) (5 bits): This field specifies the register where the result of the operation will be stored. For memory-related operations, this might indicate the destination register where the loaded data will be stored.<br>

4 . Immediate Value (16 bits): The immediate field contains a constant or immediate value that is used in the operation. This value might be added to a register, compared with a register value, or used as an offset for memory operations.<br>

5 . Sign Extension: Since the immediate field is only 16 bits in length, it needs to be sign-extended to the full width of the register (32 bits) before being used in arithmetic or logical operations. Sign extension ensures that the immediate value is properly interpreted as a signed value.<br>

example : <br>
This format allows for instructions like "add immediate" (addi), "load byte" (lb), "store byte" (sb), and many others where an immediate value is needed for the operation.<br>
1 . Add Immediate (addi): This instruction adds an immediate value to the value in a register and stores the result in another register.<br>
2 . Load Byte (lb): This instruction loads a byte from memory into a register, using an immediate offset from a base register.<br>
3 . Branch on Equal (beq): This instruction compares two registers and branches to a target address if they are equal, using an immediate offset for the branch target.<br>

#### S-TYPE INSTRUCTION

1 . S-TYPE is store type instruction used for memory store operations.<br>
2 . These instructions are responsible for storing data from a register into memory.<br>
3 . The "s" type instruction is one of the basic instruction formats used for performing arithmetic or logical operations that involve a register and an immediate value, where the immediate value is 12 bits long. This instruction format is primarily used for instructions that store a value into memory, hence the "s" designation, which stands for "store."

#### FORMAT OF S-TYPE INSTRUCTION 

| imm[11:5](7 bits)  | rs2(5 bits) | rs1(5 bits) | funct3(3 bits) | imm[4:0](5 bits)| opcode |

1 . Opcode (7 bits) [0-6]: This field specifies the operation to be performed. For S-type instructions, the opcode typically indicates a store operation, such as sw (store word), sh (store halfword), or sb (store byte).<br>

2 . Immediate (I) (7 bits) [7-11, 25-31]: The immediate field is split into two parts in the instruction encoding. The lower 5 bits (imm[4:0]) occupy bits 7-11, and the upper 7 bits (imm[11:5]) occupy bits 25-31. These parts are combined to form a 12-bit immediate value, which is sign-extended to create the full immediate value used in the address calculation for the store operation.<br>

3 . rs1 (5 bits) [15-19]: This field specifies the source register 1, which contains the base address for the memory operation. It is used along with the immediate value to calculate the effective address where the data will be stored.<br>

4 . rs2 (5 bits) [20-24]: This field specifies the source register 2, which contains the data to be stored in memory.<br>

5 . funct3 (3 bits) [12-14]: This field specifies the function or the specific variant of the store instruction. It distinguishes between different types of store instructions, such as sw (store word), sh (store halfword), and sb (store byte).<br>

Example :<br>
Opcode: For sw, the opcode is 0100011 (binary).<br>
funct3: For sw, the funct3 is 010 (binary).<br>
rs1: This would be the register containing the base address (e.g., x1 might be represented as 00001 in binary).<br>
rs2: This would be the register containing the data to be stored (e.g., x2 might be represented as 00010 in binary).<br>
Immediate: The immediate value is split into two parts:<br>
imm[11:5] (upper bits)<br>
imm[4:0] (lower bits)<br>

#### B-TYPE INSTRUCTION

1. B-TYPE is a branch type instruction used for conditional branch operations.<br>
2. These instructions allow the program to jump to a different part of the code based on the evaluation of a condition.<br>
 #### FORMAT OF B-TYPE INSTRUCTION

| imm[12] | imm[10:5] | rs2 | rs1 | funct3 | imm[4:1] | imm[11] | opcode |

1 . Opcode (7 bits) [0-6]: This field specifies the type of operation to be performed. For B-type instructions, the opcode typically indicates a branch operation. For example, common opcodes include 1100011 for branch instructions.<br>

2 . Immediate (I) (12 bits) [7, 8-11, 25-30, 31]: The immediate field is split into multiple parts in the instruction encoding. These parts are combined to form a 13-bit immediate value, which is sign-extended to create the full offset used for the branch target address. The parts are as follows:<br>
imm[11] (bit 7)<br>
imm[4:1] (bits 8-11)<br>
imm[10:5] (bits 25-30)<br>
imm[12] (bit 31)<br>

3 . rs1 (5 bits) [15-19]: This field specifies the source register 1, which contains one of the operands for the comparison.<br>

4 . rs2 (5 bits) [20-24]: This field specifies the source register 2, which contains the other operand for the comparison.<br>

5 . funct3 (3 bits) [12-14]: This field specifies the specific branch condition (e.g., equal, not equal, less than, etc.). It determines the type of comparison to be made between the values in rs1 and rs2.<br>

example: Branch if Equal (beq)<br>
 Here’s how a beq instruction is encoded and how each field is used:<br>
Opcode: For beq, the opcode is 1100011 (binary).<br>
funct3: For beq, the funct3 is 000 (binary).<br>
rs1: This would be the register containing the first operand (e.g., x1 might be represented as 00001 in binary).<br>
rs2: This would be the register containing the second operand (e.g., x2 might be represented as 00010 in binary).<br>
Immediate: The immediate value specifies the offset for the branch target address. It is split into multiple parts:<br>
imm[12]
imm[10:5]
imm[4:1]
imm[11]<br>


#### U-TYPE INSTRUCTION
 1. U-TYPE instruction is upper intermediate instruction used for operations that involve a 20-bit immediate value, typically to load this immediate value into the upper 20 bits of a register. <br>
 
  #### FORMAT OF U-TYPE INSTRUCTION
 
|   imm[31:12]   |  rd   | opcode  |

1. Immediate (imm) (20 bits) [12-31]: This field contains the 20-bit immediate value that is typically used to set the upper 20 bits of a register. The immediate value is left-shifted by 12 bits to align it with the upper part of the register.<br>

2 . rd (5 bits) [7-11]: This field specifies the destination register where the result will be stored.<br>

3 . Opcode (7 bits) [0-6]: This field specifies the type of operation to be performed. For U-type instructions, common opcodes include LUI (Load Upper Immediate) and AUIPC (Add Upper Immediate to PC).<br>

 example : <br>
 -LUI (Load Upper Immediate): Loads the 20-bit immediate value into the upper 20 bits of the destination register, with the lower 12 bits set to zero.<br>
Opcode: 0110111 (binary).<br>
-AUIPC (Add Upper Immediate to PC): Adds the 20-bit immediate value (shifted left by 12 bits) to the current value of the program counter (PC) and stores the result in the destination register.<br>
Opcode: 0010111 (binary).<br>

#### J-TYPE INSTRUCTION

1 . The J-type (Jump) instruction format is used for jump operations that involve a large immediate value, typically for implementing control flow instructions like unconditional jumps.<br>
2 . The primary instruction that uses the J-type format is JAL (Jump And Link).

#### FORMAT OF J-TYPE INSTRUCTION

|  imm[20] | imm[10:1] | imm[11] | imm[19:12] |   rd  | opcode  |<br>
 
1 . opcode (7 bits):  This field specifies the operation code. For the JAL instruction, the opcode is 1101111 (binary) or 0x6F (hex).<br>

2 . rd (5 bits): This field specifies the destination register where the return address will be stored. This is usually the register x1 (the link register).<br>

3 . imm[20] (1 bit): This is the most significant bit of the immediate value.<br>

4 . imm[10:1] (10 bits): These bits are part of the immediate value.<br>

5 . imm[11] (1 bit): This bit is part of the immediate value.<br>

6 . imm[19:12] (8 bits): These bits are part of the immediate value.<br>

#### let us write 32bit opcode for few instruction type formats....
 ##### 1. ADD r6,r2,r1
 - it is a r-type instruction as it involves arithmetic operation add.<br>
funct7 = 0000000<br>
rs2 = 00001<br>
rs1 = 00010<br>
funct3 = 000<br>
rd = 00110<br>
opcode for ADD = 0110011<br>
32 bit instruction code is 0000000 00001 00010 000 00110 0110011<br>

##### 2. SUB r7,r1,r2
- it is a r-type instruction as it involves arithmetic operation sub.<br>
funct7 = 0100000<br>
rs2 = r2 =  00010<br>
rs1 = r1 =  00001<br>
funct3 = 000<br>
rd = r7 = 00111<br>
opcode for SUB = 0110011<br>
32 bit instruction code is 0100000 00010 00001 000 00111 0110011<br>

#### 3. AND r8,r1,r3
  -it is a r-type instruction as it involves logical operation AND.<br>
funct7: 0000000(7 bits)<br>
rs2 = r3 = 00011(5 bits) <br>
rs1 = r1 = 00001 (5 bits)<br>
funct3 = 111 (3 bits)<br>
rd = r8 = 01000 (5 bits)<br>
opcode for AND  = 0110011 (7 bits)<br>
32 bit instruction code is 0000000 00011 00001 111 01000 01000<br>

#### 4. OR r9,r2,r5
- it is r-type instruction as it involves logical operation.<br>
func7 = 0000000<br>
rs2 = r5 = 00101<br>
rs1 = r2 = 00010<br>
func3 = 110<br>
rd = r9 = 01001<br>
Opcode for OR = 0110011<br>
32 bit instruction code is 0000000 00101 00010 110 01001 0110011<br>

#### 5. XOR r10, r1, r4
- it is r-type instruction as it involves logical operation.<br>
Opcode for XOR = 0110011<br>
rd = r10 = 01010<br>
rs1 = r1 = 00001<br>
rs2 = r4 = 00100<br>
func3 = 100<br>
func7 = 0000000,br>
32 bits instruction : 0000000 00100 00001 100 01010 0110011<br>

#### 6. SLT r11, r2, r4
- it is r-type instruction as it involves logical operations on registers.<br>
- r1 is the destination register, if r2 is less than r4 it sets to 1 else  if r2 is greater than r4 it sets to 0<br>
Opcode for SLT = 0110011<br>
rd = r1 = 01011<br>
rs1 = r2 = 00010<br>
rs2 = r4 = 00100,br>
func3 = 010<br>
func7 = 0000000<br>
32 bits instruction : 0000000 00100 00010 010 01011 0110011<br>

#### 7.ADDI r12, r4, 5
- it is I-type instruction as it states that addition with immediate.<br>
- r12 is the destination register that will store the value of rs1 addition with the immediate value 5.<br>
Opcode for ADDI = 0010011<br>
rd = r12 = 01100<br>
rs1 = r4 = 00100<br>
imm[11:0] = 5 = 000000000101<br>
func3 = 000<br>
32 bits instruction : 000000000101 00100 000 01100 0010011<br>

#### 8. SW r3, r1, 2
- it is s-type instruction as sw states store word<br>
- r3 is the source register. This instruction will store the value located in register r3 at the address obtained by adding the immediate address 2 with the address located in register r1.<br>
Opcode for SW = 0100011<br>
rs2 = r3 = 00011<br>
rs1 = r1 = 00001<br>
imm[11:0] = 2 = 000000000010<br>
func3 = 010<br>
32 bits instruction : 0000000 00011 00001 010 00010 0100011<br>

 #### 9. SRL r16, r14, r2
 - it is a r-type instruction as it states logucal shift right.<br>
 -16 is the destination register, in which the value stored in r14 will be written after performing logical right shift based on the number stored in r2.<br>
func7 = 0000000<br>
rs2 = r2 = 00010<br>
rs1 = r14 = 01110<br>
func3 = 101<br>
rd = r16 = 10000<br>
Opcode for SRL = 0110011<br>
32 bits instruction : 0000000 00010 01110 101 10000 0110011

#### 10. BNE r0,r0,15
- it is a b-type instruction as BNE stand for "branch if not equal" and and checks whether the contents of registers r0 and r0 are not equal.<br>
- since r0 is the zero register (which always contains zero), this particular instruction is essentially checking if zero is not equal to zero, which is always false. Thus, the branch will never be taken.<br>
Opcode: The opcode for all branch instructions is 1100011 (7 bits).<br>

Funct3: The funct3 field for BNE is 001 (3 bits).<br>

rs1 and rs2: Both registers are r0, which is register 0.<br>

Immediate: The immediate value (offset) is 15. The immediate in B-type is split and placed into different parts of the instruction format:<br>

Immediate value 15 in binary: 0000 0000 0000 1111 (12 bits).<br>
imm[12] (bit 31) = 0<br>
imm[10:5] (bits 30-25) = 000000<br>
imm[4:1] (bits 11-8) = 1111<br>
imm[11] (bit 7) = 0<br>
32 bit instruction code is = 0 000000 00000 00000 001 1111 0 1100011<br>

#### 11 . LW r13,r1,2
- it is I-type instruction.<br>
- the LW (Load Word) instruction is an I-type instruction, which is used to load a 32-bit word from memory into a register.<br>
imm[11:0] = 2 = 00000000001<br>
rs1 = r1 = 00001<br>
funct3 for LW = 010<br>
rd = r13 = 01101<br>
opcode for LW = 0000011<br>
32 bit instruction code is = 000000000010 00001 010 01101 0000011<br>

#### 12. SLL r15,r1,r2
- it is r-type instruction as it involves logical operation.<br>
- SLL stands for shift left logical.<br>
funct7 = 0000000<br>
rs2 = r2 = 00010<br>
rs1 = r1 = 00001<br>
funct3 = 001<br>
rd = r15 = 01111<br>
opcode = 0110011<br>
32 bit instruction code is = 0000000 00010 00001 001 01111 0110011

## TASK - 3

#### Task is to perform function simulation on RISC-V core verilog netlist and testbench and observe the output waveforms of few instructions of hardcoded ISA.

The verilog code and testbench of RISC-V is already designed which is taken from the reference github repo provided.<br>

To perform Functional simulation:<br>
1. create a new directory with any name using the command "mkdir < name > " like<br>
         mkdir amulya.<br>

3. create two files   amulya_v.v  and   amulya_tb.v using the command<br>

     "touch amulya_v.v amulya_tb.v".  so,two files are created in directory.<br>

4.  copy and paste the verilog code in amulya_v.v file and testbench in amulya_tb.v file from reference repo.<br>

5. now,make sure that you are on right directory (cd amulya) and to run and simulate the code use the command.<br>

   iverilog -o amulya amulya_v.v amulya_tb.v<br>
   ./amulya<br>
   
6. to see the waveforms install gtkwave by using command "sudo apt install gtkwave"<br>

7. now to see the waveforms use the command "gtkwave iiitb_rv32i.vcd"<br>
   
![task 1 pic 1](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/877e2487-709f-44f0-a514-fab9147c56b9)

8. click on "+" button at your file name on the top then you will get list of signals.<br>

    ![task 2](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/6cd3dfbb-46b0-4316-92d5-72eeae3ad3cb)


10. as shown in fig , all the instructions in verilog code is hardcoded.<br>


#### what is hardcoded ISA ?

1. A Hardcoded ISA is an ISA where the instructions and their execution logic are directly implemented in the hardware circuitary of a processor.<br>
2. Hardcoded ISA offers advantages in terms of speed and efficiency.<br>

Now instead of following RISC-V instructions we follow the Hardcoded ISA pattern.<br>

THE HARDCODED ISA PATTERN FROM REFERENCE REPO IS :<br>

##### ADD R6, R2, R1	   -	32'h02208300
##### SUB R7, R1, R2   	-	32'h02209380
##### AND R8, R1, R3	   -	32'h0230a400
##### OR R9, R2, R5	    - 	32'h02513480
##### XOR R10, R1, R4	  - 	32'h0240c500
##### SLT R1, R2, R4	   - 32'h02415580
##### ADDI R12, R4, 5 	 - 	32'h00520600
##### BEQ R0, R0, 15	   - 32'h00f00002
##### SW R3, R1, 2	     - 	32'h00209181
##### LW R13, R1, 2    	- 32'h00208681
##### SRL R16, R14, R2 	- 32'h00271803
##### SLL R15, R1, R2	  - 32'h00208783

### observation of various waveforms for the instructions 

#### 1. ADD R6,R2,R1

![add new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/d5486e80-8782-46e1-84b1-dc824f1d77d5)

here in the signals to get the waveform of instruction ADD R6,R2,R1;<br>

1. clk: Represents the clock signal.<br>

2. EX_MEM_IR[31:0]: Holds the instruction being executed in the EX stage of the pipeline.<br>

3. ID_EX_A[31:0]: Contains the value of register r1.<br>

4. ID_EX_B[31:0]: Contains the value of register r2.<br>

5. EX_MEM_ALUOUT[31:0]: Represents the result of the ALU operation in the EX stage.<br>


EX stage is  where the arithmetic or logic operations specified by the instruction are actually performed.<br>

similarly for other arithmetic and logical instructions also.<br>

#### 2. SUB R7,R1,R2

![sub new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/4bf8c586-d8d6-4837-9de4-089fb3f11b78)

#### 3. AND R8,R1,R3

![and new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/9ae2d285-eb26-4b08-8d88-e90a1294b36b)

#### 4. OR R9,R2,R5 

![or new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/f160a374-d792-4861-90f5-bb4b527092e0)

#### 5. SLT R1,R2,R4

![slt new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/7e7eb0bf-c4c2-488a-a7b6-8a27f02ecdaf)

#### 6. XOR 10,R1,R4

![xor new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/de75a1ff-0dac-49ad-8e01-ff1b7d33d032)

#### 7. ADDI R12,R4,5

![addi new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/bb02272e-d8b1-485f-a45a-cdd92cf15a81)

#### 8. BEQ R0,R0,15

![beq new](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/56c67770-6ef6-40d0-8d11-c63e160d7443)

   
## TASK - 4

### TASK IS TO IMPLEMENT ANY DIGITAL CIRCUIT USING RISC-V VSDSQUADRON MINI BOARD

#### IMPLEMENTING 2:1 MULTIPLEXER USING RISC-V VSDSQUADRON MINI BOARD.

#### OVERVIEW

This project involves implementing 4:1 multiplexer using RISC-V VSDsquadron mini board.A 4:1 multiplexer (MUX) is a digital switch that selects one of four input signals and forwards the selected input to a single output line. It operates based on the values of two selection (or control) lines. A 4:1 multiplexer (MUX) has various applications in digital electronics due to its ability to select and route one of several input signals to a single output line.It is a versatile digital component used in various applications to streamline and simplify signal selection and routing tasks in electronic systems..This project will demonstrate the practical application of digital logic design using a RISC-V based development platform. <br>

#### What is a 4:1 Multiplexer?
A 4:1 multiplexer is a digital switch that allows one of four input signals to pass through to the output based on two control signals. The selection mechanism is simple:<br>

let the four inputs be D0,D1,D2,D3 and two control signals be S0,S1 then<br>

When the control signal (S0,S1) is 0,0  the output (Y) is the first input D0 .<br>
When the control signal (S0,S1) is 0,1 the output (Y) is the second input D1.<br>
When the control signal (S0,S1) is 1,0 the output (Y) is the second input D2.<br>
When the control signal (S0,S1) is 1,1 the output (Y) is the second input D3.<br>

#### COMPONENTS REQUIRED :

1. VSDsquadron mini board
2. push buttons - 6 for giving input data
3. LED's - 1 for displaying output
4. Breadboard
5. jumper wires
6. VS code for software development

#### HARDWARE CONNECTIONS :

##### input : Six inputs of single bit are connected to the GPIO pins of VSDSquadron Mini to push buttons placed on the breadboard.
##### output : One LED is connected to display the output on breadboard from the GPIO pins of mini board.

#### CIRCUIT CONNECTIONS :

![Screenshot (256)](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/3defb23e-6723-4463-89ba-5786baa67743)


#### TRUTH TABLE TO VERIFY 4:1 MUX :

| S1 | S0 |  Y  |
|----|----|-----|
|  0 |  0 | D0  |
|  0 |  1 | D1  |
|  1 |  0 | D2  |
|  1 |  1 | D3  |

#### CODE FOR IMPLEMENTATION

#include <stdio.h>
#include <debug.h>
#include <ch32v00x.h>

// Defining the Logic Gate Function
int and(int bit1, int bit2) {
    int out = bit1 & bit2;
    return out;
}

int or(int bit1, int bit2) {
    int out = bit1 | bit2; // Changed to bitwise OR
    return out;
}

int not(int bit1) {
    int out = ~bit1 & 0x01;
    return out;
}

void GPIO_Config(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0}; // structure variable used for GPIO configuration
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE); // to enable the clock for port D
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC, ENABLE); // to enable the clock for port C

    // Input Pins Configuration
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_1 | GPIO_Pin_2 | GPIO_Pin_3 | GPIO_Pin_4 | GPIO_Pin_5 | GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU; // Defined as Input Type with Pull-Up
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Output Pin Configuration
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_5;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Defined Output Type
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz; // Defined Speed
    GPIO_Init(GPIOC, &GPIO_InitStructure);
}

// The MAIN function responsible for the execution of program
int main() {
    uint8_t s0, s1, in0, in1, in2, in3; // Declared the required variables
    uint8_t x, y, a1, a, b1, b, c1, c, d1, d, e1, e2, e;
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_2);
    SystemCoreClockUpdate();
    Delay_Init();
    GPIO_Config();

    while(1) {
        s0 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_1); // Selection line 1
        s1 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_2); // Selection line 2
        in0 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_3); // Input 0
        in1 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_4); // Input 1
        in2 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_5); // Input 2
        in3 = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_6); // Input 3
        
        x = not(s0);
        y = not(s1);
        a1 = and(x, y);
        a = and(a1, in0);
        b1 = and(x, s1);
        b = and(b1, in1);
        c1 = and(s0, y);
        c = and(c1, in2);
        d1 = and(s0, s1);
        d = and(d1, in3);
        e1 = or(a, b);
        e2 = or(c, d);
        e = or(e1, e2);

        if (e == 1) { // Changed condition to check if e is 1
            GPIO_WriteBit(GPIOC, GPIO_Pin_5, SET); // Set pin high if e is 1
        } else {
            GPIO_WriteBit(GPIOC, GPIO_Pin_5, RESET); // Set pin low if e is 0
        }
    }
}

#### APPLICATION VIDEO

https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/c8f9e924-ab06-428b-b7c2-fbc76c2e922c


