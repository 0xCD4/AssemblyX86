## Level 5 - Compute Modulo (rdi % rsi)

In this challenge, we are asked to compute the modulo operation `rdi % rsi`, where:

- `rdi` = 0x3355c0bd
- `rsi` = 0xf

We are required to place the result of the modulo operation in the `rax` register.

### Assembly Code

```assembly
mov rax, rdi
mov edx, 0
div rsi
mov rax, rdx
```

### Explanation

The above assembly code performs the following steps to compute the modulo operation:

1. It starts by moving the value of `rdi` (dividend) into the `rax` register using the `mov` instruction. This step prepares `rax` to be the dividend for the division operation.

2. The `mov edx, 0` instruction clears the `edx` register (remainder) to zero. This step is important before performing the division because the `div` instruction takes both the dividend and divisor from `rax` and `rsi`, respectively, and stores the quotient in `rax` and the remainder in `rdx`. To ensure there is no leftover value in `rdx` from previous calculations, it is cleared to zero.

3. The `div rsi` instruction performs the division of the value in `rax` by the value in `rsi`. After the division, the quotient is placed in `rax`, and the remainder is placed in `rdx`.

4. Finally, the `mov rax, rdx` instruction moves the value of `rdx` (remainder) into `rax`. This step effectively places the result of the modulo operation in `rax`, as required by the challenge.

After executing this code, the `rax` register will hold the value of `rdi % rsi`, which represents the remainder after dividing `rdi` by `rsi`.

### Solution Steps

1. Move the value of `rdi` (dividend) into `rax`.
2. Clear the `edx` register (remainder) to zero.
3. Divide `rax` (dividend) by `rsi` (divisor) using the `div` instruction.
4. Move the value of `rdx` (remainder) into `rax`.

The `rax` register will now hold the result of the modulo operation, as required by the challenge.

---

The Flag: pwn.college{sdQCoxpSKhsJOxKLqLi5IF0jDi1.0FO5EDLxUjNyEzW}
