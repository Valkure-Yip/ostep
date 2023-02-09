[TOC]

## Concurrency

**thread**: like process, but share the same address space with other threads, can access the same data 

a **multi-threaded** program has more than one point of execution (i.e., multiple PCs, each of which is being fetched and executed from)

**context-switch**: switching from running one thread (T1) to running the other (T2), register state of T1 must be saved to **thread control blocks (TCBs)** and the register state of T2 restored before running T2.

 In a multi-threaded process, each thread runs independently, and has **one stack per thread**: **thread-local storage**

Reasons for multi-thread: **parallel** with multiple processor, **avoid I/O block**