# Level 18 Solution

To interact with any level you will send raw bytes over stdin to this program.
To efficiently solve these problems, first run it once to see what you need
then craft, assemble, and pipe your bytes to this program.

In this level you will be working with control flow manipulation. This involves using instructions
to both indirectly and directly control the special register `rip`, the instruction pointer.
You will use instructions like: jmp, call, cmp, and the like to implement requests behavior.

We will be testing your code multiple times in this level with dynamic values! This means we will
be running your code in a variety of random ways to verify that the logic is robust enough to
survive normal use. You can consider this as normal dynamic value se

We will now introduce you to conditional jumps--one of the most valuable instructions in x86.
In higher level programming languages, an if-else structure exists to do things like:
if x is even:
   is_even = 1
else:
   is_even = 0
This should look familiar, since its implementable in only bit-logic. In these structures, we can
control the programs control flow based on dynamic values provided to the program. Implementing the
above logic with jmps can be done like so:

```assembly
; assume rdi = x, rax is output
; rdx = rdi mod 2
mov rax, rdi
mov rsi, 2
div rsi
; remainder is 0 if even
cmp rdx, 0
; jump to not_even code if it's not 0
jne not_even
; fall through to even code
mov rbx, 1
jmp done
; jump to this only when not_even
not_even:
mov rbx, 0
done:
mov rax, rbx
; more instructions here

```

Often though, you want more than just a single 'if-else'. Sometimes you want two if checks, followed
by an else. To do this, you need to make sure that you have control flow that 'falls-through' to the
next if after it fails. All must jump to the same done after execution to avoid the else.
There are many jump types in x86, it will help to learn how they can be used. Nearly all of them rely
on something called the ZF, the Zero Flag. The ZF is set to 1 when a cmp is equal. 0 otherwise.

Using the above knowledge, implement the following:
```bash
if [x] is 0x7f454c46:
   y = [x+4] + [x+8] + [x+12]
else if [x] is 0x00005A4D:
   y = [x+4] - [x+8] - [x+12]
else:
   y = [x+4] * [x+8] * [x+12]
```
where:
x = rdi, y = rax. Assume each dereferenced value is a signed dword. This means the values can start as
a negative value at each memory position.
A valid solution will use the following at least once:
jmp (any variant), cmp

Here's the provided solution:
```assembly
mov eax, [rdi]
mov ebx, [rdi+4]
mov ecx, [rdi+8]
mov edx, [rdi+12]

case1:
cmp eax, 0x7f454c46
jne case2
mov eax, 0
add eax, ebx
add eax, ecx
add eax, edx
jmp exit

case2:
cmp rax, 0x00005A4D
jne case3
mov eax, ebx
sub eax, ecx
sub eax, edx
jmp exit

case3:
mov eax, edx
imul eax, ecx
imul eax, ebx
jmp exit

exit:
nop
```

Absolutely, I'll provide a more detailed breakdown of the solution for ASMLevel18:

## Problem Description

In this challenge, you are given the task of implementing conditional control flow using x86 assembly instructions. Specifically, you need to perform different calculations based on the value stored at memory location `x` (passed in as `rdi`), and store the result in the register `rax`.

You are required to implement the following logic:
- If the value at `[x]` is `0x7f454c46`, then calculate `y` as the sum of the values at `[x+4]`, `[x+8]`, and `[x+12]`.
- Else if the value at `[x]` is `0x00005A4D`, then calculate `y` as the result of subtracting the values at `[x+4]`, `[x+8]`, and `[x+12]`.
- Otherwise, calculate `y` as the product of the values at `[x+4]`, `[x+8]`, and `[x+12]`.

## Solution Breakdown

1. Load Values: The code begins by loading four values from memory into registers:
   ```assembly
   mov eax, [rdi]
   mov ebx, [rdi+4]
   mov ecx, [rdi+8]
   mov edx, [rdi+12]
   ```

2. Case 1: Check if `[x]` is equal to `0x7f454c46`:
   ```assembly
   case1:
   cmp eax, 0x7f454c46
   jne case2
   ```

   If the comparison is true (equal), jump to `case2`. Otherwise, continue executing the code.

3. Calculate Sum (`y`) for Case 1:
   ```assembly
   mov eax, 0        ; Set result to 0
   add eax, ebx      ; Add value at [x+4]
   add eax, ecx      ; Add value at [x+8]
   add eax, edx      ; Add value at [x+12]
   jmp exit          ; Jump to the exit
   ```

4. Case 2: Check if `[x]` is equal to `0x00005A4D`:
   ```assembly
   case2:
   cmp rax, 0x00005A4D
   jne case3
   ```

   If the comparison is true (equal), jump to `case3`. Otherwise, continue executing the code.

5. Calculate Difference (`y`) for Case 2:
   ```assembly
   mov eax, ebx      ; Set result to value at [x+4]
   sub eax, ecx      ; Subtract value at [x+8]
   sub eax, edx      ; Subtract value at [x+12]
   jmp exit          ; Jump to the exit
   ```

6. Calculate Product (`y`) for Case 3:
   ```assembly
   case3:
   mov eax, edx      ; Set result to value at [x+12]
   imul eax, ecx     ; Multiply by value at [x+8]
   imul eax, ebx     ; Multiply by value at [x+4]
   jmp exit          ; Jump to the exit
   ```

7. Exit:
   ```assembly
   exit:
   nop               ; Placeholder instruction
   ```

## Conclusion

The provided solution demonstrates the use of conditional jumps and comparison instructions to implement different calculations based on the values at specific memory locations. By using `cmp` and `jmp` instructions, the program controls its flow and performs the required calculations, storing the result in the `rax` register.

The detailed breakdown above should give you a comprehensive understanding of how the solution works to achieve the desired conditional control flow.

The Flag: pwn.college{c1lOJb2HDKgEdtNtjZnfjZ4Fw11.0VMxIDLxUjNyEzW}
