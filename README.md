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

6 . funct7 (7 bits): This field is of 7 bits.It Provides additional opcode extension for more fine-grained operation control. It helps to distinguish between different operations that share the same opcode and funct3 values.
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

   31       25 24    20 19    15 14    12 11    7 6       0
+-----------+--------+--------+--------+--------+---------+
|  immediate|   rs1  |  funct3|   rd   |  opcode|         |
+-----------+--------+--------+--------+--------+---------+

1 . Opcode (6 bits): The opcode field specifies the operation to be performed by the instruction. It indicates the type of instruction, such as arithmetic, logical, or memory-related operation.it is of 6 bits.<br>

2 . Source Register (rs) (5 bits): This field identifies the source register from which data will be read for the operation. In some cases, this might be the base register for memory operations.it is of 5 bits.<br>

3 . Destination Register (rt) (5 bits): This field specifies the register where the result of the operation will be stored. For memory-related operations, this might indicate the destination register where the loaded data will be stored.<br>

4 . Immediate Value (16 bits): The immediate field contains a constant or immediate value that is used in the operation. This value might be added to a register, compared with a register value, or used as an offset for memory operations.<br>

5 . Sign Extension: Since the immediate field is only 16 bits in length, it needs to be sign-extended to the full width of the register (32 bits) before being used in arithmetic or logical operations. Sign extension ensures that the immediate value is properly interpreted as a signed value.<br>

4 . This format allows for instructions like "add immediate" (addi), "load byte" (lb), "store byte" (sb), and many others where an immediate value is needed for the operation.<br>
examples : <br>
5 . Add Immediate (addi): This instruction adds an immediate value to the value in a register and stores the result in another register.<br>
6 . Load Byte (lb): This instruction loads a byte from memory into a register, using an immediate offset from a base register.<br>
7 . Branch on Equal (beq): This instruction compares two registers and branches to a target address if they are equal, using an immediate offset for the branch target.<br>

#### S-TYPE INSTRUCTION

1 . S-TYPE is store type instruction used for memory store operations.<br>
2 . These instructions are responsible for storing data from a register into memory.<br>
3 . The "s" type instruction is one of the basic instruction formats used for performing arithmetic or logical operations that involve a register and an immediate value, where the immediate value is 12 bits long. This instruction format is primarily used for instructions that store a value into memory, hence the "s" designation, which stands for "store."

#### FORMAT OF S-TYPE INSTRUCTION 

| 31  | 30 29 28 27 26 25 | 24 23 22 21 20 | 19 18 17 16 15 | 14 13 12 | 11 10  9  8  7 |  6  5  4  3  2  1  0 |
| imm[11:5]               | rs2            | rs1            | funct3   | imm[4:0]       | opcode              |

1 . Opcode (7 bits): This field specifies the operation to be performed. Different opcodes correspond to different operations such as arithmetic, logical, or memory-related operations.

2 . Immediate (5 bits): This field holds a 5-bit immediate value. In the "s" type instruction, this immediate value is used to specify an offset that is added to the base address stored in one of the registers to calculate the memory address where the data will be stored.

3 . Source Register (5 bits): This field specifies the source register containing the data to be stored in memory. The contents of this register are used as the value to be stored.

4 . Destination Register (5 bits): This field specifies the destination register. However, in "s" type instructions, this field is not used for storing the result of the operation. Instead, it holds the base address that is used in conjunction with the immediate value to calculate the memory address where the data will be stored.

5 . Funct3 (3 bits): This field, along with the opcode, further specifies the exact operation to be performed. For "s" type instructions, the funct3 field typically indicates the size and type of memory operation (e.g., byte, half-word, word) to be performed.

6 . Funct7 (7 bits): This field is not used in "s" type instructions.
