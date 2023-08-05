# Level 10

### Given Data

The value stored at memory address `0x404000` is `0x195879`.

### Step 1 - Reading the Value into `rax`

The first step is to read the value stored at memory address `0x404000` and place it into the `rax` register. However, there is an important consideration to take into account. The size of the value at `0x404000` is 32-bit (4 bytes), which means we need to use the `eax` register, as it is the lower 32 bits of `rax`.

```assembly
mov eax, dword ptr [0x404000]
```

This instruction reads the 32-bit value stored at memory address `0x404000` and moves it into the `eax` register.

Before the `mov` instruction:

```
Before: eax = uninitialized (contains garbage value)
Before: [0x404000] = 0x195879
```

After the `mov` instruction:

```
After:  eax = 0x000195879
After:  [0x404000] = 0x195879
```

### Step 2 - Incrementing the Value at `0x404000`

The next step is to increment the value stored at memory address `0x404000` by `0x1337`. We use the `add` instruction to achieve this.

```assembly
add dword ptr [0x404000], 0x1337
```

This instruction adds the value `0x1337` to the 32-bit value stored at memory address `0x404000`, effectively incrementing it.

Before the `add` instruction:

```
Before: [0x404000] = 0x195879
```

After the `add` instruction:

```
After:  [0x404000] = 0x196BB0
```

### Final Result

After executing the provided code, the values in memory are updated as follows:

```
[0x404000] = 0x196BB0
```

The value in the `rax` register is `0x000195879`, which is the original value read from memory address `0x404000`.

Flag: `pwn.college{MaPpipn8am7oJj1e7MsmjPPg3th.01MwIDLxUjNyEzW}`
