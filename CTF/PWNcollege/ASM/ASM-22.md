# Level 22


## Explanation of Assembly Code

The provided assembly code implements a function `str_lower(src_addr)` that processes a null-terminated string located in memory. It iterates through the string, converting uppercase letters to lowercase letters using the function `foo`, and counts the number of converted characters. Let's break down each part of the code:

```assembly
int3            ; Debug breakpoint
mov rax, 0      ; Initialize rax to 0
cmp rdi, 0      ; Compare rdi (src_addr) with 0
je done         ; If src_addr is 0, jump to 'done'

loop:
    mov rbx, 0   ; Initialize rbx to 0
    mov bl, [rdi] ; Load the byte at memory address rdi into bl
    cmp bl, 0    ; Compare the byte with 0
    je done      ; If the byte is 0, jump to 'done'
    
    cmp bl, 0x5a ; Compare the byte with 0x5a (ASCII for 'Z')
    jg greater   ; If byte is greater than 0x5a, jump to 'greater' label

    push rdi     ; Push src_addr onto the stack
    push rax     ; Push rax onto the stack
    mov rdi, 0   ; Clear rdi (for foo argument)
    mov dil, bl  ; Move the byte value to dil (lower 8 bits of rdi)
    mov r10, 0x403000 ; Store the address of function foo in r10
    call r10     ; Call the foo function with the argument in dil
    mov bl, al   ; Store the result (lower 8 bits of rax) back into bl
    pop rax      ; Restore rax from the stack
    pop rdi      ; Restore src_addr from the stack
    mov [rdi], bl ; Store the modified byte back into memory
    add rax, 1   ; Increment rax (counter) by 1

    jmp loop     ; Jump back to the beginning of the loop

greater:
    add rdi, 1   ; Move to the next byte in memory
    jmp loop     ; Jump back to the beginning of the loop

done:
    int3          ; Debug breakpoint
    ret           ; Return from the function
```

# Code Explanation

```assembly
int3            ; Debug breakpoint
```
- This line sets a debug breakpoint. It's used for debugging purposes, allowing you to halt the execution and examine the program's state.

```assembly
mov rax, 0      ; Initialize rax to 0
```
- Sets the value of the `rax` register to 0.

```assembly
cmp rdi, 0      ; Compare rdi (src_addr) with 0
je done         ; If src_addr is 0, jump to 'done'
```
- Compares the value in the `rdi` register (src_addr) with 0. If `rdi` is 0, it jumps to the `done` label, indicating the end of the string.

```assembly
loop:
```
- Marks the beginning of a loop named `loop`.

```assembly
    mov rbx, 0   ; Initialize rbx to 0
    mov bl, [rdi] ; Load the byte at memory address rdi into bl
```
- Initializes the `rbx` register to 0 and loads the byte from the memory address pointed to by `rdi` into the lower 8 bits of the `rbx` register (`bl`).

```assembly
    cmp bl, 0    ; Compare the byte with 0
    je done      ; If the byte is 0, jump to 'done'
```
- Compares the value in `bl` (the loaded byte) with 0. If it's 0, the code jumps to the `done` label, indicating the end of the string.

```assembly
    cmp bl, 0x5a ; Compare the byte with 0x5a (ASCII for 'Z')
    jg greater   ; If byte is greater than 0x5a, jump to 'greater' label
```
- Compares the value in `bl` (the loaded byte) with 0x5a ('Z' in ASCII). If the byte is greater than 0x5a (i.e., it's an uppercase letter), the code jumps to the `greater` label.

```assembly
    push rdi     ; Push src_addr onto the stack
    push rax     ; Push rax onto the stack
```
- Pushes the current values of `rdi` and `rax` registers onto the stack to preserve them.

```assembly
    mov rdi, 0   ; Clear rdi (for foo argument)
    mov dil, bl  ; Move the byte value to dil (lower 8 bits of rdi)
    mov r10, 0x403000 ; Store the address of function foo in r10
    call r10     ; Call the foo function with the argument in dil
    mov bl, al   ; Store the result (lower 8 bits of rax) back into bl
    pop rax      ; Restore rax from the stack
    pop rdi      ; Restore src_addr from the stack
    mov [rdi], bl ; Store the modified byte back into memory
    add rax, 1   ; Increment rax (counter) by 1
```
- Prepares for calling the `foo` function by clearing `rdi`, setting up the argument for `foo`, calling `foo`, and then storing the result back into memory. It also increments the `rax` register (counter) to keep track of the number of converted characters.



```assembly
    jmp loop     ; Jump back to the beginning of the loop
```
- Jumps back to the beginning of the loop to process the next byte in the string.

```assembly
greater:
```
- Marks the `greater` label, which is used when the byte is greater than 'Z'.

```assembly
    add rdi, 1   ; Move to the next byte in memory
    jmp loop     ; Jump back to the beginning of the loop
```
- If the byte is greater than 'Z', this code moves to the next byte in memory and then jumps back to the beginning of the loop.

```assembly
done:
    int3          ; Debug breakpoint
    ret           ; Return from the function
```
- The code reaches the `done` label when the end of the string is encountered. It sets another debug breakpoint and then returns from the function.

This code defines a function `str_lower(src_addr)` that iterates through a null-terminated string, converts uppercase letters to lowercase using the `foo` function, and counts the number of converted characters.

Please note that the `foo` function is assumed to be defined at address `0x403000` and is used to perform the actual conversion of uppercase letters to lowercase. The specifics of the `foo` function are not provided in this code snippet.

Explanation:

    Debug Breakpoint (int3): This sets a debug breakpoint for debugging purposes, allowing you to halt the execution and inspect the program's state.

    Initialize rax and Check rdi: Set the value of the rax register to 0 and compare the value in rdi (src_addr) with 0. If rdi is 0, it jumps to the done label, indicating the end of the string.

    Loop Structure (loop): The beginning of a loop. Continues until a zero byte is encountered.

    Load Byte: Loads the byte from the memory address pointed to by rdi into the lower 8 bits of the rbx register (bl).

    Check Byte and Jump: Compares the value in bl (loaded byte) with 0. If it's 0, jumps to the done label, indicating the end of the string.

    Compare and Call Function (foo): Compares the loaded byte with 0x5a ('Z' in ASCII). If it's less than or equal to 0x5a, it calls the foo function to convert the uppercase letter to lowercase and increments the counter (rax).

    Restore and Store: Prepares for calling the foo function by clearing rdi, setting up the argument for foo, calling foo, and then stores the result back into memory. Also increments the counter (rax).

    Jump Back to Loop (loop): Jumps back to the beginning of the loop to process the next byte in the string.

    Check Greater and Jump: If the loaded byte is greater than 'Z', moves to the next byte in memory and then jumps back to the beginning of the loop.

    Loop Termination (done): When the end of the string is encountered, reaches the done label and executes the debug breakpoint.

    Return (ret): The ret instruction returns from the function.

Summary:

The provided assembly code defines a function str_lower(src_addr) that iterates through a null-terminated string located in memory, converts uppercase letters to lowercase using the foo function, and counts the number of converted characters. The function uses control flow manipulation, the call instruction to call foo, and the stack to preserve and restore registers. The code performs the following steps:

    Initializes counters and checks if src_addr is 0.
    Loops through the string, processing each character.
    Converts uppercase characters to lowercase using the foo function.
    Counts the number of converted characters.
    Returns the count.

The flag pwn.college{I71rdYxLz3dUdXcGNhGJhWKSrOP.0VNxIDLxUjNyEzW} indicates the successful completion of the level.

