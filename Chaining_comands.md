###Chaining Commands
This module will help us to learn how to write shell scripts

##chaining with semicolons
This challenge teaches us to chain commands with semicolons

#My Solve
flag: pwn.college{06v186uETJLNB2ekxDXFHtWUW_s.QX1UDO0wSNxIzNzEzW}

hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{06v186uETJLNB2ekxDXFHtWUW_s.QX1UDO0wSNxIzNzEzW}

#What I Learned
how to chain commands with ';'

#References
pwn.college

##building on success
Learning how to use && in chains

#My Solve
flag: pwn.college{kvE9J2IzxnP81RHFWGKUZ2Xjz9D.0lM0MDOxwSNxIzNzEzW}

hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{kvE9J2IzxnP81RHFWGKUZ2Xjz9D.0lM0MDOxwSNxIzNzEzW}

#What I Learned
how to use && and proccessses module together

#References
pwn.college

##handling failure
how to use || in chains

#My Solve
flag: pwn.college{Iu5nN_4XOXHN2ytli3wB9MTiV84.01M0MDOxwSNxIzNzEzW}

hacker@chaining~handling-failure:~$ touch /tmp/.chained /tmp/.or && ls -l /tmp/.chained /tmp/.or && false || /challenge/second
-rw-r--r-- 1 hacker hacker 0 Oct  7 13:50 /tmp/.chained
-rw-r--r-- 1 hacker hacker 0 Oct  7 13:50 /tmp/.or
Nice chaining! Flag: pwn.college{Iu5nN_4XOXHN2ytli3wB9MTiV84.01M0MDOxwSNxIzNzEzW}

#What I Learned
How to use || condition to this

#References
pwn.college

##your first shell script
We learn how to use .sh command

#My Solve
flag: pwn.college{0a8hYkAHEiGhLe92HNgV38H663Y.QXxcDO0wSNxIzNzEzW}

hacker@chaining~your-first-shell-script:~$ cat > x.sh <<'SH'
> /challenge/pwn
> /challenge/college
> SH
hacker@chaining~your-first-shell-script:~$ chmod +x x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{0a8hYkAHEiGhLe92HNgV38H663Y.QXxcDO0wSNxIzNzEzW}

#What I learned
How to code inside a command using .sh command

#Reference
pwn.college
chatgpt (learning about .sh command)

##redirecting script output
We learn how to use piping in the chain

#My Solve
flag: pwn.college{0KCF2Y1vH5MYWoYBKS5noxSKPnV.QX4ETO0wSNxIzNzEzW}

hacker@chaining~redirecting-script-output:~$ cat > x.sh <<'SH'
> /challenge/pwn
> /challenge/college
> SH
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0KCF2Y1vH5MYWoYBKS5noxSKPnV.QX4ETO0wSNxIzNzEzW}

#What I Learned
How to use previously learned commands in piping module

#Refernce
pwn.college

##executable shell scripts
Teaches us why bash is in bash script.sh

#My Solve
flag: pwn.college{kpA0VIWaNznN13rirk2Lq1VlusR.QX0cjM1wSNxIzNzEzW}

hacker@chaining~executable-shell-scripts:~$ cat > runsolve.sh <<'SH'
> /challenge/solve
> SH
hacker@chaining~executable-shell-scripts:~$ chmod +x runsolve.sh
hacker@chaining~executable-shell-scripts:~$ ./runsolve.sh
Congratulations on your shell script execution! Your flag:
pwn.college{kpA0VIWaNznN13rirk2Lq1VlusR.QX0cjM1wSNxIzNzEzW}

#What I Learned
Why we use bash

#Reference
pwn.college
chatgpt(to understand more about the command)

##understanding shebangs
Teaches us how to invoke a command in python in a shell

#My Solve
flag: pwn.college{0YaDe1PJ2ak-fmgDHa7lewrMBqI.0VOzMDOxwSNxIzNzEzW}

