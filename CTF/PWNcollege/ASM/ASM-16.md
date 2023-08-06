# level 16


To calculate the average of 4 consecutive quad words stored on the stack without using `pop`, we can directly access the stack using the stack pointer `rsp`.

1. Load the first quad word from the stack into `rax`.
```assembly
add rax, qword ptr [rsp]
```

2. Load the second quad word from the stack into `rax`.
```assembly
add rax, qword ptr [rsp + 8]
```

3. Load the third quad word from the stack into `rax`.
```assembly
add rax, qword ptr [rsp + 0x10]
```

4. Load the fourth quad word from the stack into `rax`.
```assembly
add rax, qword ptr [rsp + 0x18]
```

5. Divide the sum in `rax` by 4 to calculate the average. We will use the `div` instruction with `rbx` set to 4 for the division.
```assembly
mov rbx, 4
div rbx
```

6. Push the calculated average back onto the stack.
```assembly
push rax
```

So, the average of the 4 consecutive quad words will be stored on the top of the stack after this code sequence.

Reminder: 

`qword ptr` is a specifier used in x86 and x86-64 assembly language to indicate the size of a memory operand or immediate value. It stands for "quad word pointer" and is used to denote that the operand or immediate value being accessed is 64 bits (8 bytes) in size, which corresponds to a quad word.

In assembly language, memory operands are often represented using the syntax `[address]`, where `address` is the memory location being accessed. The `qword ptr` specifier is used to indicate that the memory operand is a quad word, and the processor should interpret 8 bytes of data starting from the specified memory address.

Here are some examples of how `qword ptr` is used:

```assembly
; Load the quad word value at memory address 0x404000 into the rax register
mov rax, qword ptr [0x404000]

; Store the value in the rax register into the quad word at memory address 0x404000
mov qword ptr [0x404000], rax

; Add the quad word value at memory address stored in rdi to the value in the rax register
add rax, qword ptr [rdi]
```

By using `qword ptr`, the assembler knows that it needs to generate machine code instructions that operate on 64-bit data when dealing with memory operands. This ensures that the correct number of bytes is read or written to memory when performing operations on quad words.

## Flag

pwn.college{YC7I5t3aLCjlY6O-ogHyALF60X1.0VOwIDLxUjNyEzW}
```

This solution directly accesses the stack using the stack pointer `rsp` and performs arithmetic operations to calculate the average of the quad words without using the `pop` instruction.
