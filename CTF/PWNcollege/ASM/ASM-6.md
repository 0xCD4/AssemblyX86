## Level 6 - Compute Modulo and Store in Different Registers

In this challenge, we are asked to compute the modulo operations and store the results in different registers using the following values:

- `rdi` = 0x1ac1
- `rsi` = 0x8484512c

We are required to compute the following:

- rax = rdi modulo 256 (lower 8 bits of rdi)
- rbx = rsi modulo 65536 (lower 16 bits of rsi)

### Assembly Code

```assembly
mov rax, 0
mov rbx, 0
mov al, dil
mov bx, si
```

### Explanation

The above assembly code performs the following steps to compute the modulo operations:

1. `mov rax, 0`: This instruction clears the `rax` register to zero. This step is done to make sure that the `rax` register is ready to store the lower 8 bits of `rdi` (remainder after the modulo operation).

2. `mov rbx, 0`: This instruction clears the `rbx` register to zero. This step is done to make sure that the `rbx` register is ready to store the lower 16 bits of `rsi` (remainder after the modulo operation).

3. `mov al, dil`: This instruction moves the lower 8 bits of `rdi` into the `al` register. The `dil` register holds the lower 8 bits of `rdi`. After this instruction, `rax` will hold the result of `rdi % 256`.

4. `mov bx, si`: This instruction moves the lower 16 bits of `rsi` into the `bx` register. After this instruction, `rbx` will hold the result of `rsi % 65536`.

After executing this code, the `rax` register will hold the remainder of `rdi` after dividing by 256, and the `rbx` register will hold the remainder of `rsi` after dividing by 65536.

### Solution Steps

1. Clear `rax` to zero.
2. Clear `rbx` to zero.
3. Move the lower 8 bits of `rdi` into `rax`.
4. Move the lower 16 bits of `rsi` into `rbx`.

The `rax` register will now hold the result of `rdi % 256`, and the `rbx` register will hold the result of `rsi % 65536`, as required by the challenge.

---
![image](https://github.com/0xCD4/AssemblyX86/assets/116346668/e33e711b-d4db-4c29-9482-e9439cef8309)



The Flag: pwn.college{khWuhXBy5bT5j3XW_iDOOrMlUou.0VO5EDLxUjNyEzW}