hacker@chaining~understanding-shebangs:~$ cat > /home/hacker/solve.sh.new <<'SH'
> #!/bin/bash
> echo "hack the planet"
> SH
hacker@chaining~understanding-shebangs:~$ chmod +x /home/hacker/sovle.sh.new
chmod: cannot access '/home/hacker/sovle.sh.new': No such file or directory
hacker@chaining~understanding-shebangs:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~understanding-shebangs:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~understanding-shebangs:~$ sync
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{0YaDe1PJ2ak-fmgDHa7lewrMBqI.0VOzMDOxwSNxIzNzEzW}

#What I Learned
how to use .sh and .py

#Reference
pwn.college

##scripting with arguments
Teaches us how shell accepts arguments

#My Solve
flag: pwn.college{w557C9OA2c9cK9tXn__SkWR7UkH.0VNzMDOxwSNxIzNzEzW}

hacker@chaining~scripting-with-arguments:~$ cat > /home/hacker/solve.sh.new <<'SH'
> #!/bin/bash
> printf '%s %s\n' "$2" "$1"
> SH
hacker@chaining~scripting-with-arguments:~$ chmod +x /home/hacker/solve.sh.new
hacker@chaining~scripting-with-arguments:~$ mv -f /home/hacker/solve.sh.new /home/hacker/solve.sh
hacker@chaining~scripting-with-arguments:~$ sync
hacker@chaining~scripting-with-arguments:~$ /home/hacker/solve.sh pwn college
college pwn
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{w557C9OA2c9cK9tXn__SkWR7UkH.0VNzMDOxwSNxIzNzEzW}

#What I Learned
How a shell accepts arguments

#Reference
pwn.college
chatgpt(understanding more about the challenge)

##scripting with conditionals
Teaches us to use conditional operators in arguments in a shell

#My Solve
flag: pwn.college{seGD72W9lwxqAkXuLo1TN_2EnMA.0lNzMDOxwSNxIzNzEzW}

hacker@chaining~scripting-with-conditionals:~$ cat > /home/hacker/solve.sh.new <<'SH'
> #!/bin/bash
> if [ "$1" = "pwn" ]; then
> printf '%s\n' "college"
> fi
> SH
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

#What I Learned
How to make the arguments inside the shell smarter with conditonal operators

#Refernce
pwn.college

##scripting with default cases
Teaches us to use if else statements in an argument

#My Solve
flag: pwn.college{UKQWxFLI7-cTgyJD06TgXKHXGXO.01NzMDOxwSNxIzNzEzW}


hacker@chaining~scripting-with-default-cases:~$ cat > /home/hacker/solve.sh.new <<'SH'
> #!/bin/bash
> if [ "$1" = "pwn" ]; then
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

#What I Learned
How to use if else statements

#Reference
pwn.colege

##scripting with multiple conditions
Teaches us how to use elif after if and else statements in an argument

#My Solve
flag: pwn.college{sa2MVUxAFpo8EVKBv7dXjRjJNtW.0FOzMDOxwSNxIzNzEzW}

hacker@chaining~scripting-with-multiple-conditions:~$ cat > /home/hacker/solve.sh.new <<'SH'
> #!/bin/bash
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

#What I learned
How to use eluf statements

#Refernce
pwn.college

##reading shell scripts
Teaches us how to read shell scripts

#My Solve
flag: pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}

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
hacker@chaining~reading-shell-scripts:~$ grep -oP '"[^"]{6,200}"' /challenge/run | sed 's/^"//; s/"$//' | head -n 10
$GUESS
hack the PLANET
CORRECT! Your flag:
Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ printf 'hack the PLANET\n' | /challenge/run || printf 'hack the planet\n' | /challenge/run
CORRECT! Your flag:
pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}
hacker@chaining~reading-shell-scripts:~$ 

#What I Learned
How to read scripts

#Reference
pwn.college
chatgpt( to understand about the challenge)
