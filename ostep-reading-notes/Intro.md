# Intro

the book: [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/): 41 chapters (minus dialogue, summary & Security)

codes in book: https://github.com/remzi-arpacidusseau/ostep-code

Homework: https://github.com/remzi-arpacidusseau/ostep-homework/

Project: https://github.com/remzi-arpacidusseau/ostep-projects



**virtualization**: the OS takes a physical resource (such as the processor, or memory, or a disk) and transforms it into a more general, powerful, and easy-to-use virtual form of itself

**virtualizing CPU**: Turning a single CPU (or a small set of them) into a seemingly infinite number of CPUs and thus allowing many programs to seemingly run at once

**virtualizing memory**: Each process accesses its own private virtual address space (sometimes just called its address space), which the OS somehow maps onto the physical memory of the machine.

**concurrency**

**persistence**：store data persistently, file system