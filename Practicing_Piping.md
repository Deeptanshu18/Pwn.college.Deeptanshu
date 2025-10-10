# Practicing Piping — Formatted Solutions

This module covers input/output redirection, pipes, process substitution, tee, and named pipes (FIFOs). Each challenge below includes the **goal**, **flag**, the **terminal session** (in a `bash` block), **what I learned**, and **references**.

---

## Redirecting Output

**Goal:** Write the word `PWN` into a file named `COLLEGE` using stdout redirection.

**Flag**

```
pwn.college{Q6EzgvjrS7ma0gqFph0be-rzb04.QX0YTN0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~redirecting-output:~$ echo PWN >COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your flag:
pwn.college{Q6EzgvjrS7ma0gqFph0be-rzb04.QX0YTN0wSN0EzNzEzW}
```

**What I learned**

* `>` redirects stdout (file descriptor 1) and truncates the target file.

**References**

* Bash I/O redirection docs

---

## Redirecting More Output

**Goal:** Redirect `/challenge/run` stdout into a file `myflag`.

**Flag**

```
pwn.college{0CNDloLG9d_zC2Ab3rJS186mH0w.QX1YTN0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{0CNDloLG9d_zC2Ab3rJS186mH0w.QX1YTN0wSN0EzNzEzW}
```

**What I learned**

* Programs may print secret output only to stdout — redirect to capture it.

**References**

* Bash redirection reference

---

## Appending Output

**Goal:** Use append (`>>`) so multiple writes accumulate in one file.

**Flag**

```
pwn.college{wIuC1lO2ZTA1q7-1MiErnFvAJtD.QX3ATO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~appending-output:~$ /challenge/run > /home/hacker/the-flag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
pwn.college{wIuC1lO2ZTA1q7-1MiErnFvAJtD.QX3ATO0wSN0EzNzEzW}
```

**What I learned**

* `>>` appends to a file instead of overwriting it.

**References**

* I/O redirection docs

---

## Redirecting Errors

**Goal:** Capture stdout into `myflag` and stderr into `instructions`.

**Flag**

```
pwn.college{gncW8Nyhwx021zZuZOD9Tek7U62.QX3YTN0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{gncW8Nyhwx021zZuZOD9Tek7U62.QX3YTN0wSN0EzNzEzW}
hacker@piping~redirecting-errors:~$ cat instructions
[PASS] Success! You have satisfied all execution requirements.
```

**What I learned**

* `2>` redirects stderr (file descriptor 2) separately from stdout.

**References**

* File descriptor conventions

---

## Redirecting Input

**Goal:** Put `COLLEGE` into file `PWN` and feed it to `/challenge/run` via stdin.

**Flag**

```
pwn.college{cdwoL5YhDa8zddM-oIgsgDWrFiZ.QXwcTN0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cdwoL5YhDa8zddM-oIgsgDWrFiZ.QXwcTN0wSN0EzNzEzW}
```

**What I learned**

* `< file` supplies data to a program's stdin (fd 0).

**References**

* stdin redirection docs

---

## Grepping Stored Results

**Goal:** Save `/challenge/run` output to `/tmp/data.txt` and search it with `grep`.

**Flag**

```
pwn.college{gLqi3tLxUZfs-Fl_wKPYofumrI8.QX4EDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep "pwn.college" /tmp/data.txt
pwn.college{gLqi3tLxUZfs-Fl_wKPYofumrI8.QX4EDO0wSN0EzNzEzW}
```

**What I learned**

* Persisting output is helpful for later analysis with tools like `grep`.

**References**

* `grep` usage

---

## Grepping Live Output

**Goal:** Pipe `/challenge/run` directly into `grep`.

**Flag**

```
pwn.college{A9nO4AzGgx0IkatTPrHsXi6SQG1.QX5EDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
pwn.college{A9nO4AzGgx0IkatTPrHsXi6SQG1.QX5EDO0wSN0EzNzEzW}
```

**What I learned**

