# Chaining Commands

This module covers writing simple shell scripts and chaining commands using `;`, `&&`, and `||`, plus argument handling and conditionals.

---

## chaining with semicolons

**Flag**

```
pwn.college{06v186uETJLNB2ekxDXFHtWUW_s.QX1UDO0wSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{06v186uETJLNB2ekxDXFHtWUW_s.QX1UDO0wSNxIzNzEzW}
```

**What I learned**

* How to chain commands with `;` (run commands sequentially, regardless of success).

---

## building on success

**Flag**

```
pwn.college{kvE9J2IzxnP81RHFWGKUZ2Xjz9D.0lM0MDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{kvE9J2IzxnP81RHFWGKUZ2Xjz9D.0lM0MDOxwSNxIzNzEzW}
```

**What I learned**

* Use `&&` to run the second command only if the first succeeds.

---

## handling failure

**Flag**

```
pwn.college{Iu5nN_4XOXHN2ytli3wB9MTiV84.01M0MDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~handling-failure:~$ touch /tmp/.chained /tmp/.or && ls -l /tmp/.chained /tmp/.or && false || /challenge/second
-rw-r--r-- 1 hacker hacker 0 Oct  7 13:50 /tmp/.chained
-rw-r--r-- 1 hacker hacker 0 Oct  7 13:50 /tmp/.or
Nice chaining! Flag: pwn.college{Iu5nN_4XOXHN2ytli3wB9MTiV84.01M0MDOxwSNxIzNzEzW}
```

**What I learned**

* Use `||` to run the right-hand command only if the left-hand command fails.

---

## your first shell script

**Flag**

```
pwn.college{0a8hYkAHEiGhLe92HNgV38H663Y.QXxcDO0wSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~your-first-shell-script:~$ cat > x.sh <<'SH'
/challenge/pwn
/challenge/college
SH
hacker@chaining~your-first-shell-script:~$ chmod +x x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{0a8hYkAHEiGhLe92HNgV38H663Y.QXxcDO0wSNxIzNzEzW}
```

**What I learned**

* How to create a simple `*.sh` script and run it with `bash`.

---

## redirecting script output

**Flag**

```
pwn.college{0KCF2Y1vH5MYWoYBKS5noxSKPnV.QX4ETO0wSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~redirecting-script-output:~$ cat > x.sh <<'SH'
/challenge/pwn
/challenge/college
SH
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0KCF2Y1vH5MYWoYBKS5noxSKPnV.QX4ETO0wSNxIzNzEzW}
```

**What I learned**

* Pipe script output to other commands for further processing.

---

## executable shell scripts

**Flag**

```
pwn.college{kpA0VIWaNznN13rirk2Lq1VlusR.QX0cjM1wSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~executable-shell-scripts:~$ cat > runsolve.sh <<'SH'
/challenge/solve
SH
hacker@chaining~executable-shell-scripts:~$ chmod +x runsolve.sh
hacker@chaining~executable-shell-scripts:~$ ./runsolve.sh
Congratulations on your shell script execution! Your flag:
pwn.college{kpA0VIWaNznN13rirk2Lq1VlusR.QX0cjM1wSNxIzNzEzW}
```

**What I learned**

* Make scripts executable with `chmod +x` so they can be run directly.

---

## understanding shebangs

**Flag**

```
pwn.college{0YaDe1PJ2ak-fmgDHa7lewrMBqI.0VOzMDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~understanding-shebangs:~$ cat > /home/hacker/solve.sh.new <<'SH'
#!/bin/bash
echo "hack the planet"
SH
hacker@chaining~understanding-shebangs:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~understanding-shebangs:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ sync
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{0YaDe1PJ2ak-fmgDHa7lewrMBqI.0VOzMDOxwSNxIzNzEzW}
```

**What I learned**

* Shebang (`#!`) tells the kernel which interpreter to use when executing a script.

---

## scripting with arguments

**Flag**

```
pwn.college{w557C9OA2c9cK9tXn__SkWR7UkH.0VNzMDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~scripting-with-arguments:~$ cat > /home/hacker/solve.sh.new <<'SH'
#!/bin/bash
printf '%s %s\n' "$2" "$1"
SH
hacker@chaining~scripting-with-arguments:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~scripting-with-arguments:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ sync
hacker@chaining~scripting-with-arguments:~$ /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{w557C9OA2c9cK9tXn__SkWR7UkH.0VNzMDOxwSNxIzNzEzW}
```

**What I learned**

* Access script arguments with `$1`, `$2`, etc.

---

## scripting with conditionals

**Flag**

```
pwn.college{seGD72W9lwxqAkXuLo1TN_2EnMA.0lNzMDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~scripting-with-conditionals:~$ cat > /home/hacker/solve.sh.new <<'SH'
#!/bin/bash
if [ "$1" = "pwn" ]; then
  printf '%s\n' "college"
fi
SH
hacker@chaining~scripting-with-conditionals:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~scripting-with-conditionals:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~scripting-with-conditionals:~$ sync
hacker@chaining~scripting-with-conditionals:~$ /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /home/hacker/solve.sh foo || true
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{seGD72W9lwxqAkXuLo1TN_2EnMA.0lNzMDOxwSNxIzNzEzW}
```

