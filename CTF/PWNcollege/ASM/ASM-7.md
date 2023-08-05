## Level 7 - Shifting and Extracting Least Significant Byte

In this challenge, we are given the value of `rdi`, and we are asked to set `rax` to the 5th least significant byte of `rdi`.

We need to consider that `rdi` consists of 8 bytes, and we need to extract the 5th least significant byte, which is the 6th byte counting from the right (0-indexed).

### Assembly Code

```assembly
mov rax, rdi
shr rax, 0x20
shl rax, 0x20
shl rax, 0x18
shr rax, 0x38
```

### Explanation

The above assembly code performs the following steps to set `rax` to the 5th least significant byte of `rdi`:

1. `mov rax, rdi`: This instruction moves the value of `rdi` into `rax`, making it easier to perform the shifting operations on `rax`.

2. `shr rax, 0x20`: This instruction shifts the value in `rax` 32 bits to the right. This is equivalent to discarding the most significant 4 bytes of `rax`, leaving only the 4 least significant bytes.

3. `shl rax, 0x20`: This instruction shifts the value in `rax` 32 bits to the left. This is equivalent to restoring the most significant 4 bytes to 0, effectively zeroing them out.

4. `shl rax, 0x18`: This instruction shifts the value in `rax` 24 bits to the left. This step moves the 5th least significant byte of the original `rdi` to the most significant position of `rax`.

5. `shr rax, 0x38`: This instruction shifts the value in `rax` 56 bits to the right. This is equivalent to discarding the most significant 7 bytes of `rax`, leaving only the 5th least significant byte in `rax`.

After executing this code, the `rax` register will hold the 5th least significant byte of `rdi`, as required by the challenge.

### Solution Steps

1. Move the value of `rdi` into `rax`.
2. Shift `rax` 32 bits to the right to discard the most significant 4 bytes of `rax`.
3. Shift `rax` 32 bits to the left to zero out the most significant 4 bytes of `rax`.
4. Shift `rax` 24 bits to the left to move the 5th least significant byte of the original `rdi` to the most significant position of `rax`.
5. Shift `rax` 56 bits to the right to discard the most significant 7 bytes of `rax`, leaving only the 5th least significant byte.

The `rax` register will now hold the 5th least significant byte of `rdi`, as required by the challenge.

---

The Flag: pwn.college{cm5Lbv4ttjiDHxd6ZCWkMql6NgK.0FMwIDLxUjNyEzW}
