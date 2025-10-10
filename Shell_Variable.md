# Shell Variables — Formatted Solutions

This document formats your **Shell Variable** module. Each challenge includes the flag, the terminal session (in a `bash` code block), a short explanation of the solution, and what you learned.

---

## Printing Variables

**Flag**

```
pwn.college{kOK1xr4AcaGX7YcKrTrss-K5D6x.QX3UTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{kOK1xr4AcaGX7YcKrTrss-K5D6x.QX3UTN0wSNxIzNzEzW}
```

**What I learned**

* `echo $VAR` prints the value of a shell variable. The dollar sign (`$`) expands the variable.

**References**

* pwn.college

---

## Setting Variables

**Flag**

```
pwn.college{AZyYs0tB39btGRH45KES1SafCgL.QX5UTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~setting-variables:~$ export PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{AZyYs0tB39btGRH45KES1SafCgL.QX5UTN0wSNxIzNzEzW}
```

**What I learned**

* `export VAR=value` sets a variable in the current shell and marks it for inheritance by child processes.

**References**

* pwn.college

---

## Multi-Word Variables

**Flag**

```
pwn.college{gwx8y_A6_dkQ-72AyQsqi3tqh3C.QXwYTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gwx8y_A6_dkQ-72AyQsqi3tqh3C.QXwYTN0wSNxIzNzEzW}
```

**What I learned**

* Quote multi-word values (e.g., `VAR="two words"`) to preserve spacing.

**References**

* pwn.college

---

## Exporting Variables

**Flag**

```
pwn.college{8WO60TiTeRInL_t1eUnHXQJredL.QXyYTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
hacker@variables~exporting-variables:~$ COLLEGE=PWN
hacker@variables~exporting-variables:~$ sh -c 'echo "child sees: PWN=$PWN COLLEGE=$COLLEGE"'
child sees: PWN=COLLEGE COLLEGE=
...
/challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great job! Here is your flag:
pwn.college{8WO60TiTeRInL_t1eUnHXQJredL.QXyYTN0wSNxIzNzEzW}
```

**What I learned**

* Only exported variables are visible to child processes. Setting a variable without `export` makes it local to the current shell.

**References**

* pwn.college

---

## Printing Exported Variables

**Flag**

```
pwn.college{UF-va328jDDhxEmv1XhgJFDc5sa.QX4UTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~printing-exported-variables:~$ export FLAG
hacker@variables~printing-exported-variables:~$ env | grep '^FLAG='
FLAG=pwn.college{UF-va328jDDhxEmv1XhgJFDc5sa.QX4UTN0wSNxIzNzEzW}
```

**What I learned**

* Use `env` to list exported environment variables and `grep` to filter for a specific one.

**References**

* pwn.college

---

## Storing Command Output

**Flag**

```
pwn.college{EMAC2qVQZFFmIVRed0FB_ppML0j.QX1cDN1wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out and submit it!
hacker@variables~storing-command-output:~$ printenv PWN
pwn.college{EMAC2qVQZFFmIVRed0FB_ppML0j.QX1cDN1wSNxIzNzEzW}
```

**What I learned**

* Command substitution (`VAR=$(command)`) captures a command's output into a variable.

**References**

* pwn.college

---

## Reading Input

**Flag**

```
pwn.college{cfgrFC0Lh63cbBHr0FvH9QfcGEm.QX4cTN0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~reading-input:~$ read -p "Enter value: " PWN
Enter value: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cfgrFC0Lh63cbBHr0FvH9QfcGEm.QX4cTN0wSNxIzNzEzW}
```

**What I learned**

* Use `read` to get user input into a variable (e.g., `read -p "Prompt" VAR`).

**References**

* pwn.college

---

## Reading Files

**Flag**

```
pwn.college{sjkTR7UwL5scNfxfB5_J_9uGSZR.QXwIDO0wSNxIzNzEzW}
```

**Terminal session**

```bash
hacker@variables~reading-files:~$ read -r PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sjkTR7UwL5scNfxfB5_J_9uGSZR.QXwIDO0wSNxIzNzEzW}
```

**What I learned**

* Use input redirection (`read -r VAR < file`) to read the first line of a file into a variable.

**References**

* pwn.college

---

*Would you like this exported as a PDF or merged into the combined report with your other formatted modules?*
