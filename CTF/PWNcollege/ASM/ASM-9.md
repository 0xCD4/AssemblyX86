## Level 9 - Even or Odd Number Determination (Explanation)

In this challenge, we are given the value of `rdi`, and we need to determine whether `rdi` is even or odd. If `rdi` is even, we set `rax` to 1; otherwise, we set `rax` to 0.

### Given Data

The value of `rdi` is: `0x1ef226d6`

### Solution Steps

1. We can use bitwise AND operation to extract the least significant bit (LSB) of `rdi`. This can be achieved by using the instruction `and eax, 1`. The result will be stored in `rax`.

   - Before: `rax = uninitialized` (contains garbage value)
   - Before: `rdi = 0x1ef226d6`
   - After: `rax = 0x0000000000000001`

2. After performing the bitwise AND operation, we use bitwise OR operation (`or eax, 1`) to set the value of `rax` to 1, regardless of whether the LSB was 0 or 1.

   - Before: `rax = 0x0000000000000001`
   - After: `rax = 0x0000000000000001` (The value of `rax` is now 1)

### Final Result

After executing the provided code, the `rax` register will hold the value `0x0000000000000001`, which represents that `rdi` is an odd number. The result is set to 1 because `rdi` is not an even number.

### Explanation in Assembly Code

```assembly
and eax, 1  ; Extract the LSB of rdi and store it in rax
or eax, 1   ; Set rax to 1, regardless of the LSB value
```

---

The value in the `rax` register after executing the provided code is `0x0000000000000001`, indicating that `rdi` is an odd number. The final flag can be derived from this result.

Flag: pwn.college{oG7CCgDLdkN47j14EBmR_xye_5Z.0lMwIDLxUjNyEzW}


### Given Data

The value of `rdi` is: `0x1ef226d6`

### Step 1 - Extracting the Least Significant Bit (LSB)

The first step is to determine the least significant bit (LSB) of the value stored in `rdi`. The LSB is the rightmost bit in the binary representation of a number. To achieve this, we use the bitwise AND operation with the constant value `1`.

```assembly
and eax, 1
```

Before the `and` instruction, the `eax` register contains uninitialized data, which means it may contain garbage values.

Binary representation of `rdi` (32 bits): `0001 1110 1111 0010 0010 0110 1101 0110`

Binary representation of `1`: `0000 0000 0000 0000 0000 0000 0000 0001`

The `and` operation compares each bit of the two operands (`eax` and `1`) and sets the corresponding bit in the result if both bits are 1. Otherwise, the bit in the result is set to 0.

Since we are performing the `and` operation with `1`, all the bits in `eax` except the LSB will be zeroed out, and the result will only contain the value of the LSB.

After the `and` instruction:

```
Before: eax = uninitialized (contains garbage value)
Before: rdi = 0x1ef226d6
After:  eax = 0x0000000000000001
```

### Step 2 - Determining Even or Odd

Now that we have isolated the LSB in `eax`, the value in `eax` will be `1` if the original value of `rdi` had a `1` as its LSB, indicating that `rdi` is an odd number. If the original value of `rdi` had a `0` as its LSB, then the value in `eax` will be `0`, indicating that `rdi` is an even number.

To finalize the determination, we use the bitwise OR operation with the constant value `1`. This will set the value of `eax` to `1` regardless of its original value, ensuring that `rax` will contain `1` if `rdi` is odd.

```assembly
or eax, 1
```

After the `or` instruction:

```
Before: eax = 0x0000000000000001
After:  eax = 0x0000000000000001
```

### Final Result

The value in the `rax` register after executing the provided code is `0x0000000000000001`. This indicates that the original value of `rdi` (`0x1ef226d6`) is an odd number. The result is set to `1` because `rdi` is not an even number.



