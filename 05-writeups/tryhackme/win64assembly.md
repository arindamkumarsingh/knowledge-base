# Prerequistes

Decimal = suffix by ' d '.
Binary = prefix by ' 0b ' and suffix by ' b '.
Hexadecimal = prefix by ' 0x ' and suffix by ' h '.

### offsets

Data positions are referenced by how far away they are from the address of the first byte of data, known as the base address (or just the address), of the variable. The distance a piece of data is from its base address is considered the offset. For example, let's say we have some data, 12345678. Just to push the point, let's also say each number is 2 bytes. With this information, 1 is at offset 0x0, 2 is at offset 0x2, 3 is at offset 0x4, 4 is at offset 0x6, and so on.

# Registers

Mainly two different syntaxes for assembly: Intel and AT&T. In linux AT&T is more commonly used.

Compilers main work is to translate high level code into something which CPU can understand which is assembly language. <mark>We may not have source code for the high level program but can get the assembly language from the executable.</mark>

```c
if(x == 4){
    func1();
}else{
    return;
}
```

to

```
mov RAX, x
cmp RAX, 4
jne 5       ; Line 5 (ret)
call func1
ret
```

here the variable is stored in RAX, like a variable in assembly, compare that with 4. Then RAX(4) and 5 if not equal then jump(jne) to line 5 which is return, otherwise if equal then call func1.

## GPR

General purpose registers, can be considered as variables, the cpu has its own storage which is extremely fast but if a data is too big to handle then it is transfered to memory(RAM) which is slow compared to registers, so with this the CPU tries to store its values in registers rather than RAM, if data is big then the register stores a pointer of the data which can be accessed later on.

1. RAX - accumulator register, store the return value of the function.
2. RBX - base register, can be used as base pointer for memory access.
3. RDX - data register
4. RCX - counter register. used for loop counter.
5. RSI - source index, source pointer in string operations.
6. RDI - Destination index, destination pointer in string operations.
7. RSP - Stack pointer, holds address of top of the stack.
8. RBP - base pointer, holds address of the bottom of the stack

These registers are basically used for storing while it can be used for doing anything, but while programming we should have some fixed constraints where the values has been stored or smth.

The most important of all registers is the RIP( instruction pointer ), address of the next line of the code is stored here.

RAX - 64 bits, EAX - 32 bits, AX - 16 bits, AH - 8 bits and AL - 8 bits.

RAX will consist 0-7(8 bytes), EAX will contain (4-7) and AX will contain (6-7), AH contain byte 6 and AL contain  byte 7

Eg. 0x0123456789ABCDEF 

RAX will contain the full, EAX will contain 0x89ABCDEF, AX - 0xCDEF, AH - 0xCD, AL - 0xEF.

Funny, E stands for Extended and R stands for registers, and R was newly introduced so we wont find them in 32-bit systems, but for 64 bit system.

### Different data types

As floating point numbers and integers are different, so these must be stored in different registers. YMM0 to YMM15(64 bit) and XMM0 to XMM15(32-bit), XMM are the lower part of the YMM registers, can be used as array, YMM# registers store 256 bits 4 64-bit and 8 32-bit.

# Instructions

1. immediate value(immediate or IM) - like a constant value.
2. Register - referring to (RAX, AL etc.)
3. Memory address - location in memory.

Semi-colon is used to write comments in Assembly.

(Instruction/Opcode/Mnemonic) (Destination Operand), (Source Operand).

```assembly
mov RAX, 5
```

mov is instruction, RAX is the destination, 5 is source. here 5 is immediate value, no specific capitals or smalls required for keywords.

## Common Instructions

LEA - load effective address stores the address rather than the value of the variable.

```
lea RAX, 5
```

```
lea RAX, [struct+8]
```

```
mov RBX, 5
lea RAX, [RBX + 1]
```

in 3rd rax becomes 6, as lea takes the address for RBX takes the value and adds plus one in the address.

`push` is used to stack on the top of it. its often used for storing data in register and then later restoring it by popping.

`pop` takes out the value which is on top. and stored in the destination.

`inc` increases the value by 1, `dec` decreases the value by 1.

`add` takes the source and adds it to the destination and stores in the destination operand.

```
mov RAX, 2
mov RBX, 3
add RAX, RBX
```

here the destination is RAX and source is RBX.

Similiar case is for subtraction.

