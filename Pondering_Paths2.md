# Position Thyself — Path Navigation Exercises

This document contains formatted solutions for the **Position Thyself** module. Each challenge includes the flag, the terminal session (in a `bash` code block), a short explanation of the solve, and what was learned.

---

## Position Thyself

**Flag**

```
pwn.college{U8odpKZzpKP7Ymr_OKRAqBp-SSP.QX2QTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~position-thy-self:~$ /challlenge/run
bash: /challlenge/run: No such file or directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect... You are not currently in the /etc directory. Please use the cd utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /etc
hacker@paths~position-thy-self:/etc$ /challenge/run
Correct!!! /challenge/run is an absolute path, invoked from the right directory!
Here is your flag: pwn.college{U8odpKZzpKP7Ymr_OKRAqBp-SSP.QX2QTN0wSN0EzNzEzW}
```

**Summary**

A typo initially caused `No such file`; after correcting the path, the program required being in `/etc`. `cd /etc` fixed the current working directory and running `/challenge/run` returned the flag.

**What I learned**

Absolute paths are independent of CWD, but some programs check the CWD and require you to be in a specific directory.

---

## Position Elsewhere

**Flag**

```
pwn.college{8werDYWK62YL3kDj9U-jTXAW7GO.QX3QTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect... You are not currently in the /var directory. Please use the cd utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /var
hacker@paths~position-elsewhere:/var$ /challenge/run
Correct!!! /challenge/run is an absolute path, invoked from the right directory!
Here is your flag: pwn.college{8werDYWK62YL3kDj9U-jTXAW7GO.QX3QTN0wSN0EzNzEzW}
```

**Summary**

The program expects to be run from `/var` in this variant. `cd /var` satisfied the check and printed the flag.

**What I learned**

Some programs depend on the current working directory; switching directories with `cd` is essential.

---

## Position Yet Elsewhere

**Flag**

```
pwn.college{wrau69nZGt_M40evBMlxoXv6Wdr.QX4QTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect... You are not currently in the /usr/share/zoneinfo/posix/Asia directory. Please use the cd utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/zoneinfo/posix/Asia
hacker@paths~position-yet-elsewhere:/usr/share/zoneinfo/posix/Asia$ /challenge/run
Correct!!! /challenge/run is an absolute path, invoked from the right directory!
Here is your flag: pwn.college{wrau69nZGt_M40evBMlxoXv6Wdr.QX4QTN0wSN0EzNzEzW}
```

**Summary**

Navigated into a nested directory and ran `/challenge/run` — the program confirmed CWD and printed the flag.

**What I learned**

Practice navigating deep directory trees with `cd` and understanding path-based checks.

---

## Implicit Relative Paths From /

**Flag**

```
pwn.college{AwzfzgmxbIr9XpEMxVbw8yJcL3j.QX5QTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!! challenge/run is a relative path, invoked from the right directory!
Here is your flag: pwn.college{AwzfzgmxbIr9XpEMxVbw8yJcL3j.QX5QTN0wSN0EzNzEzW}
```

**Summary**

From `/`, invoking `challenge/run` (without a leading `/`) uses a relative path and executed successfully.

**What I learned**

Relative paths are resolved from the current working directory; they do not begin with `/`.

---

## Explicit Relative Paths From /

**Flag**

```
pwn.college{swkDgxCSjexUQwicdetM44p-UTT.QXwUTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!! ./challenge/run is a relative path, invoked from the right directory!
Here is your flag: pwn.college{swkDgxCSjexUQwicdetM44p-UTT.QXwUTN0wSN0EzNzEzW}
```

**Summary**

Using `./challenge/run` explicitly references the program in the current directory (`.`) and ran successfully.

**What I learned**

`.` denotes the current directory; `./program` explicitly runs `program` from CWD (useful when CWD isn’t in PATH).

---

## Implicit Relative Paths (from /challenge)

**Flag**

```
pwn.college{cBSbwq9RmotVUTV0iBXaKq00FCy.QXxUTN0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!! ./run is a relative path, invoked from the right directory!
Here is your flag: pwn.college{cBSbwq9RmotVUTV0iBXaKq00FCy.QXxUTN0wSN0EzNzEzW}
```

**Summary**

While inside `/challenge`, `./run` executed the local binary and returned the flag.

**What I learned**

Linux shells often do not search the current directory for executables unless explicitly referenced with `./`.

---

## Home Sweet Home

**Flag**

```
pwn.college{snx8nIwKVFiItcDbanROOeLL8Zk.QXzMDO0wSN0EzNzEzW}
```

**Terminal session / Code**

```bash
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a! ... and reading it back to you:
pwn.college{snx8nIwKVFiItcDbanROOeLL8Zk.QXzMDO0wSN0EzNzEzW}
```

**Summary**

Ran `/challenge/run ~/a` to instruct the program to write the flag to `/home/hacker/a` and print it back.

**What I learned**

* `~` expands to the current user's home directory.
* Programs accepting file arguments can write to user paths; use absolute or tilde-expanded paths as needed.

**References**

* Bash `cd`, path resolution, and `~` expansion documentation; pwn.college tutorials.

---


