###Terminal Multiplexing
This module teaches us how to open many terminals without using many windows


##Launching Screen
This teach teaches us how to use the program screen which creates terminals inside a terminal

#My Solve
Flag: ''' pwn.college{YFNhpyJ956jToEsxz1_J0Jn2ikX.0VN4IDOxwSNxIzNzEzW} '''

Code: 
''' 
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{YFNhpyJ956jToEsxz1_J0Jn2ikX.0VN4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~launching-screen:~$
'''

#What I Learned
I learned how to use screen program and open a terminal in current terminal and retrieve my flag.

#Note: We need to type exit or press control-D to leave the opened terminal.

#Reference
pwn.college

##Detaching and Attaching
This challenge teaches us to how to switch between terminals and reattach them.

#My Solve
flag: ''' pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW} '''

Code: 
'''
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
Yes! Flag is: pwn.college{UFIzLS5hx88gfN4Wq1wLISdgEGu.0lN4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching:~$
'''

#What I Learned
How to open a terminal, press cntrl-A then d to exit it and reattach it with "screen -r" and retrieve the flag.

#Refernce
pwn.college

##Finding Sessions
This challenge teaches us how to find available screens and which one are running

#My Solve
flag: ''' pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW} '''

Code: 
'''
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
pwn.college{Yg7kEyhRBMNn8Mc1SPVIReuhH-o.01N4IDOxwSNxIzNzEzW}
'''

#What I Learned
How to detach not available and attach available screens and retrieve the flag in them

#Reference
pwn.college

##Switching Windows
This challenge teaches us how to use multiple windows as program screen is terminal-with-a-terminal

#My Solve
flag: ''' pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW} '''

Code: 
'''
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{o30Mn4E9VFolWjAV3qkHCljJRzx.0FO4IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~switching-windows:~$ 1
'''

#What I Learned
How to use multiple windows by using different functions of cntrl-A like,
Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows
and to attach everything

#Refernce
pwn.college

##Detaching and Attaching(tmux)
This challenge teaches us how to use tmux( terminal multiplexer ) insteaed of screen and cntrl-B instead of cntrl-A

#My Solve
flag: ''' pwn.college{IFcvGggGFYigujtY4OPzACDcf_p.0VO4IDOxwSNxIzNzEzW} '''

Code: 
'''
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
'''

#What I Learned
How to use tmux, list sessions ( tmux ls ), attaching ( tmux a )

#Reference
pwn.college

##Switching Windows( tmux )
Teaches us how to switch windows using tmux 

#My Solve
flag: ''' pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW} '''

Code: 
'''
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{sbI1iGtkwdcBlKr6ACJ6TvzgYvQ.0FM5IDOxwSNxIzNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$
'''

#What I Learned
How to swtich windows using tmux program and cntrl-B and its different functions
Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker
I also learned that tmux shows our windows at the bottom in a status bar like,
[0] 0:bash* 1:bash
"*" shows us our current window

#Reference
pwn.college
chatgpt( to understand how to switch windows )
