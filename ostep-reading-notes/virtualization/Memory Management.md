## Address Space

when multiple processes are running at the same time (time-sharing): 

<img src="Memory Management.assets/image-20221009121057826.png" alt="image-20221009121057826" style="zoom:33%;" />

requires the OS to create an easy to use **abstraction** of physical memory. We call this abstraction the **address space**, and it is the running program’s view of memory in the system. 

a process: code, heap & stack:

<img src="Memory Management.assets/image-20221009121552088.png" alt="image-20221009121552088" style="zoom:33%;" />
**stack** to keep track of where it is in the function call chain, allocate local variables, pass parameters and return values to and from routines.
**heap** is used for dynamically-allocated, user-managed memory, such as that you might receive from a call to malloc() in C or new in an objectoriented language such as C++ or Java. 

The program really isn’t in memory at physical addresses 0 through 16KB; rather it is loaded at some arbitrary physical address(es). 

Goal of Virtual Memory (VM):
- invisible to process
- time & space efficient
- memory protection 

## memory API

**stack memory**： function scope, short-lived, automatic manage by compiler

```c++
void func() {
int x; // declares an integer on the stack
...
}
```



**heap memory**: long-lived, allocations and deallocations are explicitly handled the programmer
allocate heap mem in C: `malloc(size_t size)`

```c++
void func() {
int *x = (int *) malloc(sizeof(int));
...
}
```

free memory: `free()`

```c++
int *x = malloc(10 * sizeof(int));
...
free(x);
```



## Address Translation

 the hardware transforms each memory access (e.g., an instruction fetch, load, or store), changing the **virtual address** provided by the instruction to a **physical address** where the desired information is actually located. 

e.g. consider this function:
```c
void func() {
int x = 3000; // thanks, Perry.
x = x + 3; // line of code we are interested in
```

```assembly
128: movl 0x0(%ebx), %eax ;load 0+ebx into eax
132: addl $0x03, %eax ;add 3 to eax register
135: movl %eax, 0x0(%ebx) ;store eax back to mem
```

process address space：
<img src="Memory Management.assets/image-20230118142614559.png" alt="image-20230118142614559" style="zoom: 33%;" />

in physical memory:
<img src="Memory Management.assets/image-20230118121227185.png" alt="image-20230118121227185" style="zoom: 33%;" />

> Address translation: make the program feels that it has its own memory starting from addr 0

### Dynamic (Hardware-based) Relocation

**base and bounds: memory management unit**

Base and bound registers hardcoded on chips

physical address = virtual address + **base** (32KB for e.g. in Fig 15.2)

If a process generates a virtual address that is greater than the **bounds** (16KB for e.g. in Fig 15.2), or one that is negative, the CPU will raise an exception

e.g.
```assembly
128: movl 0x0(%ebx), %eax 
```
The program counter (PC) is set to 128; when the hardware needs to fetch this instruction, it first adds the value to the base register value of 32 KB (32768) to get a physical address of 32896;

**hardware needs to**
![image-20230118143858091](Memory Management.assets/image-20230118143858091.png)

**OS needs to**
![image-20230118143923523](Memory Management.assets/image-20230118143923523.png)
