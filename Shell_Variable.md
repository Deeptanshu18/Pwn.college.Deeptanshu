#Shell Variable
Helps us understand vairbales and printing different values of different variables

##Printing Variables
Teaches us how to print varibales

**Flag** pwn.college{kOK1xr4AcaGX7YcKrTrss-K5D6x.QX3UTN0wSNxIzNzEzW}

##My Solve
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{kOK1xr4AcaGX7YcKrTrss-K5D6x.QX3UTN0wSNxIzNzEzW}
hacker@variables~printing-variables:~$

##What I Learned
How echo works
Why $ is used

##References
pwn.college

##Setting Variables
Helps us to set a varibale and print it

**flag** pwn.college{AZyYs0tB39btGRH45KES1SafCgL.QX5UTN0wSNxIzNzEzW}

##My Solve
hacker@variables~setting-variables:~$ export PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{AZyYs0tB39btGRH45KES1SafCgL.QX5UTN0wSNxIzNzEzW}
hacker@variables~setting-variables:~$

##What I Learned
how to set a value for a variable

##References
pwn.college

##Multi Word Variables
Helps us to learn quoting

**flag** pwn.college{gwx8y_A6_dkQ-72AyQsqi3tqh3C.QXwYTN0wSNxIzNzEzW}

##My Solve
acker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gwx8y_A6_dkQ-72AyQsqi3tqh3C.QXwYTN0wSNxIzNzEzW}
hacker@variables~multi-word-variables:~$

##What I Learned
How to Quote a variable

##References
pwn.colege

#Exporting Variables
Teaches us how to export a value for a variable

**flag** pwn.college{8WO60TiTeRInL_t1eUnHXQJredL.QXyYTN0wSNxIzNzEzW}

#My Solve
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh -c 'echo "child sees: PWN=$PWN COLLEGE=$COLLEGE"'
child sees: PWN=COLLEGE COLLEGE=
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{8WO60TiTeRInL_t1eUnHXQJredL.QXyYTN0wSNxIzNzEzW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$

##What I Learnedd
how to export a variable
hwo to print is using sh

##References
pwn.college

##Printing Exporting Variables
Teavhes us to use env insttead of echo

**flag** pwn.college{UF-va328jDDhxEmv1XhgJFDc5sa.QX4UTN0wSNxIzNzEzW}

##My Solve
hacker@variables~printing-exported-variables:~$ export FLAG
hacker@variables~printing-exported-variables:~$ env | grep '^FLAG='
FLAG=pwn.college{UF-va328jDDhxEmv1XhgJFDc5sa.QX4UTN0wSNxIzNzEzW}
hacker@variables~printing-exported-variables:~$

##What I Learned
How to use env 

##References
pwn.college

##Storing Command Output
Teaches us about command substitution

**flag** pwn.college{EMAC2qVQZFFmIVRed0FB_ppML0j.QX1cDN1wSNxIzNzEzW}

##My Solve
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo PWN
PWN
hacker@variables~storing-command-output:~$ printenv PWN
pwn.college{EMAC2qVQZFFmIVRed0FB_ppML0j.QX1cDN1wSNxIzNzEzW}
hacker@variables~storing-command-output:~$

##What I Learned
how to print variables using command substitution

##References
pwn.college

##Reading Input
Teaches us to print the input given by the user into the variable 

**flag** pwn.college{cfgrFC0Lh63cbBHr0FvH9QfcGEm.QX4cTN0wSNxIzNzEzW}

##My Solve
hacker@variables~reading-input:~$ read -p "Enter value: " PWN
Enter value: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cfgrFC0Lh63cbBHr0FvH9QfcGEm.QX4cTN0wSNxIzNzEzW}
hacker@variables~reading-input:~$ 

##What I Learned
how to read an input

##References
pwn.college

##Reading Files
Teaches us to read files 

**flag** pwn.college{sjkTR7UwL5scNfxfB5_J_9uGSZR.QXwIDO0wSNxIzNzEzW}

##My Solve
hacker@variables~reading-files:~$ read -r PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sjkTR7UwL5scNfxfB5_J_9uGSZR.QXwIDO0wSNxIzNzEzW}
hacker@variables~reading-files:~$

##What I Learned
how to help the program to read the file

##References
pwn.college
