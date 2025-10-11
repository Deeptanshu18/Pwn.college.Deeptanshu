# Terminal Multiplexing — Formatted Solutions

This module demonstrates terminal multiplexers (`screen` and `tmux`). Each challenge below contains the **goal**, the **flag**, the **terminal session** (in a `bash` code block), a short **what I learned**, and **references**.

---

## Launching `screen`

**Goal:** Start a `screen` session and discover the flag shown inside it.

**Flag**

```
pwn.college{YFNhpyJ956jToEsxz1_J0Jn2ikX.0VN4IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{YFNhpyJ956jToEsxz1_J0Jn2ikX.0VN4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~launching-screen:~$
```

**What I learned**

* `screen` creates virtual terminals inside a single real terminal. Use `exit` or `Ctrl-D` to leave a screen window.

**References**

* pwn.college

---

## Detaching and Attaching (screen)

**Goal:** Detach a `screen` session and reattach to retrieve the flag.

**Flag**

```
pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
```

**What I learned**

* Detach with `Ctrl-A d` and reattach with `screen -r` to resume sessions.

**References**

* pwn.college

---

## Finding Sessions (screen)

**Goal:** Locate the correct `screen` session that contains the flag.

**Flag**

```
pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~finding-sessions:~$ echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$ echo pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
```

**What I learned**

* Use `screen -ls` to list sessions and `screen -r <pid|name>` to attach to the right one.

**References**

* pwn.college

---

## Switching Windows (screen)

**Goal:** Switch between windows inside `screen` and find the flag in a specific window.

**Flag**

```
pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~switching-windows:~$ cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW}
```

**What I learned**

* Useful `screen` shortcuts:

  * `Ctrl-A c` — create window
  * `Ctrl-A n` — next window
  * `Ctrl-A p` — previous window
  * `Ctrl-A 0..9` — jump to numbered windows
  * `Ctrl-A "` — window list

**References**

* pwn.college

---

## Detaching and Attaching (`tmux`)

**Goal:** Use `tmux` to create a session, let a program send a message to it, then reattach to see the flag.

**Flag**

```
pwn.college{IFcvGggGFYigujtY4OPzACDcf_p.0VO4IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach
Congratulations, here is your flag: pwn.college{IFcvGggGFYigujtY4OPzACDcf_p.0VO4IDOxwSNxIzNzEzW}
```

**What I learned**

* `tmux` is a modern terminal multiplexer. Create sessions with `tmux`, list with `tmux ls`, attach with `tmux attach` or `tmux a`.

**References**

* pwn.college

---

## Switching Windows (tmux)

**Goal:** Switch windows inside `tmux` to find the flag.

**Flag**

```
pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
```

**What I learned**

* Useful `tmux` shortcuts:

  * `Ctrl-B c` — create window
  * `Ctrl-B n` — next window
  * `Ctrl-B p` — previous window
  * `Ctrl-B 0..9` — jump to windows
  * `Ctrl-B w` — window picker
* `tmux` shows windows in a status bar and marks the active one with `*`.

**References**

* pwn.college
* ChatGPT (for clarifying `tmux` shortcuts)

---


