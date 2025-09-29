# Processes and jobs 
## Challenge 1: Listing Processes 
In this challenge of the *Linux Luminarium Dojo, Processes and Jobs Module,* we need to find out the true name of the `/challenge/run` program and then run it to get the flag. 

## My solve 

**Flag:** `pwn.college{kn8XhcqwO4NQLFgos0bKf0bj-YM.QX4MDO0wSO3gjNzEzW}` 

To solve this challenge, I followed steps as listed below: 
- I first ran the `ps -ef` command to get the result of all processes in full format mode. 
- After getting the output, I analyzed the result and concluded that `/challenge/11648-run-17669` is the renamed program. 
- I then invoked the program to get the flag. 

```bash 
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 17:15 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/b
root           7       1  0 17:15 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 17:15 ?        00:00:00 /challenge/11648-run-17669
root         135     132  0 17:15 ?        00:00:00 sleep 6h
hacker       137       0  0 17:17 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/d
hacker       143     137  0 17:17 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       152     143  0 17:17 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/11648-run017669
bash: /challenge/11648-run017669: No such file or directory
hacker@processes~listing-processes:~$ /challenge/11648-run-17669
Yahaha, you found me! Here is your flag:
pwn.college{kn8XhcqwO4NQLFgos0bKf0bj-YM.QX4MDO0wSO3gjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').

```

## What I learned 
From this challenge, I learned about the usage of the `ps` command along with its necessary arguments to get the information about all the running processes on the system 

## References 
- https://pwn.college/linux-luminarium/processes/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Killing Processes 
In this challenge of the *Linux Luminarium Dojo, Processes and Jobs module,* we need to kill a specific process before invoking `/challenge/run`. 

## My solve 

**Flag:** `pwn.college{4EfbbVnQQAAxofoOYLGpljs7mPY.QXyQDO0wSO3gjNzEzW}` 


To solve the above challenge, I followed the steps as listed below: 
- I first ran the `ps -e | grep /challenge/dont_run` command to find the process. However this return no result. Feeling a bit confused I ran the normal `ps -ef` command to get the processes. 
- Luckily in this case, the number of processes was small and I was able to find the `/challenge/dont_run` process and kill it. 
- After killing the intended process, I invoked the `/challenge/run` program to get the flag. 

```bash 

hacker@processes~killing-processes:~$ ps -e | grep /challenge/dont_run
hacker@processes~killing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
    135 ?        00:00:00 su
    136 ?        00:00:00 bash
    137 ?        00:00:00 sleep
    139 pts/0    00:00:00 ssh-entrypoint
    145 pts/0    00:00:00 bash
    158 pts/0    00:00:00 ps
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 17:23 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/b
root           7       1  0 17:23 ?        00:00:00 /run/dojo/bin/sleep 6h
root         135       1  0 17:23 ?        00:00:00 su -c /challenge/.launcher hacker
hacker       136     135  0 17:23 ?        00:00:00 /challenge/dont_run
hacker       137     136  0 17:23 ?        00:00:00 sleep 6h
hacker       139       0  0 17:23 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/d
hacker       145     139  0 17:23 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       159     145  0 17:24 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{4EfbbVnQQAAxofoOYLGpljs7mPY.QXyQDO0wSO3gjNzEzW}
hacker@processes~killing-processes:~$

```


## What I learned 
From this challenge, I learned that full names of the processes would not be show by default and we need to as the `ps` command to give us full names using the `-f` argument. 

## References 
- https://pwn.college/linux-luminarium/processes/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Interrupting processes 
In this challenge of the *Linux Luminarium dojo, Processes and Jobs Module,* we need to interrupt the running of the `/challenge/run` program to get the correct flag. 

## My solve 

**Flag:** `pwn.college{c89xv9YcSAqPiCAtJpwY4p-Xqdp.QXzQDO0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I simply followed the instruction given in the challenge statement, and I invoked the `/challenge/run` program and then interrupted it using the `Ctrl-c` control code.
- This gave me the flag as needed. 

```bash 
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{c89xv9YcSAqPiCAtJpwY4p-Xqdp.QXzQDO0wSO3gjNzEzW}
hacker@processes~interrupting-processes:~$

