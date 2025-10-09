###Challanges
This is for 3 challanges i found difficult to solve


1) Reading Shell Scripts (Chaining Commands)
> Code for this challenge is
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
hacker@chaining~reading-shell-scripts:~$ grep -oP '"[^"]{6,200}"' /challenge/run | sed 's/^"//; s/"$//' | head -n 10
$GUESS
hack the PLANET
CORRECT! Your flag:
Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ printf 'hack the PLANET\n' | /challenge/run || printf 'hack the planet\n' | /challenge/run
CORRECT! Your flag:
pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}

'''
Way:
a) I wasn't able to understand what the challenge required
b) I tried using some stuff used in the previous challenges in this module
c) But that wasn't enough and wasn't giving answers
d) Then i tried a python program of simple if else statement 
e) But that also wasn't enough 
f) Then i asked chatgpt to help me understand what actually is required 
g) Then i tried using echo with other commands
h) Then i understood what to use in echo and types the commands
i) And then it become simple and i just had to run /challenge/run
j) Then i got my answer
k) It took me 2 days to finish it 
l) I had taken help from my friends who had done it but that help wasn't good enough as they had just helped me understanding the challenge just like what i asked chatgpt
m) After getting answer it became easier to continue the rest of the challenges
n) The thing which made this challenge difficult for me was mixing python statements and getting confused in echo statements together



2) Permission Tweakening Practice (Perceiving Permissions)
> Code:
'''
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-rw-r--r-- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ stat -c "%A %a" /challenge/pwn
-rw-r--r-- 644
hacker@permissions~permission-tweaking-practice:~$ chmod u=rwx, g-r, o= /challenge/run
/usr/bin/chmod: invalid mode: ‘u=rwx,’
Try '/usr/bin/chmod --help' for more information.
NEEDED, BUT UNMET permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permission-tweaking-practice:~$ chmod u=rwx, g-r, o= /challenge/pwn
/usr/bin/chmod: invalid mode: ‘u=rwx,’
Try '/usr/bin/chmod --help' for more information.
NEEDED, BUT UNMET permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permission-tweaking-practice:~$ chmod 640 /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u=rw, g=r, o= /challenge/pwn
/usr/bin/chmod: invalid mode: ‘u=rw,’
Try '/usr/bin/chmod --help' for more information.
NEEDED, BUT UNMET permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permission-tweaking-practice:~$ chmod 640 /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-rw-r----- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 640 /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permission-tweaking-practice:~$ chmod 640 /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rw-r-----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-rw-r----- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 600 /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--------
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-rw------- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 400 /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": r--------
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-----rwx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-r-------- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 407 /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r-----rwx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-------x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-r-----rwx 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 401 /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r-------x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--------
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-r-------x 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 400 /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": r--------
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-r-------- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 000 /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw----rw-
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
---------- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod 606 /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ls -l /challenge/pwn
-rw----rw- 1 hacker hacker 0 Oct  6 15:07 /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /flag
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-------r-- 1 hacker hacker 60 Oct  6 15:07 /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~permission-tweaking-practice:~$ whoami
hacker
hacker@permissions~permission-tweaking-practice:~$ ls -ld /flag
-------r-- 1 hacker hacker 60 Oct  6 15:07 /flag
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /flag
hacker@permissions~permission-tweaking-practice:~$ ls -l /flag
-r-----r-- 1 hacker hacker 60 Oct  6 15:07 /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{81iNsOZzmgjrMgCGP0SOyX4J0rX.QXwEjN0wSNxIzNzEzW}
'''

>Way:
a) I found this challenge hard
b) The challenge looked simple and i thought i had only 8 chances
c) Then i realised that i need to do 8 rounds and after that i need to retrieve flag
d) First i started the challenge with /challenge/run
e) Then I tried to list it and use a command which would be helpful for the next challenge in this module also so i thought we could use in this also 
f) That turned to incorrect
g) Then i understood every clue it gave had a specific number or PID related to it
h) I had tried to check if it is given in the module in any challenge, but i could find only less so I had to check in google or chatgpt to find the number related to it
i) It worked and 2nd round worked and i listed it 
j) The i used the clue for round 2 for round 3 and so on
k) Though the challenge is easy, but i had gotten confused and made it tough for myself
l) I kept of getting clues till round 8
m) Then it showed all rounds are done
n) After that it became easy and i had used 'chmod' , listing and 'cat' to retrieve the flag



3) The Path Variable (Pondering Path)
> Code:
'''
hacker@path~the-path-variable:~$ ORIG_PATH="$PATH"
hacker@path~the-path-variable:~$ /bin/mkdir -p /tmp/fakebin
hacker@path~the-path-variable:~$ /bin/cat > /tmp/fakebin/rm <<'EOF'
> #!/bin/sh
if [ -e /flag ]; then
  /bin/cp -a /flag /tmp/flag.backup 2>/dev/null || /bin/echo "backup copy failed" >/dev/null
  /bin/chmod 644 /tmp/flag.backup 2>/dev/null || /bin/echo "chmod failed" >/dev/null
