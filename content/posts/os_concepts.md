---
draft: true
title: 'OS Concepts'
---

## Introduction
OS also known as Operating System is a software which is used to control and allocate hardware and software resources efficiently. Most of the operating systems are written using C and C++. The kernal of the Operating System is mostly written in C.

The kernals of the OS's are wrtten in C language because C allows you to access memory via poiters unlike other programming languages which hides memory access. C language allows you to directly manipulate hardware registers and memory addresses which makes it ideal to write memory managers and drivers. C language also compiles to machine code before runtime which makes it fast compared to other programming languages and it also allows inline assembly code which is sutable for CPU instructions.

OS is a low level software which acts as a government which has various departments with all absic functions such as process management,memory management,file management, networking, UI, backup & recovery, system calls etc...

## Types of OS:-
There are ten types of OS,
1. Batch OS
2. Time sharing OS
3. Distributed OS
4. Network OS
5. Single-user OS
6. Multi-user OS
7. Cluster OS
8. Embedded OS
9. Multiprocessing OS
10. Real-time OS

### Batch OS:-
It interacts with an operator which groups similar jobs into batches. it does not interact with computer directly.

Example:-  
![Batch OS](https://media.geeksforgeeks.org/wp-content/uploads/20221020142659/Batchoperatingsystem2-660x330.png)

>**Note**: The image is taken from geeksforgeeks.

### Time sharing OS:-
It allows many users to share computer resources utilizing the computer resources to the maximum.

Example:-  
![Time OS](https://media.geeksforgeeks.org/wp-content/uploads/20200524180155/Capture2210.png)

>**Note**: The image is taken from geeksforgeeks.

### Distributed OS:-
It manages a group of computers working as a single computer allowing multiple users to access shared resources and communicate with each other over the network

Example:-  
![Distributed OS](https://media.geeksforgeeks.org/wp-content/uploads/20240422135717/Working-of-Distributed-System.webp)

>**Note**: The image is taken from geeksforgeeks.


### Network OS:-
It runs on a server and provides the capability to manage data, users, groups, security, applications, and other networking functions.

Example:-  
![Network OS](https://www.techtarget.com/rms/onlineimages/network_operating_system_model-f.png)

>**Note**: The image is taken from techtarget.

### Single-user OS:-
It supports single user at a time.

Example:-  
![Single-user OS](https://media.geeksforgeeks.org/wp-content/uploads/20221017113742/Singleuseroperatingsystem.png)

>**Note**: The image is taken from geeksforgeeks.

### Multi-user OS:-
It is designed to support multiple users at a time.

Example:-  
![Multi-user OS](https://media.geeksforgeeks.org/wp-content/uploads/20221018162540/Multiuseroperatingsystem.png)

>**Note**: The image is taken from geeksforgeeks.

### Cluster OS:-
It runs on group of computers, or a cluster, to work together as a single system. They are used for high-performance computing and for applications that require high availability and reliability.

Example:-  
![Cluster OS](https://media.geeksforgeeks.org/wp-content/uploads/20210313225739/UntitledDiagram4.png)

>**Note**: The image is taken from geeksforgeeks.

### Embedded OS:-
It runs on devices with limited resources, such as smartphones, wearable devices, and household appliances.

Example:-  
![Embedded OS](https://media.geeksforgeeks.org/wp-content/uploads/20200803021221/Untitled-Diagram-185-1.png)

>**Note**: The image is taken from geeksforgeeks.

### Multiprocessing OS:-
It is used in operating systems to boost the performance of multiple CPUs within a single computer system. Multiple CPUs are linked together so that a job can be divided and executed more quickly.

Example:-  
![Multiprocess OS](https://media.geeksforgeeks.org/wp-content/uploads/Untitled-drawing-24.png)

>**Note**: The image is taken from geeksforgeeks.

### Real-time OS:-
It serves a real time system with very small time interval to process and respond to inputs.

Example:-  
![Real-time OS](https://www.researchgate.net/publication/319471019/figure/fig3/AS:779403747405849@1562835742475/Structure-of-real-time-operating-system.gif)

>**Note**: The image is taken from researchgate.

## Process Management:- 
Process management is easy for single process or batch process because it only has one process but multiple processes require efficient use of CPU. since multiple process may share resources process synchronization is required without an option.

### CPU bound processes:-
It requires more CPU time or spends more time in running state

### I/O bound processes:-
It requires more I/O time and less CPU time or spends more time in waiting state

## Process management:-
1. Process creation - involves creating a process ID and setting up process control block
2. CPU scheduling - OS assigns CPU to multiple process to ensure smooth and efficient execution
3. Deadlock handling - to make sure the system does not reach a state where process cannot process due to dependency
4. Inter process communication - OS provides facilities such as shared memory and messaging to help process communicate with each other
5. Process synchronization - it is the execution of multiple process in co-ordination in a controlled and predicatable manner
6. Termination - involves clearing all resources

## Process Operations:-
![Real-time OS](https://media.geeksforgeeks.org/wp-content/uploads/20240709113806/Screenshot-2024-07-09-113355.png)

>**Note**: The image is taken from geeksforgeeks.

1. Process creation - process is an instance of a program which can execute independently
2. scheduling - process enters ready queue when it is ready to run and execution starts when scheduler picks it up
3. Execution - CPU starts working on the process. it might reach waiting queue or blocked depending on the priority
4. Killing the process - once the process finishes OS removes its `Process Control Block(PCB)`

## Context switching:-
It is the process of saving the context of one process and loading the context of another process. it happens when a `high priority task` appears, `process interrupts`, `user` and `kernal` mode switches or `CPU scheduling` is used

## Mode switch:-
It occurs when CPU privelage level is changed.The currently executing process need not be changed during a mode switch.Only the `kernel` can cause a context switch. 

## Process scheduling algorithms:-
Some commonly used algorithms are,
1. First Come First Serve(FCFS) - simplest scheduling algorithm works on first come first serve basis and is non preemptive(once it starts, it continues till it is finished)
2. Shortest Job First(SJF) - selects process which takes shortest time to complete and minimizes average waiting time of process
3. Round Robin(RR) - reserves fixed amount of time in a round for each process. if the process is not completed within time it is blocked and added to end of queue. it ensures fair distribution and avoids starvation 
4. Priority Scheduling - assigns priority to each process and the process with highest priority executes first and it can be set based on process type,importance or resource requirements
5. Multilevel queue - divides ready queue into several queues with diffenrent priority and processes based on priority with different sheduling methods for each queue

## Process Control Block(PCB):-
he Process Table is an array of PCBs, which logically contains a PCB for all of the current processes in the system.A Process Control Block (PCB) is a data structure used by the operating system to manage information about a process.The Process Control Block (PCB) is stored in a special part of memory that normal users can't access. This is because it holds important information about the process. Some operating systems place the PCB at the start of the kernel stack for the process, as this is a safe and secure spot.
![Real-time OS](https://media.geeksforgeeks.org/wp-content/uploads/20241122132710403798/process---------control---------block.webp)

>**Note**: The image is taken from geeksforgeeks.

1. Pointer - it is a stack pointer which retains current position of the process
2. Process state - stores respective state
3. Process number - every process is assigned a unique ID called ProcessID(PID)
4. Program counter - contains the address of the next instruction to execute for the process
5. Register - It is a data structure which stores process specific registers in PCB as a form of state data
6. Memory limit - contains memory management info used by OS
7. List of open files - includes list of files opened for process

