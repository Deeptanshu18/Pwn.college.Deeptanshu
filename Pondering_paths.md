# Pondering Paths — Formatted Solutions

This document formats your write-up for the **Pondering Paths** module. Commands and terminal output are shown in `bash` code blocks for clarity.

---

## Overview

This module contains nine challenges: **The Root**, **Program and Absolute Paths**, **Position Thyself**, **Position Elsewhere**, **Position Yet Elsewhere**, **Implicit Relative Paths (from `/`)**, **Explicit Relative Paths (from `/`)**, **Implicit Relative Path (from `/challenge`)**, and **Home Sweet Home**.

---

## The Root

**Goal:** Launch the `pwn` program using its absolute path to get the flag.

**Flag**

```
pwn.college{0jUsizh9t8eV29Ko8Jva5FqYdG_.QX4cTO0wSNxIzNzEzW]
```

**Steps / Terminal session**

```bash
# connect via SSH (example)
ssh -i ./key hacker@dojo.pwn.college
# on success you will see the prompt, then:
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0jUsizh9t8eV29Ko8Jva5FqYdG_.QX4cTO0wSNxIzNzEzW]
```

**What I learned**

* The filesystem root is `/`.
* Important files and programs can be found directly under `/`.

**References**

* pwn.college
* YouTube tutorial linked in the challenge

---

## Program and Absolute Paths

**Goal:** Run `/challenge/run` to get the flag.

**Flag**

```
pwn.college{8Y30v7hyCEQuafbIkFvac9rVaF6.QX1QTN0wSNxIzNzEzW}
```

**Steps / Terminal session**

```bash
# connect via SSH (example)
ssh -i ./key hacker@dojo.pwn.college
# then run:
hacker@paths~program-and-absolute-paths:$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{8Y30v7hyCEQuafbIkFvac9rVaF6.QX1QTN0wSNxIzNzEzW}
```

**What I learned**

* How absolute paths work and how to invoke programs by absolute path.
* Basic directory concepts and running commands located in other directories.

**References**

* pwn.college
* ChatGPT (for clarifying directories and filesystem concepts)

---

## Position Thyself

*This section was left for you to continue — add your steps, flag, terminal output, and notes and I will format them the same way.*

---

