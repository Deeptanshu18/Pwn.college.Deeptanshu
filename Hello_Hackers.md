# Hello Hackers
This module has threee challenges which are Intro to Commands, Intro to Arguments and Command History.

#Intro to Commands
This challenge asks to invoke the 'hello' command to get the flag.
As the Linux commands are case sensitive, we should be carefull and run exactly the same way in the shell to get the flag.
After getting the flag we need submit it in the flag section, after which the challenge is completed.

## My solution
**Flag**
'pwn.college{omcFfiMWKQqz64gW2BhqCxGKbMG.QX3YjM1wSNxIzNzEzW}'

1. I click on the challenge and click on start and choose ssh near flag input area
2. I connected the dojo host using SSH command.
   '''bash
   deepu18@Jarvis:~$ ssh -i ./key
   hacker@dojo.pwn.college
   Connected!
3. Now the shell is connected to dojo. On typing 'hello' and pressing Enter, the flag is produced on pwn.college(https://pwn.college/linux-luminarium/hello/), which i can submit to complete the challenge
   '''bash
   hacker@hello-intro-to-commands:~$ hello
   Success! Here is your flag:
   pwn.college{omcFfiMWKQqz64gW2BhqCxGKbMG.QX3YjM1wSNxIzNzEzW}

## What i learned
1. Basic structure of linux commands.
   a. Every command in shell follows a structure
   b. WE can run the coomands with Enter or return key depending on the users device.
   c. When the command is entered, the shell invokes it, proccesses it and prints the output.
   d. After getting the output the shell prompt reappears for next command.

2. Commands are case sensitive


## References
1. pwn.college
2. youtube video available in the command line above the challenges(https://youtu.be/g_85EVO3IC0?si=3cVEwx8DqQN3KXSG)

#Intro to Arguments
this challenges asks us to run a command 'hello' like last challenge but this time to add and argument 'hackers' into it, without using echo.
Therefore, the asked output is command+argument 'hello hackers'.
Then the flag is printed and submitted, which completes the challenge.

#My solution
flag: pwn.college{cCb00PSBOyrit0tfuXT3MKFwXYW.QX4YjM1wSNxIzNzEzW}

1. I connected the dojonhost using ssh command
   '''bash
   deepu18@Jarvis:~/pwn.college.Deeptanshu
   deepu18@Jarvis:~$ ssh -i ./key hacker@dojo.pwn.college
   Connected!

3. Now the shell is connected to the dojo.
4. Now i need to type the command 'hello hackers'
   '''bash
   hacker@hello~intro-to-arguments:~$ hello hackers
   Success! Here is your flag:
   pwn.college{cCb00PSBOyrit0tfuXT3MKFwXYW.Qx4YjM1wSNxIzNzEzW}
5. now the flag has been printed, which i can copy and submit to pwn.college to complete the challenge.

## References
1. pwn.college



# Command History
1. In this challenge the flag is already injected int o command history.
2. We have to open terminal, start the challenge and press the up arrow key to get our flag that was hidden in the command history.
3. After getting our flag we need to submit it, hence, completing the challenge.

#My solution
flag: pwn.college{UhKf_685tPHwTuZfsCSV207adsj.0lNzEzNxwSNxIzEzW}
1. Just like the previous challenges i had connected the dojo host using ssh command.
   '''bash
   deepu18@Jarvis:~$ ssh -i ./key
   hacker@dojo.pwn.college
   connected!
2.Now the shell is connected to dojo.
3.Now i need to press the up arrow key, so that the shell displayed the previous saved command that contained the flag
   '''bash
   hacker@hello~command-history:~& the flag is pwn.college{UhKf_685tPHwTuZfsCSV207adsj.01NzEzNxwSNxIzEzW}
4. This given flag I had copied and submitted on pwn.college to complete the challenge.

 ## What have i Learned
 1. The shell keeps a record of the commands.
 2. History can be navigated
 3. Time can be saved by avoiding repetitive typing

##References
1. pwn.college
2. read about the history command through chatgpt
