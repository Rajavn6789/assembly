## 64 bit Architecture

Since the 64-bit registers allow access for many sizes and locations, we define a byte as 8 bits, a word as 16 bits, a double word as 32 bits, a quadword as 64 bits, and a double quadword as 128 bits. Intel stores bytes "little endian," meaning lower significant bytes are stored in lower memory addresses.

![](https://software.intel.com/sites/default/files/m/7/5/0/2/0/29529-figure-1.jpg)
Source: [Intel](https://software.intel.com/en-us/articles/introduction-to-x64-assembly)
### a) Registers
Registers are part of processors that hold 64 bits of data. It can hold values ranging from 0 - 2^64.

1. rax - register a extended(accumulator)
2. rbx -  register b extended(base)
3. rcx - register c extended(count)
4. rdx - register d extended
5. rbp -  register base pointer (contains address of base of current stack)
6. rsp -  register stack pointer (contains address of top of current stack frame)
7. rsi - register source index (source for data copies)
8. rdi - register destination index (destination for data copies)
9. r8 - register 8
10. r9 - register 9
11. r10 - register 10
12. r11 - register 11
13. r12 - register 12
14. r13 - register 13
15. r14 - register 14
16. r15 - register 15

Note
The different portion of the bits in 64 bit in the register can be accessed by the following
a) rax
1. eax - Lower 32 bits
2. ax - Lower 16 bits
3. al - lower 8 bits

b) r8
1. r8d - Lower 32 bits
2. r8w - Lower 16 bits
3. r8b - lower 8 bits

### b) Flags
Flag can also hold data (only one bit of data true or false)

1. Carry Flag (CF)
2. Parity Flag (PF)
3. Zero Flag (ZF)
4. Sign Flag(SF)
5. Overflow Flag(OF)
6. Adjust Flag(AF)
7. Interrupt Enabled(IE)
8. DF - Direction flag
9. OF - Overflow flag

### c) Pointers
Pointers are also registers that holds data. They hold "point to" data, meaning they hold memory address.

1. Index pointer(rip) - Points the next address to be executed in the control flow
2. Stack Pointer(rsp) - Points to the top of address stack
3. Stack Base Pointer (rbp) - Points to the bottom of the address stack
.....

##### i) Registers As pointers
  To treat register as pointer, rax becomes [rax]
```asm
  mov rax, rbx ;Loads the value of rbx into the rax
  mov rax, [rbx] ;Loads the value of rbx pointing to into the rbx
```

### d) Control flow
All program runs from top to bottom
rip - instruction pointer, holds the address of the next instruction to be executed
```asm
_start:
    mov       rax, 1  ; rip = x
    mov       rdi, 1  ; rip = x + 1
    mov       rsi, msg ; rip = x + 2
    mov       rdx, 11 ; rip = x + 3
    syscall ; rip = x + 4
```

#### i) Comparisons
 Comparisons allow program to take different path based on certain conditions, after making comparisons certain flags are section
 for eg a = b ZF is set to 1, a != b ZF is set to 0

```asm
  cmp rax, 23 ;compares value of rax with 23
  cmp rax, rbx ; compares value of rax with the value stored in rbx
```

#### ii) Conditional jumps
  Conditional jumps can be made after comparison.
```asm
  cmp rax, 23
  je _doThis ; equals

  cmp rax, rbx
  je _doThat ; greater
```

#### iii) Call
 Call is also a type of jump, where it jumps to a subroutine and returns to the previous execution once the subroutine execution is complete.
 ```asm
 _start:
     call _exitTerminal ; calls subroutine

 _exitTerminal:
     mov       rax, 60
     mov       rdi, 1
     syscall
     ret     
 ```

## References
1. [How to Computers read code?](https://www.youtube.com/watch?v=QXjU9qTsYCc&t=431s)
2. [x86 Assembly Crash Course](https://www.youtube.com/watch?v=75gBFiFtAb8&t=332s)
3. [Kupala](https://www.youtube.com/playlist?list=PLetF-YjXm-sCH6FrTz4AQhfH6INDQvQSn) and  4. [senecacollege](https://wiki.cdot.senecacollege.ca/wiki/X86_64_Register_and_Instruction_Quick_Start)