**What I learned**

* Use `if` tests (`[ ... ]`) inside scripts to branch behavior based on arguments.

---

## scripting with default cases

**Flag**

```
pwn.college{UKQWxFLI7-cTgyJD06TgXKHXGXO.01NzMDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~scripting-with-default-cases:~$ cat > /home/hacker/solve.sh.new <<'SH'
#!/bin/bash
if [ "$1" = "pwn" ]; then
  printf '%s\n' "college"
else
  printf '%s\n' "nope"
fi
SH
hacker@chaining~scripting-with-default-cases:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~scripting-with-default-cases:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~scripting-with-default-cases:~$ sync
hacker@chaining~scripting-with-default-cases:~$ /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ /home/hacker/solve.sh hack
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{UKQWxFLI7-cTgyJD06TgXKHXGXO.01NzMDOxwSNxIzNzEzW}
```

**What I learned**

* Use `if/else` to provide default cases when conditions aren't met.

---

## scripting with multiple conditions

**Flag**

```
pwn.college{sa2MVUxAFpo8EVKBv7dXjRjJNtW.0FOzMDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ cat > /home/hacker/solve.sh.new <<'SH'
#!/bin/bash
# multi-branch response (explicit and unambiguous)
if [ "$1" = "hack" ]; then
  printf '%s\n' "the planet"
elif [ "$1" = "pwn" ]; then
  printf '%s\n' "college"
elif [ "$1" = "learn" ]; then
  printf '%s\n' "linux"
else
  printf '%s\n' "unknown"
fi
SH
hacker@chaining~scripting-with-multiple-conditions:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~scripting-with-multiple-conditions:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ sync
hacker@chaining~scripting-with-multiple-conditions:~$ echo "---- /home/hacker/solve.sh ----"
---- /home/hacker/solve.sh ----
hacker@chaining~scripting-with-multiple-conditions:~$ sed -n '1,200p' /home/hacker/solve.sh
#!/bin/bash
# multi-branch response (explicit and unambiguous)
if [ "$1" = "hack" ]; then
  printf '%s\n' "the planet"
elif [ "$1" = "pwn" ]; then
  printf '%s\n' "college"
elif [ "$1" = "learn" ]; then
  printf '%s\n' "linux"
else
  printf '%s\n' "unknown"
fi
hacker@chaining~scripting-with-multiple-conditions:~$ echo "-------------------------------"
-------------------------------
hacker@chaining~scripting-with-multiple-conditions:~$ echo "test: hack ->";  /home/hacker/solve.sh hack
test: hack ->
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ echo "test: pwn  ->";  /home/hacker/solve.sh pwn
test: pwn  ->
college
hacker@chaining~scripting-with-multiple-conditions:~$ echo "test: learn->";  /home/hacker/solve.sh learn
test: learn->
linux
hacker@chaining~scripting-with-multiple-conditions:~$ echo "test: foo  ->";  /home/hacker/solve.sh foo
test: foo  ->
unknown
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{sa2MVUxAFpo8EVKBv7dXjRjJNtW.0FOzMDOxwSNxIzNzEzW}
```

**What I learned**

* Use `elif` to handle multiple branches.

---

## reading shell scripts

**Flag**

```
pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}
```

**Code / Solution**

```bash
hacker@chaining~reading-shell-scripts:~$ file /challenge/run
/challenge/run: setuid a /opt/pwn.college/bash script, ASCII text executable
hacker@chaining~reading-shell-scripts:~$ sed -n '1,200p' /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
	echo "CORRECT! Your flag:"
	cat /flag
else
	echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ # show lines that mention common names
grep -nE 'PASSWORD|PASS|SECRET|KEY|flag|pwn\.college|hardcoded|read -s|read -p' /challenge/run || true
1:#!/opt/pwn.college/bash
6:	echo "CORRECT! Your flag:"
7:	cat /flag
hacker@chaining~reading-shell-scripts:~$ grep -oP '([A-Za-z_]*PASSWORD[A-Za-z_]*|SECRET|KEY)[[:space:]]*=[[:space:]]*"\K[^"]+' /challenge/run || true
hacker@chaining~reading-shell-scripts:~$ grep -oP "([A-Za-z_]*PASSWORD[A-Za-z_]*|SECRET|KEY)[[:space:]]*=[[:space:]]*'\K[^']+" /challenge/run || true
hacker@chaining~reading-shell-scripts:~$ grep -oP 'pwn\.college\{[^}]+\}' /challenge/run || true
hacker@chaining~reading-shell-scripts:~$ grep -oP '"[^\"]{6,200}"' /challenge/run | sed 's/^"//; s/"$//' | head -n 10
$GUESS
hack the PLANET
CORRECT! Your flag:
Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ printf 'hack the PLANET\n' | /challenge/run || printf 'hack the planet\n' | /challenge/run
CORRECT! Your flag:
pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}
hacker@chaining~reading-shell-scripts:~$
```

**What I learned**

* How to inspect shell scripts with `file`, `sed`, `grep`, and run them with crafted input.

---

**References**

* pwn.college
* ChatGPT (used as clarification/reference)

