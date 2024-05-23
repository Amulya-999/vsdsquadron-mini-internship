# vsdsquadron-mini-internship

## TASK-1
### Task is to install RISC-V toolchain and refer to C based and RISC-V based videos and to compile the c program using gcc and RISC-V simulator


## C LANGUAGE BASED LAB
#### After installing the RISC-V toolchain , the task is to compile a C program which calculates the sum of numbers from 1 to n using GCC Compiler.
#### The command 'leafpad sum1ton.c &' is used to open a text editor called Leafpad with the file name sum1ton.c for editing in which the c program to find the sum of numbers from 1 to n is written.
#### The command 'gcc sum1ton.c' is used to compile the C program which is in file sum1ton.c  into an executable program
#### The command './a.out' is used to execute the compiled program.
#### as  the code is written to find the sum of numbers from 1 to 5,by following the above commands this code is compiled and output is produced as 15.


![VirtualBox_vsdworkshop_23_05_2024_17_44_22](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/deb28ef8-428b-4f8a-8ae4-c5b42a1e821d)



## RISC-V BASED LAB
#### now,the task is to compile the same C program using RISC-V simulator
#### 1.we use the command 'cat sum1ton.c' to view the code on the terminal
#### 2.To compile the code we use the command 'riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c'
#### here, -mabi=lp64 flag in the RISC-V compiler command specifies the ABI (Application Binary Interface) and the data model for our compiled program
#### '-mabi': This flag specifies the ABI to use.
#### 'lp64': This part defines the data model used for the ABI.
#### RISC-V supports different ABIs depending on the specific requirements of our application.so,'lp64'denotes the long integer pointer that is it signifies that pointers are 64 bit wide.
#### -o is the currently using option
#### sum1ton.o is the output file
#### sum1ton.c is the input file
#### then it generates a file sum1ton.c

![1](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/fbaa359a-49a4-474c-a2a4-40792fce564e)

#### next step is to open a new tab terminal and see the assembly code for c code and command to see the assembly code of c code iS 'riscv64-unknown-elf-objdump -d sum1ton.o'
#### 'objdump': This is the specific command within the toolchain used to disassemble object files
#### this gives bunch of assembly codes,to reduce the code we use the command 'riscv64-unknown-elf-objdump -d sum1ton.o | less'

![2](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/732c1d66-59d5-4199-aca3-331e1ea4e693)

we get a huge section of code but we are interested in main section of the code so type '/main'

![3](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/7b016ed8-493a-4247-b1bc-6d70b9fc9541)

#### now,press n we get the main section with its address 

![4](https://github.com/Amulya-999/vsdsquadron-mini-internship/assets/170462957/f41828e6-cebf-4651-b5c4-ea3ad1b18fd2)

#### so we see that there are 35 instructions in main section
#### now we repeat the same from the starting by using option ofast