* Pipes (`|`) stream stdout to another process's stdin without temporary files.

**References**

* Pipelines & streams docs

---

## Grepping Errors

**Goal:** Search stderr for the flag by merging stderr into stdout.

**Flag**

```
pwn.college{QBbBzfN-L70Cacjg5-BPL-XcZcC.QX1ATO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
pwn.college{QBbBzfN-L70Cacjg5-BPL-XcZcC.QX1ATO0wSN0EzNzEzW}
```

**What I learned**

* `2>&1` merges stderr into stdout. Order matters: do the merge before piping.

**References**

* Shell redirection idioms

---

## Filtering with grep -v

**Goal:** Remove decoy lines from output using `grep -v`.

**Flag**

```
pwn.college{o8WY2O_zkDCQ3COGVoihkbsc5F2.0FOxEzNxwSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{o8WY2O_zkDCQ3COGVoihkbsc5F2.0FOxEzNxwSN0EzNzEzW}
```

**What I learned**

* `grep -v` inverts matches to exclude lines containing a pattern.

**References**

* `grep` manual

---

## Duplicating Piped Data with tee

**Goal:** Intercept a pipeline with `tee`, inspect the stream, then pass it along.

**Flag**

```
pwn.college{wJ8JIqFgspGLAOxw9jsTsVFisMJ.QXxITO0wSN0EzNzEzW}
```

**Terminal (abridged)**

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee taty | /challenge/college
# inspect taty to see secret
cat taty
# then re-run with the secret
/challenge/pwn --secret wJ8JIqFg | tee taty | /challenge/college
# flag printed
```

**What I learned**

* `tee` writes a stream to a file and also to stdout; useful for debugging pipelines.
* Process substitution and `tee` let you inspect intermediate pipeline data.

**References**

* `tee` docs; process substitution notes

---

## Process Substitution (diff)

**Goal:** Compare outputs of two commands as files using `<(command)`.

**Flag**

```
pwn.college{UOsLFSS6Ls_p6VvA7GGfvApImgi.0lNwMDOxwSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~process-substitution-for-input:~$ diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
64a65
> pwn.college{UOsLFSS6Ls_p6VvA7GGfvApImgi.0lNwMDOxwSN0EzNzEzW}
```

**What I learned**

* `<(cmd)` exposes command output as a pseudo-file (`/dev/fd/*`), enabling tools that expect filenames to compare live output.

**References**

* `bash` process substitution docs; `diff` manpage

---

## Writing to Multiple Programs

**Goal:** Use `tee` with output process substitution to feed the same stream into two commands.

**Flag**

```
pwn.college{snzOsMISgdvaDpcPkEaLYmW-56n.QXwgDN1wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
# both commands receive the streamed input simultaneously
```

**What I learned**

* `>(command)` creates a writable pipe that feeds `command`'s stdin. `tee` can duplicate a stream into multiple such pipes.

**References**

* `tee` manpage; process substitution examples

---

## Split Piping stdout and stderr

**Goal:** Route stdout to one command and stderr to another, keeping streams separate.

**Flag**

```
pwn.college{QT2jj-Fz1ZIEfiLD4tVeaxbxphl.QXxQDM2wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```

**What I learned**

* Use `> >(cmd)` and `2> >(cmd)` together to deliver different file descriptors to separate consumers.
* Keeps stdout and stderr unmixed while still piping both to programs.

**References**

* File descriptor redirects; process substitution

---

## Named Pipes (FIFOs)

**Goal:** Create a persistent FIFO at `/tmp/flag_fifo`, write program output into it, and read from another process.

**Flag**

```
pwn.college{Q34fpfT54C1SfXkTkjEsLL_qBtf.01MzMDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo &   # background reader
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
# reader receives the data and prints the flag
```

**What I learned**

* `mkfifo` creates a named pipe. Reads/writes block until both ends are opened. Great for explicit inter-process coordination.

**References**

* `mkfifo` manpage; UNIX FIFO docs

---

*Would you like this exported as a PDF or merged into your master study guide?*
