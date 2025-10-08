Perceiving Permissions



hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -1 /flag
/flag
hacker@permissions~changing-file-ownership:~$ ls -l /flag
-r-------- 1 hacker root 60 Oct  6 14:57 /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{8KmyDVKL6wvkRFref41CkCMzPgW.QXxEjN0wSNxIzNzEzW}




hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root hacker 60 Oct  6 14:59 /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{k1P5gvL2LvL01WnVX8tT9JiU0tp.QXxcjM1wSNxIzNzEzW}






hacker@permissions~fun-with-groups-names:~$ id -gn
grp8490
hacker@permissions~fun-with-groups-names:~$ chgrp "$(grp8498)" /flag
bash: grp8498: command not found
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /glag
chgrp: cannot access '/glag': No such file or directory
hacker@permissions~fun-with-groups-names:~$ chgrp "$(id -gn)" /flag
hacker@permissions~fun-with-groups-names:~$ la -l /flag
bash: la: command not found
hacker@permissions~fun-with-groups-names:~$ ls -l /flag
-r--r----- 1 root grp8490 60 Oct  6 15:00 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{A9sdFn80EqsIBtcQNfxsB1j66fa.QXycjM1wSNxIzNzEzW}




hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-----r-- 1 root root 60 Oct  6 15:03 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{wISQaSuOyZ7eibaf2UYt3IEJ2DZ.QXzcjM1wSNxIzNzEzW}





hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr-xr-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{ghA3tfgffp8XyQPTMIduJbs6YAU.QXyEjN0wSNxIzNzEzW}






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












hacker@permissions~permissions-setting-practice:~$ chmod u=rw, g=r, o=r /challenge/pwn
/usr/bin/chmod: invalid mode: ‘u=rw,’
Try '/usr/bin/chmod --help' for more information.
NEEDED, BUT UNMET permissions of "/challenge/pwn": rwx-----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

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
hacker@permissions~permissions-setting-practice:~$ chmod 644 /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": rwx-----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

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
hacker@permissions~permissions-setting-practice:~$ chmod 701 /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": rwx-----x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ---rwx-w-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
-rwx-----x 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 072 /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": ---rwx-w-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r----x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
----rwx-w- 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 241 /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": -w-r----x
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ------r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
--w-r----x 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 005 /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": ------r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x---rw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
-------r-x 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 506 /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r-x---rw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr-xr--
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
-r-x---rw- 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 354 /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": -wxr-xr--
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
--wxr-xr-- 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 006 /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": ------rw-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x---r--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
-------rw- 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod 504 /challenge/pwn
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
hacker@permissions~permissions-setting-practice:~$ ls -l /challenge/pwn
-r-x---r-- 1 hacker hacker 0 Oct  7 08:00 /challenge/pwn
hacker@permissions~permissions-setting-practice:~$ chmod u+r /flag
hacker@permissions~permissions-setting-practice:~$ ls -l /flag
-r-------- 1 hacker hacker 60 Oct  7 08:00 /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{QgYu1i3-NvPUBT_RBKdoTqG9ke9.QXzETO0wSNxIzNzEzW}




hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwsr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# id
uid=0(root) gid=1000(hacker) groups=1000(hacker)
root@permissions~the-suid-bit:~# whoami
root
root@permissions~the-suid-bit:~# cat /root/flag 2>/dev/null || cat /flag 2>/dev/null
pwn.college{8fl6Qv9Thp-VzSt0EVHUzgWrTFT.QXzEjN0wSNxIzNzEzW}


















