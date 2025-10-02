# Pondering Path 
## Challenge 1: The PATH Variable 
In this challenge of the *Linux Luminarium Dojo, Pondering Path module,* we need to remove the `rm` command from the PATH variable so that the `/challenge/run` program cannot find it. 

## My solve 

**Flag:** `pwn.college{cwih09NF_nncZwC38OYfB4af_u9.QX2cDM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simple used the command `PATH=""` to set the path variable to empty. This removed all commands in the PATH variable. 
- I then invoked the `/challenge/run` program and got the flag. 

```bash 
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{cwih09NF_nncZwC38OYfB4af_u9.QX2cDM1wSO3gjNzEzW}
hacker@path~the-path-variable:~$

```

## Alternate Solve 

- On reading the Note in the challenge statement, I realized that by first setting the `PATH` variable to empty, I affected this entire shell. While this did give me the result, it also meant that I reduced my shell to nothing. 
- To do it as the hint mentioned, I went online and read up on how we can set a variable for one particular program. 
- After finding the results online, I then ran the `PATH="" /challenge/run` command to set the `PATH` variable to none and then run it. 

```bash 
hacker@path~the-path-variable:~$ PATH="" /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{cwih09NF_nncZwC38OYfB4af_u9.QX2cDM1wSO3gjNzEzW}
hacker@path~the-path-variable:~$ ls 
solve.sh
hacker@path~the-path-variable:~$ 


```
- I typed out `ls` command to see whether the parent shell was affected or not, or was it just for the program that the variables changed. 

## What I learned
From this challenge, I learned that all commands that we have been invoking till now have lived in the PATH variable of a shell and we can manipulate this variable to get the result we want. I also learned how we can set variable for each program to ensure that we do not render our machine redundant 

## References 
- https://pwn.college/linux-luminarium/path/
- https://unix.stackexchange.com/questions/56444/how-do-i-set-an-environment-variable-on-the-command-line-and-have-it-appear-in-c
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Setting PATH 
In this challenge of the *Linux Luminarium Dojo, Pondering PATH module,* we need to set the `PATH` variable to a directory which has the `win` command. 

## My Solve

**Flag:** `pwn.college{cMKQDrigvbBvAQc2QqINCa0ydYD.QX1cjM1wSO3gjNzEzW}` 


To solve this challenge, I followed the steps as listed below: 
- I first overwrote the `PATH` variable to set it as `/challenge/more_commands/win`. However when I invoked the `/challenge/run` command, I got an error in that. 
- On rereading the challenge statement, I realized that the `PATH` variable takes directory paths and stores them. Re-crafting my statement to solve the challenge, I set `PATH=/challenge/more_commands` and then invoked the `/challenge/run` program to get the flag. 

```bash 

hacker@path~setting-path:~$ PATH=/challenge/more_commands/win 
hacker@path~setting-path:~$ /challenge/run 
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cMKQDrigvbBvAQc2QqINCa0ydYD.QX1cjM1wSO3gjNzEzW}
hacker@path~setting-path:~$ 

