# Comprehending Commands — Formatted Solutions

Clean, consistent formatting for the **Comprehending Commands** module. Each challenge contains: **Goal**, **Flag**, **Terminal session** (in a `bash` code block), **What I learned**, and **References**.

---

## Cat: not the pet, but the command

**Goal:** Read the flag file in your home directory using `cat`.

**Flag**

```
pwn.college{ACSdtdXKZxeC9-PM7fPaDqgpkBm.QXxcTN0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{ACSdtdXKZxeC9-PM7fPaDqgpkBm.QXxcTN0wSN0EzNzEzW}
```

**What I learned**

* `cat` prints file contents. Check file existence & permissions first.

**References**

* `man cat`, pwn.college

---

## Catting Absolute Paths

**Goal:** Read the flag at `/flag`.

**Flag**

```
pwn.college{Q_FoO4OIrYf7FziX7-Ek2eTbc-G.QX5ETO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{Q_FoO4OIrYf7FziX7-Ek2eTbc-G.QX5ETO0wSN0EzNzEzW}
```

**What I learned**

* Absolute paths access files regardless of current directory (permissions permitting).

**References**

* pwn.college

---

## More Catting Practice

**Goal:** Read `/lib/maxima-sage/flag` without changing directories.

**Flag**

```
pwn.college{cmIOmgjNjUeV9VJvwUsR9OFb_Xb.QXwITO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~more-catting-practice:~$ cat /lib/maxima-sage/flag
pwn.college{cmIOmgjNjUeV9VJvwUsR9OFb_Xb.QXwITO0wSN0EzNzEzW}
```

**What I learned**

* Use full paths to access files when `cd` is not allowed or practical.

**References**

* `man cat`, pwn.college

---

## Grepping For A Needle In A Haystack

**Goal:** Find the flag inside a large text file using `grep`.

**Flag**

```
pwn.college{w-hKSEba41q8WKlw9prFqvJHMUq.QX3EDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{w-hKSEba41q8WKlw9prFqvJHMUq.QX3EDO0wSN0EzNzEzW}
```

**What I learned**

* `grep` quickly locates matching lines; narrow searches with unique prefixes.

**References**

* pwn.college

---

## Comparing Files

**Goal:** Use `diff` to spot added lines that contain the flag.

**Flag**

```
pwn.college{0qJAH5CYiaFSvIqF01Ws8p7d_2O.01MwMDOxwSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
47a48
> pwn.college{0qJAH5CYiaFSvIqF01Ws8p7d_2O.01MwMDOxwSN0EzNzEzW}
```

**What I learned**

* `diff` shows line-level differences; added lines appear with `a` and `>` markers.

**References**

* pwn.college

---

## Listing Files: /challenge

**Goal:** List `/challenge`, discover the renamed binary, and execute it.

**Flag**

```
pwn.college{ohEgkX_IKDOBUPECpvNyproB1VO.QX4IDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~listing-files:/challenge$ ls
26762-renamed-run-31782  DESCRIPTION.md

hacker@commands~listing-files:/challenge$ /challenge/26762-renamed-run-31782
Yahaha, you found me! Here is your flag:
pwn.college{ohEgkX_IKDOBUPECpvNyproB1VO.QX4IDO0wSN0EzNzEzW}
```

**What I learned**

* `ls` reveals directory contents; execute discovered binaries by path to avoid PATH issues.

**References**

* pwn.college

---

## Touching Files: /tmp

**Goal:** Create files `pwn` and `college` in `/tmp` and run the checker.

**Flag**

```
pwn.college{EPls2GuUj6FzumQ4k6QUHgJ2KQn.QXwMDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{EPls2GuUj6FzumQ4k6QUHgJ2KQn.QXwMDO0wSN0EzNzEzW}
```

**What I learned**

* `touch` creates empty files; use `ls` to verify before running checkers.

**References**

* pwn.college

---

## Linking Files

**Goal:** Create a symlink so a fixed-path script reads the real flag.

**Flag**

```
pwn.college{YswdYPV9bvcq3lJ5MD88gNyH5mY.QX5ETN1wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{YswdYPV9bvcq3lJ5MD88gNyH5mY.QX5ETN1wSN0EzNzEzW}
```

