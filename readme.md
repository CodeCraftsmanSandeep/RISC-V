# 5-stage-RISC-V-pipeline
Hi folks 👋🏻  
In this repository I wrote verilog code to desgin 5 stage 64-bit RISC-V pipeline. 

## Table of contents
| file | description |
|:-----|:------|
| [verlog_code.v](verilog_code.v) | verilog code of 5 stage RISC-V pipeline |
| [test-bench.v](test-bench.v) | test bench to verify the output of the machine code passed as input |
| [project_report.pdf](project_report.pdf) | talks about this project in detail |

## Problem statement
Design a 5 stage RISC-V pipelined data path with the following features <br/>
1) Store data and access data.
2) Perform add, sub, mul, addi arthimetic operations.
3) Apply forwarding logic to decrease number of stalls as much as possible thereby increasing performance.

## Introduction to RISC-V architecture:
RISC-V is an open-source instruction set architecture (ISA) designed for computer processors. It stands for "Reduced Instruction Set Computer - Five." The RISC-V architecture is based on the concept of reduced instruction set computing, which emphasizes simplicity and efficiency by using a smaller set of instructions.
More specifically, RISC-V has been used in cloud computing, servers, and embedded applications.

### Guiding Design principles in RISC-V ISA:
1) Simplicity favours regularity.
2) Smaller is faster.
3) Good design demands good compromises.

## Pipelining:

### What is pipelining?
Pipelining is a technique where multiple sub-tasks of instructions are implemented at the same time. Pipelining allows mutiple sub‐tasks to be carried out simultaneously using independent resources(Instruction level parallelism) <br/>

###  5-stages for implementing instruction(in general):
Similar to MIPS architecture there are 5 stages in RISC-V ISA(Instruction Set Architecture) :
1) IF : Instruction fetch from Instruction cache.
2) ID : Instruction Decode and Register read.
3) EX: Execute Operations[eg: add, sub] (or) Calculate address[ld, sd].
4) MEM: Access memory operands from data cache.
5) WB: Write result back to the register in register file.

### Why pipelining in computer architecture?

Execution time = IC * CPI * T <br/>
IC – Instruction count
CPI – Cycles Per Instruction
T – Clock Period.

In a single cycle processing unit the instructions are going to be executed sequentially one by one. Here CPI (Cycles Per Instruction) is low [for one instruction – one cycle] but here we are going to have a long clock period [the clock period corresponds to slowest instruction]. As a result the execution time is going to increase significantly due to long clock period, which results in less performance. This single cycle processing unit doesn’t have any benefit except its simplicity.

CPI (Cycles Per Instruction): 1 <br/>
Clock period: IF_time + ID_time + EX_time + MEM_time + WB_time
		    (long clock period, critical path: ld instruction) 
```
For further details of the project, please look at project_report.pdf
```
