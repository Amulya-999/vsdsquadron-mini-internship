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
#### we use the command 'cat sum1ton.c' to view the code on the terminal
#### to compile the code we use the command 
#### 'riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c'
#### here, -mabi=lp64 flag in the RISC-V compiler command specifies the ABI (Application Binary Interface) and the data model for our compiled program
#### '-mabi': This flag specifies the ABI to use.
#### 'lp64': This part defines the data model used for the ABI.
#### RISC-V supports different ABIs depending on the specific requirements of our application.so,'lp64'denotes the long integer pointer that is it signifies that pointers are 64 bit wide.
#### then it generates a file sum1ton.c

