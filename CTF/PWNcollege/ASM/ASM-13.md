# Level 13

## Step 1: Load two consecutive quad words from the address stored in rdi

```assembly
mov rax, [rdi]       ; Load the first quad word from the address stored in rdi into rax
add rax, [rdi+8]    ; Add the second quad word (at offset 8 bytes from rdi) to rax
```

1. The first line uses the `mov` instruction to load the value stored at the memory address in the `rdi` register into the `rax` register. In x86_64, `rdi` is one of the general-purpose registers that can be used to store memory addresses. The square brackets around `rdi` indicate that we are dereferencing `rdi` to access the memory location it points to. Since each quad word is 8 bytes (64 bits), this instruction loads the first quad word from the address stored in `rdi` into the `rax` register.

2. The second line uses the `add` instruction to add the value of the second quad word to the `rax` register. The value of the second quad word is located at the memory address `rdi+8`. The `+8` is an offset indicating that we want to access the memory 8 bytes after the address in `rdi`, which corresponds to the second quad word.

At this point, the `rax` register contains the sum of the two consecutive quad words from the address stored in `rdi`.

## Step 2: Store the sum at the address in rsi

```assembly
mov [rsi], rax       ; Store the sum (in rax) at the memory address in rsi
```

1. The last line uses the `mov` instruction to move the value in the `rax` register (which holds the sum of the two quad words) into the memory address pointed to by the `rsi` register. Similar to `rdi`, `rsi` is another general-purpose register used to store memory addresses. By using the square brackets around `rsi`, we are dereferencing `rsi` to get the memory address where we want to store the sum.

After executing these instructions, the sum of the two consecutive quad words from the address stored in `rdi` will be calculated and stored at the memory address pointed by `rsi`, which is `0x404678` in this case.

## Final Result

The sum of the two consecutive quad words from the addresses `0x404320` and `0x404328` will be calculated and stored at the memory address `0x404678`.

The flag for this level is: `pwn.college{gQAei527h6ghMsddYyyFOxCOLUa.0lNwIDLxUjNyEzW}`.
