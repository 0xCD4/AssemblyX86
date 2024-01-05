# Assembly While Loop Example

In this example, we will explore a simple while loop in x86 assembly language. The purpose of the code is to demonstrate a basic loop structure using conditional jumps.

```assembly
section .data
    ; Data section (not used in this example)

section .text
    global _start

_start:
    ; Initialize a counter
    mov ecx, 0

while_loop:
    ; Compare the counter with a threshold (e.g., 5)
    cmp ecx, 5
    jge end_loop  ; Jump to end_loop if counter >= 5

    ; Body of the loop: Print the counter value
    ; (You can replace this part with your specific logic)
    mov eax, 4            ; syscall number for sys_write
    mov ebx, 1            ; file descriptor 1 is stdout
    mov edx, ecx          ; counter value
    add dl, '0'           ; convert counter value to ASCII
    mov ecx, 1            ; length of the character to print
    int 0x80              ; call kernel

    ; Increment the counter
    inc ecx

    ; Jump back to the beginning of the loop
    jmp while_loop

end_loop:
    ; Exit the program
    mov eax, 1            ; syscall number for sys_exit
    xor ebx, ebx          ; exit code 0
    int 0x80              ; call kernel
