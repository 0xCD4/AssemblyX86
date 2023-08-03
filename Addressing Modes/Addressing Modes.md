### 1. Immediate Addressing Mode

```assembly
section .text
    global _start

_start:
    ; Load the immediate value 10 into EAX
    mov eax, 10

    ; Add the immediate value 20 to EAX
    add eax, 20

    ; Subtract the immediate value 5 from EAX
    sub eax, 5

    ; Store the immediate value 42 into the 'num' variable
    mov dword [num], 42

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    num dd 0
```

1. Load the immediate value 10 into the `EAX` register.
2. Add the immediate value 20 to the current value in `EAX`.
3. Subtract the immediate value 5 from the current value in `EAX`.
4. Store the immediate value 42 into the memory location pointed by the label `num`.
5. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### 2. Register Addressing Mode

```assembly
section .text
    global _start

_start:
    ; Load the value of 'num1' into EAX
    mov eax, [num1]

    ; Add the value of 'num2' to EAX
    add eax, [num2]

    ; Store the result in the 'num1' variable
    mov [num1], eax

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80

section .data
    num1 dd 10
    num2 dd 20
```

1. Load the value of the memory location pointed by the label `num1` into the `EAX` register.
2. Add the value of the memory location pointed by the label `num2` to the current value in `EAX`.
3. Store the result (sum) back into the memory location pointed by `num1`.
4. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### 3. Direct Addressing Mode

```assembly
section .data
    num1 dd 10

section .bss
    num2 resd 1

section .text
    global _start

_start:
    ; Load the value of 'num1' into EAX
    mov eax, [num1]

    ; Store the value of EAX into the 'num2' variable
    mov [num2], eax

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80
```

1. Load the value of the memory location pointed by the label `num1` into the `EAX` register.
2. Store the value in `EAX` (which is the value of `num1`) into the memory location pointed by the label `num2`.
3. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### 4. Indirect Addressing Mode

```assembly
section .data
    num1 dd 10

section .text
    global _start

_start:
    ; Load the address of 'num1' into EAX
    lea eax, [num1]

    ; Load the value at the address stored in EAX into EBX
    mov ebx, [eax]

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80
```

1. Load the address of the memory location pointed by the label `num1` into the `EAX` register using the `LEA` (Load Effective Address) instruction.
2. Load the value at the address stored in `EAX` into the `EBX` register.
3. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### 5. Indexed Addressing Mode

```assembly
section .data
    array dd 1, 2, 3, 4, 5

section .text
    global _start

_start:
    ; Load the address of the second element (index 1) in the array into EAX
    lea eax, [array + 4]

    ; Load the value at the second element of the array into EBX
    mov ebx, [eax]

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80
```

1. Load the address of the second element (index 1) in the `array` into the `EAX` register using the `LEA` instruction.
2. Load the value at the address stored in `EAX` (address of the second element) into the `EBX` register.
3. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### 

6. Based Addressing Mode

```assembly
section .data
    array dd 1, 2, 3, 4, 5

section .text
    global _start

_start:
    ; Load the address of the first element of the array into EAX
    mov eax, array

    ; Load the value at the first element of the array into EBX
    mov ebx, [eax]

    ; Exit the program
    mov eax, 1
    xor ebx, ebx
    int 0x80
```

1. Load the address of the first element of the `array` into the `EAX` register.
2. Load the value at the address stored in `EAX` (address of the first element) into the `EBX` register.
3. Exit the program gracefully by setting the exit system call number (`eax = 1`) and invoking the system call (`int 0x80`).

### Summary

Understanding addressing modes in x86 assembly language is crucial for efficient memory access and data manipulation. Each addressing mode provides unique ways to interact with memory and handle data. By studying and practicing these code samples, you'll gain confidence in writing optimized and effective x86 assembly code. Keep exploring and experimenting to harness the full potential of x86 assembly programming! 🚀🧠
