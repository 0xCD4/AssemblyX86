## Level 2 - Add 0x331337 to rdi

In this challenge, we are asked to add the value `0x331337` to the `rdi` register.

### Assembly Code

```assembly
mov rax, 0x331337
add rdi, rax
```

### Explanation

The above assembly code starts by moving the immediate value `0x331337` into the `rax` register using the `mov` instruction. Then, it performs an addition operation using the `add` instruction to add the value in `rax` (0x331337) to the value in `rdi`. After executing this code, the result will be stored in `rdi`.

### Solution Steps

1. Initialize the `rax` register with the value `0x331337`.
2. Add the value in `rax` to the value in `rdi`.

The `rdi` register will now hold the result of adding `0x331337` to its original value, as required by the challenge.



Flag: pwn.college{QvjyJnljKvDhgH8llaoSe_8eW8V.0VN5EDLxUjNyEzW}
