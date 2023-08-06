# Level 12 

To solve this challenge, we are given two addresses (`rdi` and `rsi`) where we need to store specific values.

1. Set [rdi] = 0xdeadbeef00001337:

```assembly
mov rax, 0xdeadbeef00001337 ; Load 0xdeadbeef00001337 into rax
mov [rdi], rax             ; Move the value in rax to the memory address stored in rdi
```

Explanation:
- In the first line, we use the `mov` instruction to load the immediate value `0xdeadbeef00001337` into the `rax` register. Since `rax` is a 64-bit register, it can hold the full value without any issues.
- In the second line, we use the `mov` instruction again to move the value from `rax` to the memory address stored in the `rdi` register. The square brackets around `rdi` indicate that we are dereferencing the value in `rdi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xdeadbeef00001337` will be stored at the memory address `0x4040b0` (rdi).

2. Set [rsi] = 0xc0ffee0000:

```assembly
mov rax, 0xc0ffee0000 ; Load 0xc0ffee0000 into rax
mov [rsi], rax        ; Move the value in rax to the memory address stored in rsi
```

Explanation:
- In the first line, we use the `mov` instruction to load the immediate value `0xc0ffee0000` into the `rax` register. Since `rax` is a 64-bit register, it can hold the full value without any issues.
- In the second line, we use the `mov` instruction again to move the value from `rax` to the memory address stored in the `rsi` register. The square brackets around `rsi` indicate that we are dereferencing the value in `rsi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xc0ffee0000` will be stored at the memory address `0x404c60` (rsi).


# In detailed way

Certainly! Let's go into more detail for each step of the solution:

## Step 1: Set [rdi] = 0xdeadbeef00001337

```assembly
mov rax, 0xdeadbeef00001337
mov [rdi], rax
```

1. We start by using the `mov` instruction to load the immediate value `0xdeadbeef00001337` into the `rax` register. The `mov` instruction is used to move data between operands, and in this case, we are moving a 64-bit immediate value into the 64-bit `rax` register. The `rax` register is commonly used as a general-purpose register in x86_64 architecture.

2. Next, we use the `mov` instruction again to move the value from the `rax` register to the memory address stored in the `rdi` register. The square brackets around `rdi` indicate that we are dereferencing the value in `rdi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xdeadbeef00001337` will be stored at the memory address `[rdi]`, which is `0x4040b0` in this case.

## Step 2: Set [rsi] = 0xc0ffee0000

```assembly
mov rax, 0xc0ffee0000
mov [rsi], rax
```

1. We start by using the `mov` instruction to load the immediate value `0xc0ffee0000` into the `rax` register. Again, we are moving a 64-bit immediate value into the `rax` register.

2. Next, we use the `mov` instruction again to move the value from the `rax` register to the memory address stored in the `rsi` register. Similar to Step 1, the square brackets around `rsi` indicate that we are dereferencing the value in `rsi` to get the memory address it points to. This way, we set the value at that memory address to the value stored in `rax`.

After executing these instructions, the value `0xc0ffee0000` will be stored at the memory address `[rsi]`, which is `0x404c60` in this case.

## Final Result

After running both sets of instructions, the memory contents at the addresses `0x4040b0` and `0x404c60` will be modified as follows:

- Memory at `0x4040b0`: `0xdeadbeef00001337`
- Memory at `0x404c60`: `0xc0ffee0000`

Finally, the flag for this level is: `pwn.college{g-fjVH4ktMpsnaz29IuHA0XfCSv.0VNwIDLxUjNyEzW}`.
