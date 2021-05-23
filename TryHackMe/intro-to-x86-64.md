# Intro to x86-64
The room was rather beginner-friendly and self-explanatory. However, it had two ***crackme*** challenges as task 6 (crackme1) and task 7 (crackme2). In the write-up, I will be explaining my approach to solving these challenges. On a side note, I am not an expert on reverse engineering and have just recently begun to explore.

## crackme1 (Task 6)
After deploying the machine, we are asked to connect to it with ssh because the **r2** framework comes installed with the deployed machine. In order to ssh into a machine, we use the **ssh** command. For simplicity basic syntax of ssh command is:
```
ssh [OPTIONS] [USER@]:HOST
```

> For more information about ssh, you can visit:
> https://linuxize.com/post/ssh-command-in-linux/

In short, I used the command below to ssh into the machine.
```console
kuantuna@ubuntu:~$ ssh tryhackme@10.10.177.43
```

## crackme2 (Task 7)