```

## What I learned 
From this challenge, I learned about how to interrupt a process that is running on the terminal and not allowing us to execute other commands. 

## References 
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Killing Misbehaving Processes 
In this challenge of the *Linux Luminarium dojo, Processes and Jobs module,* we need to kill a process which is sending garbage values to our fifo file and then invoke the `/challenge/run` program to send the correct flag to the fifo. 

## My solve 

**Flag:** `pwn.college{YC6QK4Iqb030N8uO9i3hKFErgoH.0FNzMDOxwSO3gjNzEzW}` 


To solve this challenge, I ran the steps as listed below: 
- Firstly, I ran the `ps` command with the required arguments to find out what is the PID of the `/challenge/decoy` program and kill it. I tried to kill a process which I thought was copying the decoys to the fifo, but it turned out that the process was running as a su and I could not kill it. 

```bash 
hacker@processes~killing-misbehaving-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 06:54 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/b
root           7       1  0 06:54 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 06:54 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 06:54 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 06:54 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     137  0 06:54 ?        00:00:00 sleep 6h
root         141     138  0 06:54 ?        00:00:00 sleep 6h
hacker       142     139  0 06:54 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       144       0  0 06:54 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/d
hacker       150     144  0 06:54 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       159     150  0 06:56 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$ kill 139
bash: kill: (139) - Operation not permitted
hacker@processes~killing-misbehaving-processes:~$

```

- I then re-analyzed the output of `ps` and found the correct PID as 142. So I ended up killing that process. 
- After killing that process, I first used the `cat` command to clear the buffer as per the questions instructions/note. 

```bash 
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{5XKHLU1lGbG98JLz3l72D-OMZvHe1J.kj9kREiQ.usrAet5}
pwn.college{gH8Q00Unne5j2otZFmdK-VF3Rc.Me-nCIZ2ccQbCHvU-48b}
pwn.college{mEzOT6OUeLsY62Caf-PGJtE2.h.G-6nijliNbT7Db7UVI1V}
pwn.college{imhh1fBmgT7a1viD6lJjcEXSzd0ly6FD0cciuAStYxYPkmv}
pwn.college{-mzMW9vJqE97HE1Cs7DMRRaqNHlAJpQ0PeL44h94XjWI7Vg}
.
.
.
pwn.college{WmRN1OpEhWl4HEcXQW2m0QqchFHODBFqS.2ILv1QqY3obK3}
pwn.college{WHFCk9tDqiO5r5iS9x088kHSuSxlh.EXJZk0hOaKvuHIGEO}

^C
hacker@processes~killing-misbehaving-processes:~$
```

- Because this process did not end on its own, I ended up interrupting the process. I did this because I had already stopped the decoy program from running, so I knew that fifo would not be taking any more inputs and hence it will stop at some point. 
- After doing that, I ended up running the `/challenge/run` program to send the flag to the needed fifo. 
- using the `cat` command on the fifo, I got a single flag value, which turned out to be the correct flag. 

```bash 
^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{YC6QK4Iqb030N8uO9i3hKFErgoH.0FNzMDOxwSO3gjNzEzW}

