## Level 15 

```assembly
1. In order to swap the values of rdi and rsi, we will use the stack to temporarily store the values.
   Let's push rdi and rsi onto the stack:

push rdi   ; Push the value of rdi onto the stack
push rsi   ; Push the value of rsi onto the stack

2. Now, we can pop the values from the stack into rsi and rdi, effectively swapping their values:

pop rdi    ; Pop the top value from the stack into rdi, which will be the previous value of rsi
pop rsi    ; Pop the second value from the stack into rsi, which will be the previous value of rdi
```

This code snippet swaps the values in the `rdi` and `rsi` registers using the stack. It first pushes the values of `rdi` and `rsi` onto the stack, then pops them back into `rsi` and `rdi`, respectively, effectively swapping their values.


1. First, we are told that we need to swap the values in the `rdi` and `rsi` registers. To do this, we will use the stack to temporarily store the values of these registers. The stack is a last-in-first-out (LIFO) data structure, meaning the last item pushed onto the stack will be the first one popped off.

2. To push a value onto the stack, we use the `push` instruction. The `push` instruction decrements the stack pointer `rsp` by the size of the value being pushed (in this case, 8 bytes, as both `rdi` and `rsi` are 64-bit registers) and then stores the value at the address pointed to by `rsp`.

3. The first `push` instruction, `push rdi`, pushes the current value of `rdi` onto the stack. After this operation, the stack would look like this (assuming `rdi` contains the value 2 and `rsi` contains the value 5):

```
|
| 2
|
```

4. The second `push` instruction, `push rsi`, pushes the current value of `rsi` onto the stack. Now the stack would look like this:

```
|
| 5
| 2
|
```

5. We now have both values (`rdi` and `rsi`) pushed onto the stack. To swap the values, we will use the `pop` instruction. The `pop` instruction retrieves the value from the top of the stack (the value at the address pointed to by `rsp`) and then increments the stack pointer `rsp` by the size of the value retrieved.

6. The first `pop` instruction, `pop rdi`, pops the top value from the stack and stores it in `rdi`. As the stack follows the LIFO principle, `rdi` will now contain the value that was last pushed, which is 5. After this operation, the stack would look like this:

```
|
| 2
|
```

7. The second `pop` instruction, `pop rsi`, pops the second value from the stack and stores it in `rsi`. Now, `rsi` will contain the value that was pushed before `rdi`, which is 2. After this operation, the stack becomes empty:

```
|
|
```

8. At this point, the values in `rdi` and `rsi` have been swapped successfully. `rdi` contains the value 5, and `rsi` contains the value 2.

The Falg: pwn.college{4ebUF_VYMbaZMa4M7Gnbv0-VGGq.0FOwIDLxUjNyEzW}

