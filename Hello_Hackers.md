# Hello Hackers

This module has three challenges: **Intro to Commands**, **Intro to Arguments**, and **Command History**.

---

## Intro to Commands

This challenge asks you to invoke the `hello` command to get the flag. Commands are case-sensitive, so run it exactly as shown.

### My solution

**Flag**

```
pwn.college{omcFfiMWKQqz64gW2BhqCxGKbMG.QX3YjM1wSNxIzNzEzW}
```

**Steps**

1. Click the challenge, click **Start**, then choose **SSH** near the flag input area.
2. Connect to the dojo host using SSH:

```bash
ssh -i ./key hacker@dojo.pwn.college
# Output (example):
# Connected!
```

3. Once connected, run the command exactly as shown to print the flag:

```bash
hello
# Output (example):
# Success! Here is your flag:
# pwn.college{omcFfiMWKQqz64gW2BhqCxGKbMG.QX3YjM1wSNxIzNzEzW}
```

### What I learned

1. Basic structure of Linux commands:

   * Commands follow a simple structure: `command [options] [arguments]`.
   * Press **Enter** to run a command.
   * The shell executes the command and prints output, then returns to the prompt.
2. Commands are case-sensitive.

**References**

* pwn.college
* The video linked in the challenge (YouTube)

---

## Intro to Arguments

This challenge is like the previous one but requires passing an argument to `hello`. The desired output is `hello hackers` (without using `echo`). After printing that, the flag will appear.

### My solution

**Flag**

```
pwn.college{cCb00PSBOyrit0tfuXT3MKFwXYW.QX4YjM1wSNxIzNzEzW}
```

**Steps**

1. Connect to the dojo host via SSH:

```bash
ssh -i ./key hacker@dojo.pwn.college
# Output: Connected!
```

2. Run `hello` with the argument `hackers`:

```bash
hello hackers
# Output:
# Success! Here is your flag:
# pwn.college{cCb00PSBOyrit0tfuXT3MKFwXYW.QX4YjM1wSNxIzNzEzW}
```

**References**

* pwn.college

---

## Command History

In this challenge the flag is stored in the shell's command history. Press the **Up** arrow key to recall previous commands and reveal the hidden flag.

### My solution

**Flag**

```
pwn.college{UhKf_685tPHwTuZfsCSV207adsj.0lNzEzNxwSNxIzEzW}
```

**Steps**

1. Connect to the dojo host via SSH:

```bash
ssh -i ./key hacker@dojo.pwn.college
# Output: Connected!
```

2. Press the **Up** arrow key in the terminal to browse command history. The previous command containing the flag will appear. Example shown below (simulated):

```bash
# Press ↑ and the shell shows the previous command that contained the flag
# Example display (simulated):
# hacker@hello~command-history:~$ <previous-command-containing-flag>
# pwn.college{UhKf_685tPHwTuZfsCSV207adsj.0lNzEzNxwSNxIzEzW}
```

### What I learned

1. The shell keeps a record of commands (history).
2. You can navigate history using arrow keys to avoid retyping.

**References**

* pwn.college
* Documentation on the `history` command

---

*Notes:*

* All terminal commands and outputs have been placed in fenced code blocks (`bash`) for clarity.
* Replace `./key` and hostnames as appropriate for your environment.
