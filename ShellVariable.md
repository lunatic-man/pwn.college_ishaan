# Shell Variables 

## Challenge 1: Printing Variables 
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we are introduced to the concept of the Shell Variables and taught how to print them 

## My solve 

**Flag:** `pwn.college{4CpHcKTv1lGACJM3HHYG9ybhgJh.QX3UTN0wSO3gjNzEzW}` 

To solve the above challenge, I followed the steps listed below: 
- I first read the challenge, then simply ran the `echo $FLAG` command to get the flag. 

```bash
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{4CpHcKTv1lGACJM3HHYG9ybhgJh.QX3UTN0wSO3gjNzEzW}
hacker@variables~printing-variables:~$

```

## What I learned 
From this challenge, I learned that the Shell also has a programming language and basically we are writing programs only in the shell. I also learned about the existence of the shell variables and how we tell the shell what variable we want to access. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Setting Variables 
In this challenge of the *Linux Luminarium Dojo, Shell variables module,* we are taught how to store a particular value in the shell variable. 

## My solve 

**Flag:** `pwn.college{E7BLvVzWoHfoAmxKwZoQ67BzUAL.QX5UTN0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I simply ran the `PWN=COLLEGE` command to get the flag, as mentioned in the question. 

```bash 
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{E7BLvVzWoHfoAmxKwZoQ67BzUAL.QX5UTN0wSO3gjNzEzW}
hacker@variables~setting-variables:~$
```

## What I learned
In this challenge, I learned how to create a variable and assign a value to it. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Multi-word Variables
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we are taught how to assign multiple words to a single variable. 

## My solve 

**Flag:** `pwn.college{sz3OQFmrWlQumXF31ZvqQEnQKKi.QXwYTN0wSO3gjNzEzW}` 

To solve the challenge, I ran the commands as listed below: 
- I ran the `PWN="COLLEGE YEAH"` command as mentioned in the question to get the flag. 

```bash
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sz3OQFmrWlQumXF31ZvqQEnQKKi.QXwYTN0wSO3gjNzEzW}
hacker@variables~multi-word-variables:~$

```

## What I learned 
From this challenge, I learned how to assign multiple words as a value to a single variable. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Exporting variables 
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we need to export one particular variable to the child shell and then run the `/challenge/run` program to get the flag. 

## My Solve 

**Flag:** `pwn.college{gIkrjvLaQdIQXnTR_PgPV82mqb-.QXyYTN0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first created the `PWN` and `COLLEGE` variables with the necessary arguments (`COLLEGE` and `PWN` respectively). 
- After that I exported the `PWN` variable and then opened a child shell. 
- In this child shell, I ran the `/challenge/run` program to get the flag. 

```bash 
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh 
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{gIkrjvLaQdIQXnTR_PgPV82mqb-.QXyYTN0wSO3gjNzEzW}
sh-5.2$ exit
exit
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$
```

## What I learned 
I learned about the utilization of the `export` command to export variables to the child shell. Along with that, I learned about the existence of child shells and how we can run programs which exist in the original shell in them. 


## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Printing exported variables 
In this challenge of the *Linux Luminarium Dojo, Shell variables module,* we need to find the exported flag in our shell using the `env` command. 

## My solve 

**Flag:** `pwn.college{I0bNy8GZWUP3iBXXYNrt7ZTWjW7.QX4UTN0wSO3gjNzEzW}` 

To solve the above challenge, I followed the steps as listed below: 
- I simply ran the `env` command to get all the exported variables printed out, in which I found the flag. 

```bash
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=70c0faee8cebde3d732ef0b14db5a2172628aba7e2543dd8400401e7541a3d15
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{I0bNy8GZWUP3iBXXYNrt7ZTWjW7.QX4UTN0wSO3gjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env
hacker@variables~printing-exported-variables:~$

```

## What I learned 
From this challenge, I learned about the usage of the `env` command to print out all the exported variables in a shell. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Storing command output 
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we need to first store the output of a program in a variable and then print that variable to get the flag. 

## My Solve 

**Flag:** `pwn.college{A2LbnD6mFC1Ma3nN5be5nD-Kuku.QX1cDN1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `PWN=$(/challenge/run)` to store the output of the program in the required variable. 
- Then I simply ran the `echo $PWN` command to get the flag on the terminal.

```bash 
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{A2LbnD6mFC1Ma3nN5be5nD-Kuku.QX1cDN1wSO3gjNzEzW}
hacker@variables~storing-command-output:~$

```

## What I learned 
In this challenge, I learned about how we can fool the system by giving the output of a program as the value of a variable that we want to set. 

## What I learned 
From this challenge, I learned about the usage of the `env` command to print out all the exported variables in a shell. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Reading input 
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we need to take the input from the shell to set a value of a variable and get the flag. 


## My solve 

**Flag:** `pwn.college{QiPKE9E8NJmLIDXbrM5rWrvRkRf.QX4cTN0wSO3gjNzEzW}`

To solve this challenge, I ran the steps as listed below: 
- I first ran the `read` command with the needed argument to get the shell to take an input from me. 
- I then typed in the input as `COLLEGE`  to get the flag. 

```bash 
hacker@variables~reading-input:~$ read PWN 
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{QiPKE9E8NJmLIDXbrM5rWrvRkRf.QX4cTN0wSO3gjNzEzW}
hacker@variables~reading-input:~$
```

## What I learned 
I learned about the usage of the `read` command to take the input in the shell and store it in a variable. 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Reading files
In this challenge of the *Linux Luminarium Dojo, Shell Variables module,* we need to write a file into the `PWN` variable to get the flag. 

## My solve 

**Flag:** `pwn.college{oxccYzIngEn9GE0un02AmjFy5n-.QXwIDO0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I simply ran the `read PWN < /challenge/read_me` command to get the flag. 

```bash 
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{oxccYzIngEn9GE0un02AmjFy5n-.QXwIDO0wSO3gjNzEzW}
hacker@variables~reading-files:~$

```

## What I learned 
I learned from this challenge that I can simply use the input redirection method to directly send a file as value to the variable 

## References 
- https://pwn.college/linux-luminarium/variables/
- https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html
----------------------------------------------------------------------------------------------------------------------------------
