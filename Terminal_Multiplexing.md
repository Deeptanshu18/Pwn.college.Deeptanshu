Terminal Multiplexing






Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{YFNhpyJ956jToEsxz1_J0Jn2ikX.0VN4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~launching-screen:~$






hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching:~$





hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}




hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux attach
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{IFcvGggGFYigujtY4OPzACDcf_p.0VO4IDOxwSNxIzNzEzW}
Congratulations, here is your flag: pwn.college{IFcvGggGFYigujtY4OPzACDcf_p.0VO4IDOxwSNxIzNzEzW}







hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$









