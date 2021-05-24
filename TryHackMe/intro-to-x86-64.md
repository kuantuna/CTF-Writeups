# Intro to x86-64
The room was rather beginner-friendly and self-explanatory. However, it had two ***crackme*** challenges as task 6 (crackme1) and task 7 (crackme2). In the write-up, I will be explaining my approach to solving these challenges. On a side note, I am not an expert on reverse engineering and have just recently begun to explore.

## crackme1 (Task 6)
After deploying the machine, we are asked to connect to it with ssh because the **radare2** framework comes installed with the deployed machine. In order to ssh into a machine, we use the **ssh** command. For simplicity, basic syntax of ssh command is:
```
ssh [OPTIONS] USER@HOST
```

> For more information about ssh, you can visit:
> https://linuxize.com/post/ssh-command-in-linux/

In short, I used the command below to ssh into the machine.
```console
kuantuna@ubuntu:~$ ssh tryhackme@10.10.241.245
The authenticity of host '10.10.241.245 (10.10.241.245)' can't be established.
ECDSA key fingerprint is SHA256:TWskcUGZV64T745S4CFQqh0wLjy9J8XXQpbakRwlMJc.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
When we continue by saying yes, a password is asked.

```console
tryhackme@10.10.241.245's password:
```
and when we enter the **reismyfavl33t** password, we finally connect to the machine with ssh.
Afterwards, we go to the ***crackme folder*** and find 2 elf files named crackme1 and crackme2. For the first challenge, we will be reversing the crackme1. Normally it is wiser to analyze the file with file, strings, ltrace, etc. commands but in this case, because the purpose of the room is to learn radare2 framework, we will be analyzing the elf file directly with radare2. Let's check the man page of the radare2 before diving right into it.
```console
kuantuna@ubuntu:~$ man r2
RADARE2(1)                          BSD General Commands Manual                         RADARE2(1)

NAME
     radare2 — Advanced commandline hexadecimal editor, disassembler and debugger

SYNOPSIS
     radare2 [-a arch] [-b bits] [-B baddr] [-c cmd] [-e k=v] [-i file] [-I prefile] [-k kernel]
             [-m addr] [-p project] [-P patch] [-r rarun2] [-R rr2rule] [-s addr]
             [-0AdDwntLquvVxX] -|--|=|file

DESCRIPTION
     radare2 is a commandline hexadecimal editor.

     "r2" is the alias program name for radare2.

     This manpage is not updated yet. Feel free to contribute.

     The options are:
     .
     .
     .
     -d          Start in debugger mode
     .
     .
     .
```
-d flag will be important for us because we want to debug the crackme1 file. We will run the radare2 with the below command to debug crackme1.
```console
kuantuna@ubuntu:~$ r2 -d crackme1
Process with PID 1386 started...
= attach 1386 1386
bin.baddr 0x563e87f14000
Using 0x563e87f14000
asm.bits 64
 -- Most of commands accept '?' as a suffix. Use it to understand how they work :)
[0x7f8087359090]> 
```

## crackme2 (Task 7)
