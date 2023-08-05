## Level 4 - Compute speed = distance / time

In this challenge, we are asked to compute the speed using the formula `speed = distance / time`, where:

- distance = rdi (0x170c)
- time = rsi (0x14)

We are required to place the result of the speed calculation into the `rax` register.

### Assembly Code

```assembly
mov rax, rdi
mov rbx, rsi
xor rdx, rdx
div rbx
```


### Explanation

The above assembly code performs the following steps:

1. It starts by moving the value of `rdi` (distance) into the `rax` register using the `mov` instruction.
2. It then moves the value of `rsi` (time) into the `rbx` register using the `mov` instruction.
3. The `xor rdx, rdx` instruction clears the `rdx` register (remainder) to prepare it for the division operation.
4. Finally, it uses the `div rbx` instruction to perform the division of `rax` (distance) by `rbx` (time). The result is placed in `rax`, and any remainder is placed in `rdx`.

After executing this code, the `rax` register will hold the value of the calculated speed.

### Solution Steps

1. Move the value of `rdi` (distance) into `rax`.
2. Move the value of `rsi` (time) into `rbx`.
3. Clear the `rdx` register (remainder).
4. Divide `rax` (distance) by `rbx` (time).

The `rax` register will now hold the result of the speed calculation, as required by the challenge.

---

Flag: pwn.college{cC2N2Ye88oqb5Y4HgkRwxWZM2XC.01N5EDLxUjNyEzW}

