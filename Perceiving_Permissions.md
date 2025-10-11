# Perceiving Permissions

This module tells us about the permissions in Linux and how to access files across different users.

---

## Changing File Ownership

**This challenge teaches us about ownership of flag and changing original file name into `hacker`.**

### My Solve

**flag:**

```
pwn.college{8KmyDVKL6wvkRFref41CkCMzPgW.QXxEjN0wSNxIzNzEzW}
```

```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -1 /flag
/flag
hacker@permissions~changing-file-ownership:~$ ls -l /flag
-r-------- 1 hacker root 60 Oct  6 14:57 /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{8KmyDVKL6wvkRFref41CkCMzPgW.QXxEjN0wSNxIzNzEzW}
```

### What I Learned

How to take ownership of the flag and retrieve it.

**Reference:** pwn.college

---

## Grouping And Files

**This challenge teaches us how to own and group files.**

### My Solve

**flag:**

```
pwn.college{k1P5gvL2LvL01WnVX8tT9JiU0tp.QXxcjM1wSNxIzNzEzW}
```

```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root hacker 60 Oct  6 14:59 /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{k1P5gvL2LvL01WnVX8tT9JiU0tp.QXxcjM1wSNxIzNzEzW}
```

### What I Learned

How to own and group files.

**Reference:** pwn.college

---

## Fun With Groups Names

**This challenge teaches us to use `id` command and have fun with the names.**

### My Solve

**flag:**

```
pwn.college{A9sdFn80EqsIBtcQNfxsB1j66fa.QXycjM1wSNxIzNzEzW}
```

```bash
hacker@permissions~fun-with-groups-names:~$ id -gn
grp8490
hacker@permissions~fun-with-groups-names:~$ chgrp "$(grp8498)" /flag
bash: grp8498: command not found
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /glag
chgrp: cannot access '/glag': No such file or directory
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /flag
hacker@permissions~fun-with-groups-names:~$ la -l /flag
bash: la: command not found
hacker@permissions~fun-with-groups-names:~$ ls -l /flag
-r--r----- 1 root grp8490 60 Oct  6 15:00 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{A9sdFn80EqsIBtcQNfxsB1j66fa.QXycjM1wSNxIzNzEzW}
```

### What I Learned

How to use `id` command, have fun with group names, and use the `chgrp` command.

**Reference:** pwn.college

---

## Changing Permissions

**Teaches us how to change permissions using `chmod` command.**

### My Solve

**flag:**

```
pwn.college{wISQaSuOyZ7eibaf2UYt3IEJ2DZ.QXzcjM1wSNxIzNzEzW}
```

```bash
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-----r-- 1 root root 60 Oct  6 15:03 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{wISQaSuOyZ7eibaf2UYt3IEJ2DZ.QXzcjM1wSNxIzNzEzW}
```

### What I Learned

How to use `chmod` command and change permissions.

**Reference:** pwn.college

---

## Executable Files

**Teaches us how to execute files using `chmod`.**

### My Solve

**flag:**

```
pwn.college{ghA3tfgffp8XyQPTMIduJbs6YAU.QXyEjN0wSNxIzNzEzW}
```

```bash
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr-xr-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{ghA3tfgffp8XyQPTMIduJbs6YAU.QXyEjN0wSNxIzNzEzW}
```

### What I Learned

How to use `chmod` to make files executable.

**Reference:** pwn.college

---

## Permission Tweaking Practice

**This challenge is a game of clues.**

### My Solve

**flag:**

```
pwn.college{81iNsOZzmgjrMgCGP0SOyX4J0rX.QXwEjN0wSNxIzNzEzW}
```

```bash
# (Long interactive session omitted here for brevity in the code block)
# The session shows a sequence of chmod/stat/ls commands across 8 rounds
# culminating in changing /flag permissions and reading the flag.

# Key final steps from the session:
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /flag
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-------r-- 1 hacker hacker 60 Oct  6 15:07 /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
cat: /flag: Permission denied
...
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-r-----r-- 1 hacker hacker 60 Oct  6 15:07 /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{81iNsOZzmgjrMgCGP0SOyX4J0rX.QXwEjN0wSNxIzNzEzW}
```

### What I Learned

How to play the permissions-tweaking game and interpret the clues.

**Reference:** pwn.college

---

## Permissions Setting Practice

**This challenge is similar to the previous challenge.**

### My Solve

**flag:**

```
pwn.college{8fl6Qv9Thp-VzSt0EVHUzgWrTFT.QXzEjN0wSNxIzNzEzW}
```

```bash
# Another interactive 8-round chmod challenge sequence; important excerpts follow:
hacker@permissions~permissions-setting-practice:~$ chmod 701 /challenge/pwn
You set the correct permissions!
Round 2 of 8!
...
Round 8 of 8!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

hacker@permissions~permissions-setting-practice:~$ chmod u+r /flag
hacker@permissions~permissions-setting-practice:~$ ls -l /flag
-r-------- 1 hacker hacker 60 Oct  7 08:00 /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{QgYu1i3-NvPUBT_RBKdoTqG9ke9.QXzETO0wSNxIzNzEzW}
```

---

## The SUID Bit

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwsr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# id
uid=0(root) gid=1000(hacker) groups=1000(hacker)
root@permissions~the-suid-bit:~# whoami
root
root@permissions~the-suid-bit:~# cat /root/flag 2>/dev/null || cat /flag 2>/dev/null
pwn.college{8fl6Qv9Thp-VzSt0EVHUzgWrTFT.QXzEjN0wSNxIzNzEzW}
```

### What I Learned

Just like previous challenge: how to use SUID to run a binary as root and read root-owned flags.

**Reference:** pwn.college

---

## Markdown Formatting Notes

* All interactive terminal sessions are preserved as code blocks so they can be copied and reproduced.
* Flags are shown in fenced code blocks for clarity.

---











