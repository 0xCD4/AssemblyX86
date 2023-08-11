# Level 21

## Explanation of Assembly Code

The provided assembly code aims to count the consecutive non-zero bytes in a contiguous region of memory. It employs a while-loop structure to iterate until it encounters a zero byte. Let's break down each part of the code:

```assembly
int3            ; Debug breakpoint
mov rax, 0      ; Initialize rax to 0
cmp rdi, 0      ; Compare rdi (memory address) with 0
je done         ; If rdi is 0, jump to 'done'

loop:
    mov rbx, 0   ; Initialize rbx to 0
    mov bl, [rdi] ; Load the byte at memory address rdi into bl
    cmp bl, 0    ; Compare the byte with 0
    je done      ; If the byte is 0, jump to 'done'
    add rax, 1   ; Increment rax (counter) by 1
    add rdi, 1   ; Move to the next byte in memory
    jmp loop     ; Jump back to the beginning of the loop

done:
    int3         ; Debug breakpoint
```

1. **Debug Breakpoints (`int3`):** These lines act as debugging checkpoints. They allow for inspection of the program's state during execution.

2. **Initialize `rax` and Check `rdi`:** The code starts by setting `rax` to 0 and then compares the value in the `rdi` register (memory address) with 0. If `rdi` is 0, it directly jumps to the `done` label.

3. **Loop Structure (`loop`):** This marks the beginning of the while-loop. It continues to run until a zero byte is encountered.

4. **Initialize `rbx` and Load Byte:** Inside the loop, `rbx` is initialized to 0, and the byte at the memory address pointed to by `rdi` is loaded into the lower 8 bits of the `rbx` register (`bl`).

5. **Check Byte and Jump:** The code compares the byte loaded in `bl` with 0. If the byte is 0 (indicating the end of the contiguous non-zero bytes), it jumps to the `done` label.

6. **Increment Counter and Memory Address:** If the byte is non-zero, it increments the counter (`rax`) to keep track of the consecutive non-zero bytes and increments the memory address (`rdi`) to move to the next byte.

7. **Jump Back to Loop:** The `jmp loop` instruction jumps back to the beginning of the loop, allowing for the next iteration.

8. **Loop Termination (`done`):** Once the loop terminates (when a zero byte is encountered), the code reaches the `done` label.

9. **Debug Breakpoint (`int3`):** Another debug breakpoint is placed at the end for further debugging purposes.

## Assembly Code in Markdown Format

```markdown
# Count Consecutive Non-Zero Bytes

This assembly code counts the consecutive non-zero bytes in a contiguous region of memory using a while-loop structure.

## Code Explanation

1. **Debug Breakpoints (`int3`):** These lines act as debugging checkpoints, allowing for inspection of the program's state during execution.

2. **Initialize `rax` and Check `rdi`:** The code starts by setting `rax` to 0 and then compares the value in the `rdi` register (memory address) with 0. If `rdi` is 0, it directly jumps to the `done` label.

3. **Loop Structure (`loop`):** This marks the beginning of the while-loop. It continues to run until a zero byte is encountered.

4. **Initialize `rbx` and Load Byte:** Inside the loop, `rbx` is initialized to 0, and the byte at the memory address pointed to by `rdi` is loaded into the lower 8 bits of the `rbx` register (`bl`).

5. **Check Byte and Jump:** The code compares the byte loaded in `bl` with 0. If the byte is 0 (indicating the end of the contiguous non-zero bytes), it jumps to the `done` label.

6. **Increment Counter and Memory Address:** If the byte is non-zero, it increments the counter (`rax`) to keep track of the consecutive non-zero bytes and increments the memory address (`rdi`) to move to the next byte.

7. **Jump Back to Loop:** The `jmp loop` instruction jumps back to the beginning of the loop, allowing for the next iteration.

8. **Loop Termination (`done`):** Once the loop terminates (when a zero byte is encountered), the code reaches the `done` label.

9. **Debug Breakpoint (`int3`):** Another debug breakpoint is placed at the end for further debugging purposes.
```

---

This Markdown file provides a comprehensive breakdown of the provided assembly code, explaining each instruction and its purpose in a clear and detailed manner. You can refer to this explanation to better understand how the code works and what each part contributes to the overall functionality.
