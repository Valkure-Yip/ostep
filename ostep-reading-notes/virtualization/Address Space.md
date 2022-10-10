# Address Space

when multiple processes are running at the same time (time-sharing): 

<img src="Address Space.assets/image-20221009121057826.png" alt="image-20221009121057826" style="zoom:33%;" />

requires the OS to create an easy to use **abstraction** of physical memory. We call this abstraction the **address space**, and it is the running program’s view of memory in the system. 

a process: code, heap & stack:

<img src="Address Space.assets/image-20221009121552088.png" alt="image-20221009121552088" style="zoom:33%;" />

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

