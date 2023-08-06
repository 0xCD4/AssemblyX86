## Level 14 

To solve this challenge, we need to manipulate the stack to replace the top value with the result of subtracting the value in `rdi`.

1. Pop the last value from the stack into the `rax` register:

```assembly
pop rax
```

The `pop` instruction retrieves the last value from the stack and stores it in the `rax` register. Since the stack follows the Last In, First Out (LIFO) order, the last value pushed will be the first one popped.

2. Subtract the value in `rdi` from the value in `rax`:

```assembly
sub rax, rdi
```

The `sub` instruction performs subtraction. In this case, it subtracts the value in `rdi` from the value in `rax` and stores the result in `rax`. This instruction effectively replaces the top value on the stack with the result of the subtraction.

3. Push the result back onto the stack:

```assembly
push rax
```

The `push` instruction stores the value in the `rax` register back onto the stack. Since we modified `rax` in the previous step, it now contains the result of the subtraction. So, we are pushing the result back to the top of the stack.

After executing these instructions, the value at the top of the stack will be updated with the result of the subtraction of the original value at the top of the stack and the value in `rdi`.

### The code

```python
import pwn

# Set the architecture to amd64
pwn.context.update(arch="amd64")

# Create a process to interact with the level
process = pwn.process("/challenge/run")

# Assemble the assembly code and send it as raw bytes
process.write(pwn.asm("""
pop rax
sub rax, rdi
push rax
"""))
```

# Receive and print the output of the process
print(process.recvallS())


## Final Result

The stack will have its top value replaced with the result of subtracting the value in `rdi` from the original top value.

The flag for this level is: `pwn.college{M_GtNRp_KIwJdQGQqgDzQuVqjch.01NwIDLxUjNyEzW}`.
