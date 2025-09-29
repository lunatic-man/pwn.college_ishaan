# Untangling Users 
## Challenge 1: Becoming root with su 
In this challenge of the *Linux Luminarium dojo, Untangling Users module,* we need to find the correct flag by becoming the root user using `su` command. 

## My solve 

**Flag:** `pwn.college{gOk0NG-Pozq4WE6sMmLi1AFfWsT.QX1UDN1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `su` command which then prompted me for a password. Entering the password, I because a root user. 
- I then listed out the contents of the `/home/hacker` directory. I saw a `the-flag` file and got its output using the `cat` command. 
- However, when I pasted the flag into the answer area, I got an incorrect alert. 
- On re-reading the challenge statement, I understood that I need to find the flag, so I switched to the root using `cd` to find the correct flag. 

```bash 
hacker@users~becoming-root-with-su:~$ su 
Password: 
root@users~becoming-root-with-su:/home/hacker# ls
COLLEGE  Desktop  PWN  error  instructions  myflag  not-the-flag  output  the-flag
root@users~becoming-root-with-su:/home/hacker# cat the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{EAnFYmORz0zkSJw3ubn1RMAnzKD.QX3ATO0wSO3gjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
root@users~becoming-root-with-su:/home/hacker# cd /
root@users~becoming-root-with-su:/# ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
root@users~becoming-root-with-su:/# cat flag
pwn.college{gOk0NG-Pozq4WE6sMmLi1AFfWsT.QX1UDN1wSO3gjNzEzW}
root@users~becoming-root-with-su:/#

```

## What I learned 
From this challenge, I learned about the existence of the root user and how we, as a hacker will try to elevate our access to that of a the root user/system administrator. I also learned that we  can do this by using the `su` command. 

## References
- https://pwn.college/linux-luminarium/users/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Other users using su 
In this challenge of the *Linux Luminarium Dojo, Untangling Users module,* we need to switch to a different user, and then invoke the `/challenge/run` program to get the flag. 

## My solve 

**Flag:** `pwn.college{g3ANoCu3v9hxs0qi9Gnb-1Z-POL.QX2UDN1wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first changed myself to zardus user by using the `su` command with `zardus` as an argument. 
- After becoming Zardus, we invoke the `/challenge/run` program to get the flag. 

```bash 
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{g3ANoCu3v9hxs0qi9Gnb-1Z-POL.QX2UDN1wSO3gjNzEzW}
zardus@users~other-users-with-su:/home/hacker$

```

## What I learned 
From this challenge, I learned that `su` command can take usernames as arguments and thus we can use it to switch to other user accounts as well. 

## References 
- https://pwn.college/linux-luminarium/users/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Cracking Passwords 
In this challenge of the *Linux Luminarium Dojo, Untangling users module,* we need to crack the hash of Zardus user to get his password and then use the `su` command to become him and invoke the needed program. 

## My solve

**Flag:** `pwn.college{kEhI44tJMlz_2QZYkLZZGRq_zM1.QX3UDN1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `john /challenge/shadow-leak` command to get the password of zardus. This gave me the password as `aardvark`.
- Then I used the `su` command along with the `zardus` argument, and when prompted for the password, entered `aardvark` as the password. This gave me access to zardus' account. 
- I then invoked the `/challenge/run` program to get the flag. 

```bash 
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak 
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04914g/s 286.1p/s 286.1c/s 286.1C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kEhI44tJMlz_2QZYkLZZGRq_zM1.QX3UDN1wSO3gjNzEzW}
zardus@users~cracking-passwords:/home/hacker$

```

## What I learned 
From this challenge, I learned about what files I need to access to get the hashes of the passwords along with the usage of *John the Ripper* tool to get the value of the hash. 

## References 
- https://pwn.college/linux-luminarium/users/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Using sudo 
In this challenge of the *Linux Luminarium Dojo, Untangling users module,* we need to find the flag by running the `cat` command as a root user using `sudo` command. 

## My solve 


**Flag:** `pwn.college{kdM6Ko9jGf3jS7YTMPa1dHmuYzv.QX4UDN1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first switched to root directory by using `cd /` command. 
- Once in root directory, I ran the `ls` command to find the name of the flag. 
- I then tried running it using the simple `cat` command but I got the error of permission denied. 
- I then ran the `cat` command with `sudo` to get the flag. 

```bash 
hacker@users~using-sudo:~$ cd /
hacker@users~using-sudo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@users~using-sudo:/$ cat flag
cat: flag: Permission denied
hacker@users~using-sudo:/$ sudo cat flag
pwn.college{kdM6Ko9jGf3jS7YTMPa1dHmuYzv.QX4UDN1wSO3gjNzEzW}
hacker@users~using-sudo:/$
```

## What I learned 
From this challenge, I learned about the existence of `sudo` command which stands for substitute user do, and how we can use this command to execute commands in the name of other users instead of having to switch to their account every time. 


## References 
- https://pwn.college/linux-luminarium/users/
----------------------------------------------------------------------------------------------------------------------------------
