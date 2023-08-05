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




### Given Data

The value of `rdi` is: `8c 5b f7 5e 4e 54 2f 93`

### Solution Steps

1. Initially, the value of `rdi` is stored in `rax`, making it easier to perform the shifting operations on `rax`.

2. We perform a right shift of 32 bits (`shr rax, 32`). This operation discards the most significant 4 bytes of `rax`, leaving only the 4 least significant bytes.

   - Before: `8c 5b f7 5e 4e 54 2f 93`
   - After: `00 00 00 00 8c 5b f7 5e`

3. Next, we perform a left shift of 32 bits (`shl rax, 32`). This operation restores the most significant 4 bytes to 0, effectively zeroing them out.

   - Before: `00 00 00 00 8c 5b f7 5e`
   - After: `8c 5b f7 5e 00 00 00 00`

4. We perform another left shift, this time of 24 bits (`shl rax, 24`). This operation moves the 5th least significant byte of the original `rdi` to the most significant position of `rax`.

   - Before: `8c 5b f7 5e 00 00 00 00`
   - After: `5e 00 00 00 00 00 00 00`

### Final Result

After executing the above instructions, the `rax` register will hold the value `5e` (in hexadecimal), which is the 5th least significant byte of the original `rdi` value.

### Explanation in Assembly Code

```assembly
mov rax, rdi   ; Move the value of rdi into rax
shr rax, 32    ; Right shift rax by 32 bits (discard most significant 4 bytes)
shl rax, 32    ; Left shift rax by 32 bits (restore most significant 4 bytes to 0)
shl rax, 24    ; Left shift rax by 24 bits (move 5th least significant byte to most significant position)
```



The value in the `rax` register after executing the provided code is `5e`, which is the 5th least significant byte of the original `rdi` value. The final flag can be derived from this result.



The Flag: pwn.college{cm5Lbv4ttjiDHxd6ZCWkMql6NgK.0FMwIDLxUjNyEzW}
