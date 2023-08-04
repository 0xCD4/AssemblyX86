## Level 3 - Compute f(x) = mx + b

In this challenge, we are asked to compute the function `f(x) = mx + b` using the following values:

- m = rdi (0x2aa)
- x = rsi (0x1bb3)
- b = rdx (0x229b)

We are required to place the result of `f(x)` into the `rax` register.

### Assembly Code

```assembly
mov rax, rdi
imul rax, rsi
add rax, rdx
```

### Explanation

The above assembly code computes `f(x) = mx + b` as follows:

1. It starts by moving the value of `rdi` (0x2aa) into the `rax` register using the `mov` instruction.
2. It then multiplies the value in `rax` by the value of `rsi` (0x1bb3) using the `imul` instruction. This step effectively calculates `rax = rax * rsi`, where the result is stored in `rax`.
3. Finally, it adds the value of `rdx` (0x229b) to the result in `rax` using the `add` instruction. This step calculates `rax = rax + rdx`, and the final result of `f(x)` is stored in `rax`.

After executing this code, the `rax` register will hold the value of `f(x)` as computed by the given formula.

### Solution Steps

1. Move the value of `rdi` into `rax`.
2. Multiply the value in `rax` by the value of `rsi`.
3. Add the value of `rdx` to the result in `rax`.

The `rax` register will now hold the result of `f(x)` as required by the challenge.

---

Flag: pwn.college{gChn_M0Wb8kfByI2dRrAdrQAWN0.0lN5EDLxUjNyEzW}