**What I learned**

* `ln -s` makes symbolic links to satisfy programs that read fixed paths.

**References**

* pwn.college

---

## Removing Files

**Goal:** Delete `delete_me` and run the checker.

**Flag**

```
pwn.college{49Ve3S4H-QkQk8Sh5qShUYIhTmu.QX2kDM1wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{49Ve3S4H-QkQk8Sh5qShUYIhTmu.QX2kDM1wSN0EzNzEzW}
```

**What I learned**

* `rm` removes files permanently; double-check filenames before running.

**References**

* pwn.college

---

## Moving Files

**Goal:** Move `/flag` to `/tmp/hack-the-planet` and run the checker.

**Flag**

```
pwn.college{8VvccP50i5QvxEjuQHdV2GxM4BS.0VOxEzNxwSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{8VvccP50i5QvxEjuQHdV2GxM4BS.0VOxEzNxwSN0EzNzEzW}
```

**What I learned**

* `mv` moves or renames files; create destinations with `mkdir -p` when needed.

**References**

* `man mv`, pwn.college

---

## Hidden Files

**Goal:** Find dot-prefixed hidden files under `/` and read the flagged hidden file.

**Flag**

```
pwn.college{Y0jqHNbpcP7S8ATFRyck5nSPN9-.QXwUDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:~/$ ls -a
.   ..  .flag-78701969019620  ...

hacker@commands~hidden-files:~/$ cat /.flag-78701969019620
pwn.college{Y0jqHNbpcP7S8ATFRyck5nSPN9-.QXwUDO0wSN0EzNzEzW}
```

**What I learned**

* Hidden files start with `.` and are visible with `ls -a`.

**References**

* pwn.college

---

## An Epic Filesystem Quest

**Goal:** Follow a long chain of clues across many directories to the final flag.

**Flag**

```
pwn.college{UCH835FGbmepkr-SLzHHI4VvOwD.QX5IDO0wSN0EzNzEzW}
```

**Terminal (abridged)**

```bash
# start at /
cat INFO       # points to /usr/share/.../Symbols/.CUE
cat .CUE       # points to /usr/lib/tc/INSIGHT
cat INSIGHT    # points to /opt/.../qcom/TEASER
cat TEASER     # points to /usr/share/icons/.../GIST-TRAPPED
cat GIST-TRAPPED
# ...follow a trail of clues until:
cat /usr/share/emacs/26.3/etc/e/NUGGET-TRAPPED
# final output:
pwn.college{UCH835FGbmepkr-SLzHHI4VvOwD.QX5IDO0wSN0EzNzEzW}
```

**What I learned**

* Combining `ls`, `ls -a`, `cd`, and `cat` is powerful for filesystem forensics. Read clues carefully.

**References**

* pwn.college

---

## Making Directories (/tmp/pwn)

**Goal:** Create `/tmp/pwn`, add `college`, then run the checker.

**Flag**

```
pwn.college{4GKbJs93O5755UBKTE1J76U1jkj.QXxMDO0wSN0EzNzEzW}
```

**Terminal**

```bash
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{4GKbJs93O5755UBKTE1J76U1jkj.QXxMDO0wSN0EzNzEzW}
```

**What I learned**

* `mkdir` plus `touch` creates the directory and files required by checkers.

**References**

* pwn.college

---

## Finding Files (find)

**Goal:** Search the filesystem for files named `flag` and inspect them.

**Flag**

```
pwn.college{k6SE6N6wjxu8ECKHFRP-kXNMSdS.QXyMDO0wSN0EzNzEzW}
```

**Terminal (abridged)**

```bash
find / -name flag 2>/dev/null
cat /nix/store/.../pwnlib/flag
pwn.college{k6SE6N6wjxu8ECKHFRP-kXNMSdS.QXyMDO0wSN0EzNzEzW}
```

**What I learned**

* `find` searches recursively; ignore permission-denied noise and focus on accessible results.

**References**

* pwn.college

---

*Want this exported as a PDF or merged into your master study guide?*