```

## What I learned 
From this challenge, I learned that we can create scripts for the commands that we want and simply add the directory path to the `PATH` variable to directly invoke these commands. 

## References 
- https://pwn.college/linux-luminarium/path/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Finding Commands 
In this challenge of the *Linux Luminarium Dojo, Pondering PATH module,* we need to find the directory in which the command lives by using the `which` command and then `cat` the flag present in that directory. 

## My solve 

**Flag:** `pwn.college{EyC2BiO6Vl5Ng3QaMk14vWFNi5s.01NzEzNxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first used the `which` command with `win` as an argument to gain knowledge about which directory the flag lives in. 
- After that I used a command `cat $(find /challenge/paths/2790 -name flag)` to get the contents of the flag without having to change my directory. 

```bash 
hacker@path~finding-commands:~$ which win
/challenge/paths/2790/win
hacker@path~finding-commands:~$ cat  $(find /challenge/paths/2790 -name flag)
pwn.college{EyC2BiO6Vl5Ng3QaMk14vWFNi5s.01NzEzNxwSO3gjNzEzW}
hacker@path~finding-commands:~$

```

## What I learned 
From this challenge, I learned how we can search for commands using the `which` command, and the `which` command tells us in whihc directory the script lives. 

## References
- https://pwn.college/linux-luminarium/path/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Adding Commands
In this challenge of the *Linux Luminarium Dojo, Pondering PATH module,* we need to write a script, add its directory path to the `PATH` variable and then invoke the `/challenge/run` program to get the flag. 


## My solve 

**Flag:** `pwn.college{QJ0Zf02JKUb5DbbcQViTJrLAaER.QX2cjM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as below: 
- I first read the challenge statement, and from previous challenges, I knew that whenever we set the `PATH` variable we overwrite existing directories. To avoid that, I read online how to preserve the directories that already exist in the `PATH` variable. 
- After learning that, I used the `echo` command to get the name of all the directories I want to preserve. 
- Before changing the `PATH` variable, I created a `win` script as shown below: 

```bash 
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ touch win 
hacker@path~adding-commands:~$ nano win
  GNU nano 8.4                                                      win                                                                
#!/bin/bash


cat /flag










                                                           [ Read 4 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy
```

- After creating this script, I invoked the `/challenge/run` command, but it gave me permission denied error. 

```bash 
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: /home/hacker/win: Permission denied
It looks like that did not work... Did you set PATH correctly?
```

- Because it gave me a permission denied error, I then used the `chmod` command to set the permissions for this script to executable. 
- I then changed the `PATH` variable to include all the previous directories and add the `/home/hacker` directory as that is where my `win` script exists.

```bash 
hacker@path~adding-commands:~$ chmod a=rwx win
hacker@path~adding-commands:~$ PATH="/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker"
hacker@path~adding-commands:~$
```

- I then invoked the `/challenge/run` program and got the flag. 

```bash 
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{QJ0Zf02JKUb5DbbcQViTJrLAaER.QX2cjM1wSO3gjNzEzW}
hacker@path~adding-commands:~$

```

## What I learned
From this challenge, I learned about how we can create our own scripts and add them onto the `PATH` variable without having to remove the basic directories that already exist. 

## References 
- https://pwn.college/linux-luminarium/path/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Hijacking Commands
In this challenge of the *Linux Luminarium Dojo, Pondering PATH module,* we need to hijack the `rm` command and make it print out the flag for us. 


## My solve 

**Flag:** `pwn.college{Q8PgkP4mkPOdw_9BUom9vkJft06.QX3cjM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first used `nano /challenge/run` command to read the `/challenge/run` script to understand what it does. The script told me that it invoked the `rm` command to delete the flag. 
- After reading the script, I simply changed the `PATH` variable and added on the `/home/hacker` directory and then invoked the `/challenge/run` program. Here I forgot that we were invoking `rm` and not `win` so I ended up erasing the flag. 
```bash
hacker@path~hijacking-commands:~$ nano /challenge/run
hacker@path~hijacking-commands:~$ echo $PATH
/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ PATH="/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /run/dojo/bin/rm. Executing!
Uh oh, looks like I successfully removed the flag! That means you did not 
properly set PATH to keep me from finding 'rm'. Since the flag is gone, you 
will need to re-launch the challenge from the module page! Better luck next 
time.
hacker@path~hijacking-commands:~$ 
```
- I analyzed the stderr output and realized that I did not remove the `/run/dojo/bin` directory and hence that got invoked. 
- Restarting the challenge, I had a brainwave of **hijacking** the command(I would have had this brainwave earlier had I read the challenge name with some focus). 
- I realized that I can create a script with the name of `rm` in the `/home/hacker` directory and then change the `PATH` variable to have only the `/home/hacker` directory.
- Following this plan, I executed the commands as below: 
```bash 
hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ nano rm
  GNU nano 8.4                                                      rm                                                                 
#!/bin/bash

/run/dojo/bin/cat /flag





                                                           [ Read 3 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy
```
- In this above script, I called `cat` command using the absolute path as I was removing all other directories.

```bash 
hacker@path~hijacking-commands:~$ chmod a=rwx rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{Q8PgkP4mkPOdw_9BUom9vkJft06.QX3cjM1wSO3gjNzEzW}
hacker@path~hijacking-commands:~$ 

```


## What I learned 
From this challenge, I learned that we should not get hung up on the name of the command and instead look at every command as just a script, which we can either edit, or recreate from scratch to do what we want. 

## References 
- https://pwn.college/linux-luminarium/path/
----------------------------------------------------------------------------------------------------------------------------------
