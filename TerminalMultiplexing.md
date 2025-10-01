# Terminal Multiplexing 
## Challenge 1: Launching Screen 
In this challenge of the *Linux Luminarium Dojo, Terminal Multiplexing module,* we are introduced to the concept of `screen` program. 

## My solve 

**Flag:** `pwn.college{AvfS8TjaJUcVbwFqvlK0WdO24MU.0VN4IDOxwSO3gjNzEzW}` 


To solve the challenge, I followed the steps as listed below: 
- I first read through the challenge statement to understand what exactly was asked of us and what do you mean by `screen` program. 
- I then simply typed in the command `screen` and got the flag. 

```bash 
hacker@terminal-multiplexing~launching-screen:~$ screen

                                         Screen version 5.0.1 (build on 2025-05-15 15:05:07) 
Copyright (c) 2025 Alexander Naumov
Copyright (c) 2018-2024 Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2015-2017 Juergen Weigert, Alexander Naumov, Amadeusz Slawinski
Copyright (c) 2010-2014 Juergen Weigert, Sadrul Habib Chowdhury
Copyright (c) 2008-2009 Juergen Weigert, Michael Schroeder, Micah Cowan, Sadrul Habib Chowdhury
Copyright (c) 1993-2007 Juergen Weigert, Michael Schroeder
Copyright (c) 1987 Oliver Laumann

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published
by the Free Software Foundation; either version 3, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program (see the file COPYING); if not, see
https://www.gnu.org/licenses/, or contact Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02111-1301 
USA.

Send bugreports, fixes, enhancements, t-shirts, money, beer & pizza to screen-devel@gnu.org













                                            [Press Space for next page or Return to end.]


Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{AvfS8TjaJUcVbwFqvlK0WdO24MU.0VN4IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~launching-screen:~$

```
## What I learned 
From this challenge, I learned about the usage of the `screen` program to create multiple terminals in one terminal itself, sort of like creating multiple browsing tabs inside your web browser. 

## References
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Detaching and Attaching 
In this challenge of the *Linux Luminarium Dojo, Terminal Multiplexing module,* we need to first detach a screen, then invoke a program and finally attach the screen back to our terminal to get the flag. 

## My solve 

**Flag:** `pwn.college{8LK-oKZPtsUKFe4Z4XyfZN9Nbqu.0lN4IDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge to understand what you mean when you say detaching and attaching. On reading I understood that it was similar to backgrounding a process where the processes is hidden and still running, except this is for a terminal. 
- After reading this, I first opened a screen using the `screen` command. After doing that, I used the key combination(when in screen) of `ctrl-A` and then pressed `d` to detach the screen from the terminal. 
- Post this, I invoked the `/challenge/run` program and ran it to send the flag to the detached screen. 
- To reattach the screen, I used the `screen` command with `-r` as the argument to reattach the screen and get the flag. 

```bash

hacker@terminal-multiplexing~detaching-and-attaching:~$ screen 


hacker@terminal-multiplexing~detaching-and-attaching:~$

hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 162.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r

hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{8LK-oKZPtsUKFe4Z4XyfZN9Nbqu.0lN4IDOxwSO3gjNzEzW}Yes! Flag is: pwn.college{8LK-oKZPtsUKFe4Z4XyfZN9Nbqu.0lN4IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching:~$

```

## What I learned
From this challenge, I learned that we can detach a screen, which is equivalent to backgrounding a process except detaching backgrounds multiple process running in that screen, and how we can reattach that screen.

## References
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Finding Sessions 
In this challenge of *Linux Luminarium Dojo, Terminal Multiplexing module,* we need to first list out all possible screen sessions and then find the correct one to get the flag. 

## My solve 

**Flag:** `pwn.college{8bY6rtc9HHqolOmXGI06kmABgnl.01N4IDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `screen -ls` command to list out all the running screen sessions as per the instructions and hints given in the challenge statement. 
- I then tried out running each session one by one to get the correct session and ultimately the flag. 

```bash 
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
	144.session_a02b4eeb3057d7fc	(Detached)
	147.session_6d5029c2be766b9d	(Detached)
	150.session_c25c652f736ba1bd	(Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144
[detached from 144.session_a02b4eeb3057d7fc]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 147
[detached from 147.session_6d5029c2be766b9d]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 150


hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{8bY6rtc9HHqolOmXGI06kmABgnl.01N4IDOxwSO3gjNzEzW}
pwn.college{8bY6rtc9HHqolOmXGI06kmABgnl.01N4IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~finding-sessions:~$


```

## What I learned 
From this challenge, I learned how we can navigate the multiple screen sessions when they show up and we can choose what screen session we want reattached to our terminal. 

## References
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Switching Windows
In this challenge of the *Linux Luminarium Dojo, Terminal Multiplexing module,* we need to navigate to a specific window of the screen to get the flag. 


## My solve 

**Flag:** `pwn.college{YtYtM7v7gbaaDal9_tGFX6sez6p.0FO4IDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I read the challenge statement to understand what do you mean by a window and what is its utility. 
- After understanding this, I ran the command to first reattach the screen to our terminal, then I used the `ctrl-A` and then type `0` to get to the first window of the screen. That is where I found the flag. 

```bash 

hacker@terminal-multiplexing~switching-windows:~$ screen -r


 cat <<MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows:~$







hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{YtYtM7v7gbaaDal9_tGFX6sez6p.0FO4IDOxwSO3gjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{YtYtM7v7gbaaDal9_tGFX6sez6p.0FO4IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~switching-windows:~$

```

## What I learned 
From this challenge, I learned about the existence of windows in a screen and how we can utilize these windows for effective usage of screens. 

## References
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Attaching and Detaching (tmux) 
In this challenge of the *Linux Luminarium Dojo, terminal multiplexing module,* we are introduced to the younger cousin of `screen`, `tmux`. And we need to detach and attach `tmux`, with an invocation of a program in between, to get our flag.

## My solve

**Flag:** `pwn.college{0OppV0vfTON9lHdEfcLn3_FMXUg.0VO4IDOxwSO3gjNzEzW}` 


To solve this challenge, I followed the step as listed below: 
- I first used the `tmux` command to create a screen, then I detached it using the `ctrl-b` and then `d` button combo.
- After detaching the screen, I invoked the `/challenge/run` program. 
- On reattaching the screen back using `tmux a`, we got the flag. 

```bash 

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a


hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{0OppV0vfTON9lHdEfcLn3_FMXUg.0VO4IDOxwSO3gjNzEzW}
Congratulations, here is your flag: pwn.college{0OppV0vfTON9lHdEfcLn3_FMXUg.0VO4IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ 


```

## What I learned 
From this challenge, I learned that the only important difference between `tmux` and `screen` is the use of `ctrl-B` and `ctrl-A` respectively for functionality of each. 

## References 
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Switching Windows (tmux) 
In this challenge of the *Linux Luminarium Dojo, terminal Multiplexing module,* we need to find the flag hidden in a different window of the tmux session. 

## My solve

**Flag:** `pwn.college{kjvM7pfwPUdLYRFYl6721nCL8_7.0FM5IDOxwSO3gjNzEzW}` 


To solve the challenge, I followed the steps as listed below: 
- I simply reattached the tmux session with `tmux a` command first. 
- Then I used the `ctrl-B` and `0` button combo to get to the first window present in the tmux session.

```bash
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux a

 cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
hacker@terminal-multiplexing~switching-windows-tmux:~$ 



hacker@terminal-multiplexing~switching-windows-tmux:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{kjvM7pfwPUdLYRFYl6721nCL8_7.0FM5IDOxwSO3gjNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{kjvM7pfwPUdLYRFYl6721nCL8_7.0FM5IDOxwSO3gjNzEzW}
hacker@terminal-multiplexing~switching-windows-tmux:~$ 


```

## What I learned 
From this challenge, I learned that the windows in the tmux session work similar to the windows in screen. The only difference comes in the beginning of the button combo. 

## References 
- https://pwn.college/linux-luminarium/terminal-multiplexing/
----------------------------------------------------------------------------------------------------------------------------------
