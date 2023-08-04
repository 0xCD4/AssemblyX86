## ASMLevel1 - Set rdi to 0x1337

In this challenge, we are asked to set the value of the `rdi` register to `0x1337`.


```python

In [1]: import pwn

In [2]: pwn.context.update(arch="amd64")

In [3]: process = pwn.process("/challenge/run")
[x] Starting local process '/challenge/run'
[+] Starting local process '/challenge/run': pid 16174

In [4]: process.write(pwn.asm("mov rdi, 0x1337"))

In [5]: print(process.readallS)
<bound method tube.make_wrapper.<locals>.wrapper of <pwnlib.tubes.process.process object at 0x7f6c2b7f5490>>

In [6]: print(process.readallS())

```





### Assembly Code

```assembly
mov rdi, 0x1337

```
The flag: pwn.college{wUq-SZ2pI8PzOngxTUggABzrET-.0FN5EDLxUjNyEzW}
