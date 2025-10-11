# Untangling Users — Formatted Solutions

This module explores user identity and privilege escalation on Linux (`su`, `sudo`, password cracking, switching users). Each challenge contains the **goal**, **flag**, the **terminal session** (in a `bash` code block), **what I learned**, and **references**.

---

## Becoming Root with `su`

**Goal:** Become `root` using `su` and read the flagged file.

**Flag**

```
pwn.college{k_t0eOmMJ2LVm-1a0sJHPJo3Xdf.QX1UDN1wSNxIzNzEzW}
```

**Terminal**

```bash
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls
# ...listing shows not-the-flag file...
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
pwn.college{k_t0eOmMJ2LVm-1a0sJHPJo3Xdf.QX1UDN1wSNxIzNzEzW}
```

**What I learned**

* `su` switches to another user (default `root`) with the target user’s password. Once root, you can access privileged files.

**References**

* pwn.college

---

## Other Users with `su - username`

**Goal:** Switch to a specific user (`zardus`) and run the challenge binary.

**Flag**

```
pwn.college{s5sl-QFUfKJdZGY0mFsMxKD2Rg6.QX2UDN1wSNxIzNzEzW}
```

**Terminal**

```bash
hacker@users~other-users-with-su:~$ su - zardus
Password:
zardus@users~other-users-with-su:~$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{s5sl-QFUfKJdZGY0mFsMxKD2Rg6.QX2UDN1wSNxIzNzEzW}
```

**What I learned**

* `su - username` switches to another user and loads their login environment.

**References**

* pwn.college

---

## Cracking Passwords (john)

**Goal:** Use `john` to crack leaked password hashes, then `su` to log in as that user.

**Flag**

```
pwn.college{M7mA3cv-9HEoS3iWWO4s4TuuNvg.QX3UDN1wSNxIzNzEzW}
```

**Terminal (abridged)**

```bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
# john cracks the hash and reports the password (e.g., 'aardvark' or similar)
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{M7mA3cv-9HEoS3iWWO4s4TuuNvg.QX3UDN1wSNxIzNzEzW}
```

**What I learned**

* `john` (John the Ripper) can crack weak hashes found in leaked files; compromised credentials let you switch users.
* Always protect password hashes and use strong passwords.

**References**

* pwn.college
* John the Ripper

---

## Using `sudo`

**Goal:** Use `sudo` to run commands as root (or other users) without a password when permitted.

**Flag**

```
pwn.college{QdoqBazlbZMF55uBMHg9ZU16NKt.QX4UDN1wSNxIzNzEzW}
```

**Terminal**

```bash
hacker@users~using-sudo:~$ sudo -l
User hacker may run the following commands on users~using-sudo:
    (ALL) NOPASSWD: ALL
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{QdoqBazlbZMF55uBMHg9ZU16NKt.QX4UDN1wSNxIzNzEzW}
```

**What I learned**

* `sudo` executes commands as another user (commonly root). `NOPASSWD` in `/etc/sudoers` allows running permitted commands without supplying a password.
* `sudo` provides finer-grained and auditable privilege delegation compared to `su`.

**References**

* pwn.college
* `man sudo`

---


