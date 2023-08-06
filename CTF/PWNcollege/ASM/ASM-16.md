# level 16


To calculate the average of 4 consecutive quad words stored on the stack without using `pop`, we can directly access the stack using the stack pointer `rsp`.

```

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

## Flag

pwn.college{YC7I5t3aLCjlY6O-ogHyALF60X1.0VOwIDLxUjNyEzW}
```

This solution directly accesses the stack using the stack pointer `rsp` and performs arithmetic operations to calculate the average of the quad words without using the `pop` instruction.
