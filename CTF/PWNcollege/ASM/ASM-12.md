# Level 12

1. Set [rdi] = 0xdeadbeef00001337:

First, we want to set the memory address `[rdi]` to the value `0xdeadbeef00001337`. However, since we are working with a 64-bit register (rdi), we cannot directly load the 64-bit immediate value `0xdeadbeef00001337` into it. Instead, we will use the `rax` register as an intermediary to store the value and then move it to the memory address `[rdi]`.

```assembly
mov rax, 0xdeadbeef00001337 ; Load 0xdeadbeef00001337 into rax
mov [rdi], rax             ; Move the value in rax to the memory address stored in rdi
```

1.1. `mov rax, 0xdeadbeef00001337`: In this instruction, we are using the `mov` (move) instruction to load the immediate value `0xdeadbeef00001337` into the `rax` register. Since `rax` is a 64-bit register, it can hold the full value without any issues.

1.2. `mov [rdi], rax`: Now that `rax` holds the value `0xdeadbeef00001337`, we use the `mov` instruction again to move the value from `rax` to the memory address stored in the `rdi` register. The square brackets around `rdi` indicate that we are dereferencing the value in `rdi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xdeadbeef00001337` will be stored at the memory address `0x4040b0` (rdi).

2. Set [rsi] = 0xc0ffee0000:

Similar to the previous step, we want to set the memory address `[rsi]` to the value `0xc0ffee0000`. Again, since we are working with a 64-bit register (rsi), we cannot directly load the 64-bit immediate value `0xc0ffee0000` into it. We will use the `rax` register to store the value temporarily and then move it to the memory address `[rsi]`.

```assembly
mov rax, 0xc0ffee0000 ; Load 0xc0ffee0000 into rax
mov [rsi], rax        ; Move the value in rax to the memory address stored in rsi
```

2.1. `mov rax, 0xc0ffee0000`: In this instruction, we are using the `mov` instruction to load the immediate value `0xc0ffee0000` into the `rax` register. Since `rax` is a 64-bit register, it can hold the full value without any issues.

2.2. `mov [rsi], rax`: Now that `rax` holds the value `0xc0ffee0000`, we use the `mov` instruction again to move the value from `rax` to the memory address stored in the `rsi` register. The square brackets around `rsi` indicate that we are dereferencing the value in `rsi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xc0ffee0000` will be stored at the memory address `0x404c60` (rsi).

Finally, the flag for this level is: `pwn.college{g-fjVH4ktMpsnaz29IuHA0XfCSv.0VNwIDLxUjNyEzW}`.
