# Pondering Paths
this module has nine challenges which are The Root, Program and Absolute Paths, Position thy Self, Position elsewhere, Position yet elsewhere, implicit relative paths, from/, explicit relative paths, from/, implicit relative path, home sweet hacker

#The Root
This challenge tells us to launch a terminal, invoke the pwn program using its absolute path to get the glag.
After getting the flag we need to submit it to finish the challenge.

##My Solution
flag: ''' pwn.college{0jUsizh9t8eV29Ko8Jva5FqYdG_.QX4cTO0wSNxIzNzEzW] '''
1. I click on the challenge and click on start and choose ssh near flag input area
2. I connected the dojo host using SSH command.
   '''bash
   deepu18@Jarvis:~$ ssh -i ./key
   hacker@dojo.pwn.college
   Connected!
3. Now the shell is connected to dojo.
4. On typing /pwn and pressing enter, the flag is produced on pwn.college, which i can submit to complete the challenge.
   '''bash
   hacker@paths~the-root:~$ /pwn
   BOOM!!!
   Here is your flag:
   pwn.college{0jUsizh9t8eV29Ko8Jva5FqYdG_.QX4cTO0wSNxIzNzEzW]

##What I Learned
1. The filesystem starts with /
2. Under / there are many directories, files, programs, flags, etc.

#References
1. pwn.college
2. Youtube video provided on the starting of the challenge


#Program and Absolute Paths
This challenge asks us to run '/challenge/run' to get the flag.

##My Solution
flag: ''' pwn.college{8Y30v7hyCEQuafbIkFvac9rVaF6.QX1QTN0wSNxIzNzEzW} '''
1. I click on the challenge and click on start and choose ssh near flag input area
2. I connected the dojo host using SSH command.
   '''bash
   deepu18@Jarvis:~$ ssh -i ./key
   hacker@dojo.pwn.college
   Connected!
3. Now the shell is connected to dojo.
4. On typing /challenge/run and pressing enter, the flag is produced on pwn.college, which i can submit to complete the challenge
   '''bash
   hacker@paths~program-and-absolute-paths:$ /challenge/run
   Correct!!!
   /challenge/run is an absolute path! Here is your flag:
   pwn.college{8Y30v7hyCEQuafbIkFvac9rVaF6.QX1QTN0wSNxIzNzEzW}

##What I learned
1. How does the Directory works
2. How to run a command in a directory.

#References
1. pwn.college
2. Chatgpt to understand what a directory is and its functions.

#Position thy Self
