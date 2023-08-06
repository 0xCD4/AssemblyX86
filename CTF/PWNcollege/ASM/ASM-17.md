## Level17

### Problem Description:

In this level, you need to create a two-jump trampoline:

1. Make the first instruction in your code a `jmp`.
2. Make that `jmp` a relative jump to 0x51 bytes from its current position.
3. At 0x51, write the following code:
   - Place the top value on the stack into register `rdi`.
   - Jump to the absolute address 0x403000.

### Solution:

```assembly
0x400000:       jmp     label

.rept 0x51
    nop
.endr

label:
    pop     rdi
    mov     rax, 0x403000
    jmp     rax
```

### Explanation:

1. The first instruction in the code is a relative jump (`jmp`) to the label named `label`. Relative jumps use a signed offset value to determine the destination address relative to the current position. In this case, the jump is made to the label `label`, which is located at `0x400103` (offset `0x103` from the current position). Since the relative jump is `0x103` bytes ahead, it will effectively jump to address `0x400103`.

2. After the `jmp` instruction, there is a block of 0x51 `nop` (no-operation) instructions. The `nop` instruction is used as a placeholder to fill space in the code. It is 1 byte in size and does nothing when executed. The purpose of these `nop` instructions is to create a gap of 0x51 bytes between the `jmp` instruction and the `label:` part.

3. The `label:` section begins at address `0x400103`. The first instruction in this section is `pop rdi`. The `pop` instruction is used to retrieve the top value from the stack and store it in the specified register. In this case, it pops the top value from the stack into the `rdi` register.

4. The next instruction is `mov rax, 0x403000`. The `mov` instruction is used to move data between registers and memory locations. Here, we move the immediate value `0x403000` into the `rax` register. This is setting up `rax` with the address we want to jump to in the next instruction.

5. The final instruction is `jmp rax`. This is an absolute jump to the address stored in the `rax` register. Since we set `rax` to `0x403000` in the previous `mov` instruction, the `jmp` will transfer control to address `0x403000`.


### Part 1: Relative Jump

```assembly
0x400000:       jmp     label
```

The first instruction in the code is a `jmp` instruction, which stands for "jump." This instruction is used to transfer control flow to a different part of the code. In this case, we want to create a relative jump, which means the jump will be executed based on a signed offset from the current instruction pointer (`rip`).

The `jmp` instruction has the following format:

```
jmp destination
```

Here, `destination` can be specified in three ways:

1. A label: The `destination` can be a label in the code, and the `jmp` instruction will jump to the address of that label.
2. An address: The `destination` can be a specific memory address, and the `jmp` instruction will jump to that address.
3. An offset: The `destination` can be a relative offset (positive or negative), and the `jmp` instruction will add this offset to the current value of `rip`.

In our code, we are using a label called `label`. The label is defined later in the code at address `0x400103`. So, the `jmp` instruction will jump to the address of the `label`.

### Part 2: Creating a Gap with NOP Instructions

```assembly
.rept 0x51
    nop
.endr
```

In this part, we are using the `.rept` (repeat) and `.endr` (end repeat) directives to generate a block of 0x51 `nop` instructions. The `nop` instruction is a no-operation instruction, which means it does nothing when executed. It is often used as a placeholder to create gaps in the code.

The `.rept` directive specifies the number of repetitions, which is `0x51` in this case. This will repeat the `nop` instruction 0x51 times, effectively creating a gap of 0x51 bytes between the `jmp` instruction and the `label:` part.

### Part 3: Label Section - Popping Value to RDI

```assembly
label:
    pop     rdi
```

After the gap created by the `nop` instructions, we define a label called `label:`. Labels are used as markers in the code that represent specific addresses. In this case, the `label` marks the starting point of the code we want to execute after the relative jump.

The first instruction under the `label:` is `pop rdi`. The `pop` instruction is used to retrieve the top value from the stack and store it in the specified register. In this case, it pops the top value from the stack into the `rdi` register.

### Part 4: Moving Immediate Value to RAX

```assembly
    mov     rax, 0x403000
```

In this part, we are using the `mov` instruction to move an immediate value (`0x403000`) into the `rax` register. The `mov` instruction is used for data transfer between registers and memory locations. In this case, we are setting up `rax` with the address we want to jump to in the next instruction.

### Part 5: Absolute Jump to Address Stored in RAX

```assembly
    jmp     rax
```

The final instruction in the code is another `jmp` instruction, but this time it's an absolute jump. An absolute jump means that the destination address is specified directly and not based on any relative offset. The `jmp` instruction will transfer control flow to the address stored in the `rax` register.

In the previous instruction, we set `rax` to `0x403000`, so this `jmp` will effectively jump to address `0x403000`.

### Summary:

In summary, the solution starts with a relative jump to create a gap, followed by popping the top value from the stack into the `rdi` register. Then, it moves the immediate value `0x403000` into the `rax` register and performs an absolute jump to that address. This two-jump trampoline enables the program to execute a specific control flow, achieving the desired behavior for the challenge.

The Flag: flag: pwn.college{4Rj4oGfAUxNLSP-drR9ztZKZ0HC.0FMxIDLxUjNyEzW}
