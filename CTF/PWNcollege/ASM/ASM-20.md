## Computing the Average of n Consecutive Quad Words

In this challenge, the goal is to compute the average of `n` consecutive quad words stored in memory. The assembly code provided achieves this task by using control flow manipulation instructions. Let's break down the code step by step.

### Initialization

```assembly
int3                 ; Debug breakpoint
mov rax, 0           ; Initialize sum to 0
mov rcx, 0           ; Initialize loop counter to 0
```

- The code starts with a `int3` instruction, which acts as a debug breakpoint, pausing the execution at this point for debugging purposes.
- `rax` is set to 0 to initialize the sum of quad words.
- `rcx` is set to 0 to initialize the loop counter.

### Loop to Calculate Sum

```assembly
loop:
    add rax, [rdi]    ; Add the value at memory address [rdi] to sum
    add rdi, 8        ; Move to the next quad word (increment memory address by 8 bytes)
    inc rcx           ; Increment loop counter by 1
    cmp rcx, rsi      ; Compare loop counter with n (rsi)
    xor rdx, rdx      ; Clear rdx (for division)
    div rsi           ; Divide rax by n (rsi)
```

- The `loop` label defines the start of the loop.
- `add rax, [rdi]` adds the value stored at the memory address in `rdi` to the sum in `rax`.
- `add rdi, 8` increments the memory address in `rdi` by 8 bytes to move to the next quad word.
- `inc rcx` increments the loop counter in `rcx` by 1.
- `cmp rcx, rsi` compares the loop counter with the value of `n` (stored in `rsi`).
- `xor rdx, rdx` clears the `rdx` register in preparation for division.
- `div rsi` divides the contents of the combined `rdx:rax` by the value in `rsi`. The quotient (average) is stored in `rax`.

1. Loop Label (loop): We're entering a loop here. Think of it as a repeated set of instructions.

2. Add to Sum: This instruction takes the value stored at the memory address pointed to by the rdi register and adds it to the current sum stored in the rax register.

3. Move to Next Quad Word: By adding 8 to the rdi register, we're effectively moving to the next quad word in memory. Each quad word is 8 bytes long.

4. Increment Loop Counter: The inc rcx instruction adds 1 to the loop counter in rcx, indicating that we've processed one more quad word.

5. Compare Loop Counter: The cmp rcx, rsi instruction compares the loop counter (rcx) with the value of n (rsi). It checks if we've processed n quad words yet.

6. Prepare for Division: The xor rdx, rdx instruction clears the rdx register. This is necessary before we perform division.

7. Perform Division: The div rsi instruction divides the sum in the rax register by n (stored in rsi). The result – the average – is stored back in the rax register.

### Finalization

```assembly
int3                 ; Debug breakpoint
```

- Another `int3` instruction is placed after the loop for debugging purposes.

---

This assembly code calculates the sum of `n` consecutive quad words stored in memory and then computes the average. The loop iterates `n` times, adding each quad word to the sum, and finally, the sum is divided by `n` to obtain the average. This code snippet demonstrates how control flow manipulation and arithmetic operations are used to achieve the desired computation.

The Flag: pwn.college{MUtVqfc95lO9DzfJ9BkuGIRIZI5.01MxIDLxUjNyEzW}
