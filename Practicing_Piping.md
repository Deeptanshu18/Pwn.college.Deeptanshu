#Practicing Piping
This module teaches about input and output redirection

## Redirecting Output
What the challenge asks: Write the word `PWN` (uppercase) into a file named `COLLEGE` using stdout redirection, then capture the challenge output into a file to receive the flag.

**Flag:** `pwn.college{Q6EzgvjrS7ma0gqFph0be-rzb04.QX0YTN0wSN0EzNzEzW}`

hacker@piping~redirecting-output:~$ echo PWN >COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your flag:
pwn.college{Q6EzgvjrS7ma0gqFph0be-rzb04.QX0YTN0wSN0EzNzEzW}


### My solve
Used `echo PWN >COLLEGE` to create the required file and capture output.

### What I learned
`>` redirects stdout (fd 1) and truncates the target file.

### References
bash I/O redirection docs.


## Redirecting More Output
What the challenge asks: Redirect the stdout of `/challenge/run` into a file named `myflag` so the challenge writes the flag into that file.

**Flag:** `pwn.college{0CNDloLG9d_zC2Ab3rJS186mH0w.QX1YTN0wSN0EzNzEzW}`


hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{0CNDloLG9d_zC2Ab3rJS186mH0w.QX1YTN0wSN0EzNzEzW}


### My solve
Ran `/challenge/run > myflag` then `cat myflag` to read the flag.

### What I learned
Some programs only print secret output to stdout; redirecting is required to capture it.

### References
bash redirection reference.


## Appending Output
What the challenge asks: Use append-mode redirection so that a direct file write and a later stdout write combine into one file to produce the full flag.

**Flag:** `pwn.college{wIuC1lO2ZTA1q7-1MiErnFvAJtD.QX3ATO0wSN0EzNzEzW}`

hacker@piping~appending-output:~$ /challenge/run > /home/hacker/the-flag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
pwn.college{wIuC1lO2ZTA1q7-1MiErnFvAJtD.QX3ATO0wSN0EzNzEzW}


### My solve
Used `>` for the first write and `>>` to append the second write so both halves join in the same file.

### What I learned
`>>` appends instead of overwriting — important when programs write in multiple steps/channels.

### References
I/O redirection docs.

## Redirecting Errors
What the challenge asks: Redirect stdout into `myflag` and stderr into `instructions` so both streams are captured separately; read the flag from `myflag`.

**Flag:** `pwn.college{gncW8Nyhwx021zZuZOD9Tek7U62.QX3YTN0wSN0EzNzEzW}`


hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag
[FLAG] Here is your flag:
[FLAG] pwn.college{gncW8Nyhwx021zZuZOD9Tek7U62.QX3YTN0wSN0EzNzEzW}

### My solve
Used `>` and `2>` to capture stdout and stderr in separate files, then inspected the flag file.

### What I learned
`2>` redirects stderr (fd 2) independently of stdout (fd 1).

### References
File descriptor conventions.


## Redirecting Input
What the challenge asks: Create a file `PWN` containing `COLLEGE` and run `/challenge/run` with stdin redirected from that file so the program reads `COLLEGE` and returns the flag.

**Flag:** `pwn.college{cdwoL5YhDa8zddM-oIgsgDWrFiZ.QXwcTN0wSN0EzNzEzW}`

hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{cdwoL5YhDa8zddM-oIgsgDWrFiZ.QXwcTN0wSN0EzNzEzW}

### My solve
Wrote `COLLEGE` into `PWN` and used `< PWN` to feed it as stdin.

### What I learned
`< file` supplies file contents to a program’s stdin — useful for automating input.

### References
stdin redirection docs.


## Grepping Stored Results
What the challenge asks: Redirect /challenge/run stdout into /tmp/data.txt, then search that file for the flag using grep

**Flag:** pwn.college{gLqi3tLxUZfs-Fl_wKPYofumrI8.QX4EDO0wSN0EzNzEzW}

hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep "pwn.college." /tmp/data.txt
pwn.college{gLqi3tLxUZfs-Fl_wKPYofumrI8.QX4EDO0wSN0EzNzEzW}

### My solve
Saved the challenge output to /tmp/data.txt and used grep to extract the flag.

### What I learned
Persisting output helps when the program outputs huge logs or many lines.

### References
grep usage.


## Grepping Live Output
What the challenge asks: Pipe /challenge/run directly into grep to find the flag without writing intermediate files.

