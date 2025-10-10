# File Globbing — Matching & Tab Completion

A formatted write-up of the file-globbing challenges. Terminal commands and outputs are placed inside `bash` code blocks.

---

## matching-with-asterisk

**Flag**

```
pwn.college{cesz6jQkoW8ohqXSsPmezCVxWgp.QXxIDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{cesz6jQkoW8ohqXSsPmezCVxWgp.QXxIDO0wSN0EzNzEzW}
```

**My solve**

Used the `*` wildcard to match `/challenge` with `/ch*` for `cd`, then ran `/challenge/run`.

**What I learned**

* `*` matches any sequence of characters (except a leading `.` or `/`). Useful to shorten commands or match multiple files.

---

## matching-with-question-mark

**Flag**

```
pwn.college{4eRrpnZdyaCm7UlNrkm5lvsdwsT.QXyIDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{4eRrpnZdyaCm7UlNrkm5lvsdwsT.QXyIDO0wSN0EzNzEzW}
```

**My solve**

Used `?` as a single-character wildcard to match each character in `/challenge`.

**What I learned**

* `?` matches exactly one character. Useful for precise matching when filenames differ by a few letters.

---

## bracket-globbing

**Flag**

```
pwn.college{4SUAS0Gj4y7oISodgfkzfqc1SVd.QXzIDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~matching-with-:~$ /challenge/run file_[a,b,s,h]
You got it! Here is your flag!
pwn.college{4SUAS0Gj4y7oISodgfkzfqc1SVd.QXzIDO0wSN0EzNzEzW}
```

**My solve**

Used `[absh]` to match one character from the set for the filename.

**What I learned**

* `[]` allows limited wildcarding — matches any one character inside the brackets.

---

## absolute-path-bracket-globbing

**Flag**

```
pwn.college{k3qK2BMGAmz8OWIn26LIawvYjWc.QX0IDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{k3qK2BMGAmz8OWIn26LIawvYjWc.QX0IDO0wSN0EzNzEzW}
```

**My solve**

Used bracket globbing on an absolute path to match `/challenge/files/file_a`, `_b`, `_s`, or `_h`.

**What I learned**

* Globs work with full paths as well as filenames.

---

## multiple-globs

**Flag**

```
pwn.college{8Yq3JkluFmjh21VYhF_7ajZxgNn.0lM3kjNxwSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~multiple-globs:~$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{8Yq3JkluFmjh21VYhF_7ajZxgNn.0lM3kjNxwSN0EzNzEzW}
```

**My solve**

Used `*p*` to match all files containing `p`.

**What I learned**

* You can combine globs to match more complex patterns.

---

## mixing-globs

**Flag**

```
pwn.college{A17prNCplfZb8K81E9qsW96EAmM.QX1IDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
# amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
# beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{A17prNCplfZb8K81E9qsW96EAmM.QX1IDO0wSN0EzNzEzW}
```

**My solve**

Combined a bracket glob `[cep]` with `*` to match files that start with `c`, `e`, or `p`.

**What I learned**

* Mix `[]` with `*` for flexible patterns. Keep globbed arguments short when scripts require it.

---

## exclusionary-globbing

**Flag**

```
pwn.college{QlXLKbkUjrYokkFiLtY9MpCJ0Lu.QX2IDO0wSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~exclusionary-globbing:~$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{QlXLKbkUjrYokkFiLtY9MpCJ0Lu.QX2IDO0wSN0EzNzEzW}
```

**My solve**

Used `[^pwn]*` to exclude characters `p`, `w`, or `n` in the match.

**What I learned**

* `[^...]` negates characters inside the brackets.

---

# Tab Completion

## tab-completion-for-files

**Flag**

```
pwn.college{Ich3E-00GgBjKs66PTBRKqp8Qjc.0FN0EzNxwSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege
pwn.college{Ich3E-00GgBjKs66PTBRKqp8Qjc.0FN0EzNxwSN0EzNzEzW}
```

**My solve**

Used tab-completion to auto-complete the tricky filename.

**What I learned**

* Tab-completion prevents errors and saves typing.

---

## multiple-options-tab-completion

**Flag**

```
pwn.college{AMvtCYf05tQe0FKd3fSKP5dZOk_.0lN0EzNxwSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat ./pwncollege-flag
pwn.college{AMvtCYf05tQe0FKd3fSKP5dZOk_.0lN0EzNxwSN0EzNzEzW}
```

**My solve**

Used tab-completion and double-tab to list multiple matching options.

**What I learned**

* Double-Tab lists all options when multiple matches exist.

---

## tab-completion-on-commands

**Flag**

```
pwn.college{Ytit3XF4r2schLSQ34YqRbcAy6Y.0VN0EzNxwSN0EzNzEzW}
```

**Code / Solution**

```bash
hacker@globbing~tab-completion-on-commands:~$ pwncollege-1889
Correct! Here is your flag:
pwn.college{Ytit3XF4r2schLSQ34YqRbcAy6Y.0VN0EzNxwSN0EzNzEzW}
```

**My solve**

Used tab-completion for commands to auto-complete a flag-producing binary.

**What I learned**

* Tab-completion works for both filenames and commands.

---

**Reference**

* pwn.college

