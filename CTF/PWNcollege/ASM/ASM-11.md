# Level 11 

In this challenge, we need to access different memory sizes (byte, word, double word, and quad word) stored at a specific memory address and move them into different registers.

```assembly
Executing your code...
---------------- CODE ----------------
0x400000:       mov     al, byte ptr [0x404000]
0x400007:       mov     bx, word ptr [0x404000]
0x40000f:       mov     ecx, dword ptr [0x404000]
0x400016:       mov     rdx, qword ptr [0x404000]
```

1. Set `rax` to the byte at `0x404000`:
   - We use `mov al, byte ptr [0x404000]` to move the least significant byte from memory location `0x404000` to `al` register. This allows us to access only the byte at that location.

2. Set `rbx` to the word at `0x404000`:
   - We use `mov bx, word ptr [0x404000]` to move the least significant word from memory location `0x404000` to `bx` register. This allows us to access the 16-bit word at that location.

3. Set `rcx` to the double word at `0x404000`:
   - We use `mov ecx, dword ptr [0x404000]` to move the least significant double word from memory location `0x404000` to `ecx` register. This allows us to access the 32-bit double word at that location.

4. Set `rdx` to the quad word at `0x404000`:
   - We use `mov rdx, qword ptr [0x404000]` to move the full 64-bit quad word from memory location `0x404000` to `rdx` register. This allows us to access the entire 64-bit value at that location.

After executing the code, the values in the registers will be as follows:

```
rax = 0xc4
rbx = 0x1d7c
rcx = 0x1d7cc4
rdx = 0x1d7cc4
```

## The explanation


1. Set `rax` to the byte at `0x404000`:
   - To access a byte at a specific memory location, we use the `al` register in x86_64, which is the lower 8 bits of `rax`. The instruction `mov al, byte ptr [0x404000]` moves the byte stored at memory location `0x404000` into the `al` register. The `byte ptr` indicates that we are accessing a byte-sized value.
   - After executing this instruction, `al` will contain the value `0xc4`, which is the byte stored at `0x404000`.

2. Set `rbx` to the word at `0x404000`:
   - To access a word (16 bits) at a specific memory location, we use the `bx` register in x86_64, which is the lower 16 bits of `rbx`. The instruction `mov bx, word ptr [0x404000]` moves the word stored at memory location `0x404000` into the `bx` register. The `word ptr` indicates that we are accessing a word-sized value.
   - After executing this instruction, `bx` will contain the value `0x1d7c`, which is the word stored at `0x404000`.

3. Set `rcx` to the double word at `0x404000`:
   - To access a double word (32 bits) at a specific memory location, we use the `ecx` register in x86_64, which is the lower 32 bits of `rcx`. The instruction `mov ecx, dword ptr [0x404000]` moves the double word stored at memory location `0x404000` into the `ecx` register. The `dword ptr` indicates that we are accessing a double word-sized value.
   - After executing this instruction, `ecx` will contain the value `0x1d7cc4`, which is the double word stored at `0x404000`.

4. Set `rdx` to the quad word at `0x404000`:
   - To access a quad word (64 bits) at a specific memory location, we use the `rdx` register in x86_64, which is the full 64-bit register. The instruction `mov rdx, qword ptr [0x404000]` moves the quad word stored at memory location `0x404000` into the `rdx` register. The `qword ptr` indicates that we are accessing a quad word-sized value.
   - After executing this instruction, `rdx` will contain the value `0x1d7cc4`, which is the quad word stored at `0x404000`.

So, after executing the given assembly code, the values in the registers will be as follows:

```
rax = 0xc4
rbx = 0x1d7c
rcx = 0x1d7cc4
rdx = 0x1d7cc4
```

The flag for this level is: `pwn.college{8x7YK56sNsCm40c0RvvLpuGZV55.0FNwIDLxUjNyEzW}`.




