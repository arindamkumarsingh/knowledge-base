# Intro

first mass produced cpu was intel 4004 by federico faggin. 4 bit architecture instead of 64 bit systems,

instructions that cpu executes are binary data, a byte here and there to represent what instruction is being run followed by the data.

Machine code is just binary instructions in a row. Assembly is a syntax useful for understanding and writing machine code.

```
add eax, 512

translates to

05 00 02 00 00 
```

here 05 is an opcode , represents adding EAX register to a 32 bit number.

CPU reads machine code directly from the RAM, and wont run if its not loaded into the ram.

CPU stores an instruction pointer which points to the location in RAM to fetch the next instruction, when the instruction is completed it moves on and the cycle repeats. This is known as fetch-execute cycle.

Some instruction can tell the pointer to jump somewhere else, makes the code reusable and logically possible.

The instruction pointer is stored in a **register**. Small storage buckets extremely fast for  cpu to read or write. each cpu architecture has fixed set of register, used for storing temp values to config the processor.

some registers are directly accessible like `ebx`, others are used internally by cpu.

## Processors

The machine code loads into ram and instructs the cpu to jump the instruction pointer to the ram. The fetch and execute cycle runs pretty fast so the program begins executing.

A CPU is shockingly primitive - 

1. it only knows instruction pointer(IP)

2. registers

3. Flags

But we have currently multiple programs running in your computers, it feels like they are running simultaneously, but a core executes a single instruction at a time as it does fetch and execute.

So what it does is context switching.

Each program has process context which has register vals, IPs etc

So it saves the current cpu state of program A, and loads the saved state of program B. CPU resumes executing from B's execution pointer. But for cpu nothing has changed, it doesnt even know program A or B exists, just loads register vals.

Q. If programs run directly from cpu and cpu directly access the RAM, then why can it directly access the memory of other programs running or the kernel.

There must be mechanism that can prevent processes from running any instruction they want.

### Kernel

When computer is booted, the instruction pointer sshould point or start at somewhere so that program is kernel. This has almost full acess to comp memory and runs the software in computer which helps it to run effectively(**Userland programs**). 

> Linux is a kernel, and userland softwares like shells(bash,zsh). macOS --> XNU and Windows Kernel -->  NT kernel.

MOdern archs have two options:- Kernel/supervisor mode and user mode.  

In kernel mode almost anything is possible and execute any instruction and access any memory. In user mode, limited memory and I/O access.

All drivers run in kernel mode and applications run in user mode.

Processors start in kernel mode and switches to user mode. 

#### aRch

**x86-64 arch** - privileges is encode in rings(0-3) but ring 0 and ring 3 is only used. ring 0 = kernel, ring 3 = user

represent in binary form the last two bits from **cs - code segment register**. 

**CPL** = Current Privilege level are the lowest 2 bits of cs.

### Syscall

A procedure that lets a program transition from user mode to kernel space, jumping from programs code into OS Code.

This is done using a feature called software interrupts.