```

## What I learned 
From this challenge, I learned about how to kill a process which has gotten out of control. This can be very useful when we create programs that get out of our control and hence can cause damage. I also learned about the buffering of FIFO files and how we often need to clear the data already stored in them before we enter new data. 

## References 
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Suspending Processes 
In this challenge of the *Linux Luminarium dojo, Processes and Jobs Module,* we need to suspend a process instead of interrupting it and then launching another copy of it to get the flag. 

## My solve 

**Flag:** `pwn.college{Eyl4bUynEzOM4oUiqtdqMVH2z3R.QX1QDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first invoked the `/challenge/run` command to create the original process. 
- I then suspended it using the `Ctrl-z` control code. 
- Again, I ran the `/challenge/run` command to get the flag. 

```bash 
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         139     130  0 07:09 pts/0    00:00:00 bash /challenge/run
root         141     139  0 07:09 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         139     130  0 07:09 pts/0    00:00:00 bash /challenge/run
root         146     130  0 07:09 pts/0    00:00:00 bash /challenge/run
root         148     146  0 07:09 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Eyl4bUynEzOM4oUiqtdqMVH2z3R.QX1QDO0wSO3gjNzEzW}
hacker@processes~suspending-processes:~$
```

## What I learned 
From this challenge, I learned the difference between interrupting a process and suspending the process. This difference was not clearly explained in the challenge statements and hence I discussed this with ChatGPT bot, which explained that suspending a process makes it still stay alive in memory but frozen, while interrupting a process wipes it from the memory as well. 

## References 
- https://pwn.college/linux-luminarium/processes/
- https://chatgpt.com/c/68da3114-b1a0-8323-a675-ad37c58a476f
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Resuming Processes 
In this challenge of the *Linux Luminarium dojo, Processes and Jobs module,* we need to first invoke the `run` program, then suspend it, and then resume it again. 

## My solve 

**Flag:** `pwn.college{oCpeyB-JLclh_z3Cdtb1-aRggB-.QX2QDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- First, I invoked the `/challenge/run` program to get the program running. 
- I then suspended it using the `ctrl-z` code. 
- I then resumed it by typing the `fg` command to get the flag. 

```bash 
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{oCpeyB-JLclh_z3Cdtb1-aRggB-.QX2QDO0wSO3gjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
hacker@processes~resuming-processes:~$

```

## What I learned 
From this challenge, I learned about the usage of the `fg` command to bring the suspended processes to the foreground. 

## References 
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Backgrounding Processes 
In this challenge of the *Linux Luminarium Dojo, Processes and Jobs Module,* we need to make a process run in the background and then run another copy of it in the foreground to get the flag. 

## My solve 

**Flag:** `pwn.college{8P6lLWEctkX5Ign4ZJW3QY5dNT8.QX3QDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply invoked the `/challenge/run` program to get it to first run in the foreground. I then suspended it using `ctrl-z` code. 
- To resume the suspend process, I ran the `bg` command in the terminal to resume the suspended process *in the background*. This allowed me to have control over my shell and invoke the `/challenge/run` program again. 

```bash 
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S+   bash /challenge/run
root         140 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         138 S    bash /challenge/run
root         148 S    sleep 6h
root         149 S+   bash /challenge/run
root         151 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{8P6lLWEctkX5Ign4ZJW3QY5dNT8.QX3QDO0wSO3gjNzEzW}
hacker@processes~backgrounding-processes:~$

```

## What I learned 
From this challenge, I learned that backgrounding of a process can be done using the `bg` command. I also read up a bit online to understand the true difference between backgrounded process, suspended process and interrupted process. 

## References 
- https://pwn.college/linux-luminarium/processes/
- https://chatgpt.com/c/68da3114-b1a0-8323-a675-ad37c58a476f
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Foregrounding processes 
In this challenge of the *Linux Luminarium dojo, Processes and Jobs module,* we need to first invoke a program, then suspend it, then resume it in the background and finally bring it to the foreground to get the flag. 

## My solve 

**Flag:** `pwn.college{gy6VpjIBlFYISEKnU-MGXL5G8QQ.QX4QDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `fg` command assuming that some processes was already running in the shell. However, on getting no meaningful result back, I invoked the `/challenge/run` program. 
- This program told me that I needed to first suspend the program, resume it in the background and then finally bring it to the foreground to get the flag.
- Following this chain, I ran the commands as needed and got the flag. 

```bash
hacker@processes~foregrounding-processes:~$ fg
bash: fg: current: no such job
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{gy6VpjIBlFYISEKnU-MGXL5G8QQ.QX4QDO0wSO3gjNzEzW}
hacker@processes~foregrounding-processes:~$

```

## What I learned 
From this challenge, I learned about the foregrounding of a process which is running in the background using the `fg` command. 


## References 
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 9: Starting backgrounded Processes 
In this challenge of the *Linux Luminarium Dojo, Processes and Jobs module,* we need to invoke the `/challenge/run` program and run it backgrounded from the start itself to get the result. 

## My solve 

**Flag:** `pwn.college{4mlV4RYnKFBrxjhisOjfXEPDhw1.QX5QDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply ran the `/challenge/run &` command to get the flag as per the instructions given in the challenge statement. 

```bash 
hacker@processes~starting-backgrounded-processes:~$ /challenge/run & 
[1] 138
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{4mlV4RYnKFBrxjhisOjfXEPDhw1.QX5QDO0wSO3gjNzEzW}

[1]+  Done                    /challenge/run
hacker@processes~starting-backgrounded-processes:~$

```

## What I learned 
From this challenge, I learned that I can simply start processes backgrounded instead of having to first suspend and then having to resume them in the background. 

## References
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 10: Process Exit Codes
In this challenge of the *Linux Luminarium Dojo, Processes and Jobs module,* we need to find the correct exit code of a process and submit it as an argument to the new program to get the flag. 

## My solve 

**Flag:** `pwn.college{Mrbt_N1PCKPwvquGGKO7gpMseN1.QX5YDO1wSO3gjNzEzW}` 

To solve this challenge, I executed the steps as listed below: 
- I first invoked the `/challenge/get-code` program to get the exit code. I then ran the `echo $?` command to get the value of the variable outputted out to the shell.
- I then passed the value as an argument to `/challenge/submit-code` to get the correct flag. 

```bash 
hacker@processes~process-exit-codes:~$ /challenge/get-code 
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $? 
235
hacker@processes~process-exit-codes:~$ /challenge/submit-code 235
CORRECT! Here is your flag:
pwn.college{Mrbt_N1PCKPwvquGGKO7gpMseN1.QX5YDO1wSO3gjNzEzW}
hacker@processes~process-exit-codes:~$ 

```

## What I learned 
From this challenge, I learned about the existence of Process Exit Codes and how a successful process usually returns 0 to indicate successful completion of the process. 

## References 
- https://pwn.college/linux-luminarium/processes/
----------------------------------------------------------------------------------------------------------------------------------