fi
exit 0
EOF
hacker@path~the-path-variable:~$ /bin/chmod +x /tmp/fakebin/rm
hacker@path~the-path-variable:~$ export PATH="/tmp/fakebin:$PATH"
hacker@path~the-path-variable:~$ hash -r
hacker@path~the-path-variable:~$ /bin/echo "CURRENT PATH: $PATH"
CURRENT PATH: /tmp/fakebin:/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ /tmp/fakebin/rm
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
The flag is still there! I might as well give it to you!
pwn.college{QVwZ8MVoJFS6TSv533bXZ5sxgRQ.QX2cDM1wSNxIzNzEzW}
'''

> Way:
a) First i understood what PATH was by the sheet given to us and a bit research i had done
b) After knowning what PATH was I still couldn't understand what to do in the chalenge
c) I tried to do what the example in the challenge discription was but it didn't work
d) Then i tried a bit what's there in the next challenges which worked a bit
e) Then as in chaining commands module i tried to write a python code in a command which worked
f) Then it became easy and I easily exported PATH and easily got answer
g) I found this challenge a bit difficult as I had to remember previous modules and had to try much stuff which took time 





###Challanges
This is for 3 challanges i found difficult to solve


---

## 1) Reading Shell Scripts (Chaining Commands)

**Code:**
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
hacker@chaining~reading-shell-scripts:~$ grep -oP '"[^"]{6,200}"' /challenge/run | sed 's/^"//; s/"$//' | head -n 10
$GUESS
hack the PLANET
CORRECT! Your flag:
Read the /challenge/run file to figure out the correct password!
hacker@chaining~reading-shell-scripts:~$ printf 'hack the PLANET\n' | /challenge/run || printf 'hack the planet\n' | /challenge/run
CORRECT! Your flag:
pwn.college{w0tXUXc6AIworZQR6SIuJv2hGuk.0lMwgDOxwSNxIzNzEzW}
'''

Way:
a) I wasn't able to understand what the challenge required
b) I tried using some stuff used in the previous challenges in this module
c) But that wasn't enough and wasn't giving answers
d) Then i tried a python program of simple if else statement 
e) But that also wasn't enough 
f) Then i asked chatgpt to help me understand what actually is required 
g) Then i tried using echo with other commands
h) Then i understood what to use in echo and types the commands
i) And then it become simple and i just had to run /challenge/run
j) Then i got my answer
k) It took me 2 days to finish it 
l) I had taken help from my friends who had done it but that help wasn't good enough as they had just helped me understanding the challenge just like what i asked chatgpt
m) After getting answer it became easier to continue the rest of the challenges
n) The thing which made this challenge difficult for me was mixing python statements and getting confused in echo statements together