**Flag:** pwn.college{A9nO4AzGgx0IkatTPrHsXi6SQG1.QX5EDO0wSN0EzNzEzW}

hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
pwn.college{A9nO4AzGgx0IkatTPrHsXi6SQG1.QX5EDO0wSN0EzNzEzW}

### My solve
Used a pipe (|) to stream stdout directly into grep.

### What I learned
Pipes avoid temp files and are efficient for streaming analysis.

### References
Pipelines & streams documentation.


## Grepping Errors
What the challenge asks: Capture the program's **stderr** and search it for the flag by redirecting stderr into stdout and piping to grep.

**Flag:** pwn.college{QBbBzfN-L70Cacjg5-BPL-XcZcC.QX1ATO0wSN0EzNzEzW}

hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
pwn.college{QBbBzfN-L70Cacjg5-BPL-XcZcC.QX1ATO0wSN0EzNzEzW}

### My solve
Merged stderr into stdout with 2>&1 then piped the combined stream into grep:

/challenge/run 2>&1 | grep pwn.college

### What I learned
- 2>&1 merges fd 2 into fd 1 so pipes receive both streams.  
- Ordering matters: perform the merge before piping.

### References
Shell redirection idioms.


## Filtering with grep -v
What the challenge asks: Use grep -v to filter out decoy lines and show only the real flag.

**Flag:** pwn.college{o8WY2O_zkDCQ3COGVoihkbsc5F2.0FOxEzNxwSN0EzNzEzW}

hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{o8WY2O_zkDCQ3COGVoihkbsc5F2.0FOxEzNxwSN0EzNzEzW}

### My solve
Used inverted match grep -v decoy to exclude noise lines containing the word decoy, revealing the flag.

### What I learned
grep -v filters out unwanted lines — useful for removing decoy/junk output.

### References
grep manual (-v option).


## Duplicating piped data with tee
What the challenge asks: Duplicate a stream into two programs simultaneously while intercepting the data locally (use `tee` + process substitution) so you can see what `pwn` needs and pass it to `college`.

**Flag:** pwn.college{wJ8JIqFgspGLAOxw9jsTsVFisMJ.QXxITO0wSN0EzNzEzW}

hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee taty | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code!
hacker@piping~duplicating-piped-data-with-tee:~$ cat taty
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "wJ8JIqFg"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret wJ8JIqFg | tee taty | /challenge/college
Processing...
WARNING: you are overwriting file taty with tee's output...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{wJ8JIqFgspGLAOxw9jsTsVFisMJ.QXxITO0wSN0EzNzEzW}
```

### My solve
Intercepted the `pwn` output with `tee` to read the secret, then re-ran with the secret passed to `pwn`, piping into `college` to obtain the flag.

### What I learned
- `tee` duplicates a stream to stdout and one or more files.  
- `>(cmd)` process substitution routes a stream into a command.  
- Useful debugging technique for chained pipelines.

### References
`tee` docs; process substitution notes.


# process-substitution

**What the challenge asks:** Use **process substitution** to compare outputs of two commands as if they were files and find the real flag hidden among decoys.

**Flag:** `pwn.college{UOsLFSS6Ls_p6VvA7GGfvApImgi.0lNwMDOxwSN0EzNzEzW}`

## My solve
I used input process substitution so `diff` could compare the output of two commands without creating temporary files:

```bash
diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
```

Explanation:
- `<(command)` creates a **temporary named pipe** (`/dev/fd/...`) connected to the command's stdout.  
- `diff` reads from these pseudo-files and shows the difference between the streams.  
- The added line in `/challenge/print_decoys_and_flag` revealed the flag.

## What I learned
- `<(command)` lets you treat command output as a readable file argument.  
- Useful for tools that accept filenames (like `diff`) to compare dynamic outputs without creating temp files.  
- Process substitution uses **named pipes**, which exist only in memory while commands run.

## References
- `bash` process substitution documentation  
- `diff` manpage

## Process Substitution for Input
**What the challenge asks:** Use **process substitution** to make the outputs of two commands appear like files, and `diff` those pseudo-files to reveal the added line containing the real flag.

**Flag:** `pwn.college{UOsLFSS6Ls_p6VvA7GGfvApImgi.0lNwMDOxwSN0EzNzEzW}`

```wsl
hacker@piping~process-substitution-for-input:~$ diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
64a65
> pwn.college{UOsLFSS6Ls_p6VvA7GGfvApImgi.0lNwMDOxwSN0EzNzEzW}
```

### My solve
I used input process substitution so `diff` could compare **command outputs** as if they were files:

```bash
diff <( /challenge/print_decoys ) <( /challenge/print_decoys_and_flag )
```

`bash` replaced each `<(cmd)` with a `/dev/fd/...` path connected to the command's stdout. `diff` printed the extra line in the second stream — that line was the flag.

### What I learned
- `<(command)` lets you treat command output as a readable file argument.  
- Useful for tools that accept filenames (like `diff`) so you can compare dynamic outputs without creating temporary files.  
- Process substitution uses named pipes (e.g., `/dev/fd/63`) under the hood.

### References
`bash` process substitution documentation; `diff` manpage.


## writing-to-multiple-programs
**What the challenge asks:** Duplicate the output of `/challenge/hack` so the data becomes the **stdin of both** `/challenge/the` and `/challenge/planet` simultaneously (use `tee` + output process substitution).

**Flag:** `pwn.college{snzOsMISgdvaDpcPkEaLYmW-56n.QXwgDN1wSN0EzNzEzW}`

```wsl
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
5756121732687527505
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{snzOsMISgdvaDpcPkEaLYmW-56n.QXwgDN1wSN0EzNzEzW}
```

### My solve
I used `tee` with **output** process substitution `>(cmd)` so `tee` wrote the stream to multiple named pipes (each connected to a command's stdin) while still writing to stdout:

```bash
/challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
```

This launched `/challenge/the` and `/challenge/planet` with their stdin attached to the temporary pipes; `tee` duplicated the incoming data into both.

### What I learned
- `>(command)` makes a writable filename that feeds `command`'s stdin — great for routing a single stream into multiple consumers.  
- `tee` combined with `>(...)` is a handy way to fan-out data into commands (not just files).

### References
`tee` manpage; process-substitution notes.


## split-piping-stderr-and-stdout
**What the challenge asks:** Run a program (`/challenge/hack`) that writes to both stdout and stderr, but **route stdout** into `/challenge/planet` and **route stderr** into `/challenge/the` — keeping the streams unmixed.

**Flag:** `pwn.college{QT2jj-Fz1ZIEfiLD4tVeaxbxphl.QXxQDM2wSN0EzNzEzW}`

hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{QT2jj-Fz1ZIEfiLD4tVeaxbxphl.QXxQDM2wSN0EzNzEzW}

### My solve
I combined **output process substitution** and stderr redirection so each stream went to a separate command:

```bash
/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```

Explanation:
- `> >( /challenge/planet )` — redirect stdout into the write-end of a pipe connected to `/challenge/planet`'s stdin.
- `2> >( /challenge/the )` — redirect stderr into the write-end of a pipe connected to `/challenge/the`'s stdin.
Because the process substitutions are separate, stdout and stderr remain unmixed but each reaches its intended command.

### What I learned
- You can route **separate** file descriptors to different process consumers using `>(...)` with `>` and `2>`.  
- This keeps streams separate (unlike `2>&1 |` which merges them).  
- Very useful pattern for sophisticated logging or multiplexed pipelines.

### References
File descriptor redirects, process substitution examples.


##named-pipes
What the challenge asks: Create a persistent FIFO at /tmp/flag_fifo and redirect /challenge/run stdout into it so the program writes the flag into the FIFO. Because FIFOs block until both ends are opened, read the FIFO from another process/terminal to receive the flag.

**Flag:** pwn.college{Q34fpfT54C1SfXkTkjEsLL_qBtf.01MzMDOxwSNxIzNzEzW}

### My solve
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo &   # background reader
/challenge/run > /tmp/flag_fifo 
[1] 149
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{Q34fpfT54C1SfXkTkjEsLL_qBtf.01MzMDOxwSNxIzNzEzW}
[1]+  Done                    cat /tmp/flag_fifo
hacker@piping~named-pipes:~$

## What I learned
- `mkfifo` creates a named FIFO you can open by path.  
- Writing to the FIFO (`> fifo`) blocks until a reader has opened the pipe; reading blocks until a writer is present.  
- Useful for inter-process coordination when you need named endpoints on the filesystem.

### References
`mkfifo` manpage; UNIX named pipe / FIFO documentation.
