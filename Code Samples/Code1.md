```assembly
section .data
    ; initialize variables
    x dd 0
    y dd 10
    z dd 5

section .text
    global _start

_start:
    ; load values into registers
    mov eax, [x]
    mov ebx, [y]
    mov ecx, [z]

    ; for loop
    for_loop:
        add eax, ebx ; add y to x
        sub eax, ecx ; subtract z from x
        dec ecx ; decrement z
        jnz for_loop ; if z is not zero, jump to for_loop

    ; store result in x
    mov [x], eax

    ; exit program
    mov eax, 1
    xor ebx, ebx
    int 0x80
```
