# Perceiving Permissions 
## Challenge 1: Changing File Ownership 
In this challenge of the *Linux Luminarium dojo, Perceiving Permissions Module,* we need to change the ownership of the file from root to hacker using the `chown` command. 

## My solve 

**Flag:** `pwn.college{Ec1bpvtjqQi26Dox64YAovWwqxP.QXxEjN0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first changed my cwd to the root directory, once in the root directory, I used `ls` command to find the owner of the file. 
- I then used the `chown` command to change the ownership of the file from root to hacker. 
- After this, I used the `cat` command to get the flag. 

```bash 
hacker@permissions~changing-file-ownership:~$ cd /
hacker@permissions~changing-file-ownership:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@permissions~changing-file-ownership:/$ ls -l flag
-r-------- 1 root root 60 Sep 29 12:14 flag
hacker@permissions~changing-file-ownership:/$ chown hacker flag
hacker@permissions~changing-file-ownership:/$ ls -l flag
-r-------- 1 hacker root 60 Sep 29 12:14 flag
hacker@permissions~changing-file-ownership:/$ cat flag
pwn.college{Ec1bpvtjqQi26Dox64YAovWwqxP.QXxEjN0wSO3gjNzEzW}
hacker@permissions~changing-file-ownership:/$

```

## What I learned 
From this challenge, I learned about how to change the ownership of a file and make it such that we can access that file without any issues at all. 

## References 
- https://pwn.college/linux-luminarium/permissions/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Groups and files 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to gain access to a file by using the `chgrp` command to change the group ownership of the file to a group where we have access. 

## My solve 

**Flag:** `pwn.college{UB22Q_OtHMO2OZkie-m1jdvrKpY.QXxcjM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `cd /` command to change my directory to root directory. 
- Then I ran the `ls -l flag` command to check the group ownership. Finding out it is with the root group, I changed it to hacker group using the `chgrp` command. 
- After this I ran the `cat flag` command to get the flag. 

```bash 
hacker@permissions~groups-and-files:~$ cd /
hacker@permissions~groups-and-files:/$ ls -l flag
-r--r----- 1 root root 60 Sep 29 12:27 flag
hacker@permissions~groups-and-files:/$ chgrp hacker flag
hacker@permissions~groups-and-files:/$ ls -l flag
-r--r----- 1 root hacker 60 Sep 29 12:27 flag
hacker@permissions~groups-and-files:/$ cat flag
pwn.college{UB22Q_OtHMO2OZkie-m1jdvrKpY.QXxcjM1wSO3gjNzEzW}
hacker@permissions~groups-and-files:/$ 
```

## What I learned 
From this challenge, I learned how to change the group ownership from one group to another and this allows us to gain access to a particular file, provided we are a part of the second group. 

## References 
- https://pwn.college/linux-luminarium/permissions/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Fun with Group Names 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to change the group ownership of a file to a random group name and then use the `cat` command to get the flag. 

**Flag:** `pwn.college{MLAIEtYMk26KNqQFMk_ODrNmoUB.QXycjM1wSO3gjNzEzW}` 


To solve this challenge, I followed the steps as listed below: 
- I first ran the `id` command to find out which group our user belongs in.
- Then I changed the cwd to root directory and then ran the `chgrp` command with the needed argument. 
- I then ran the `cat` command to get the flag. 

```bash
hacker@permissions~fun-with-groups-names:~$ id 
uid=1000(hacker) gid=1000(grp15113) groups=1000(grp15113)
hacker@permissions~fun-with-groups-names:~$ cd / 
hacker@permissions~fun-with-groups-names:/$ chgrp grp15113 flag 
hacker@permissions~fun-with-groups-names:/$ cat flag
pwn.college{MLAIEtYMk26KNqQFMk_ODrNmoUB.QXycjM1wSO3gjNzEzW}
hacker@permissions~fun-with-groups-names:/$
```

## What I learned 
From this challenge, I learned about the usage of the `id` command to figure out what group our user belongs in and how we can change the group ownership of a file to the group we want. 

## References 
- https://pwn.college/linux-luminarium/permissions/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Changing Permission 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to change the access of a file to ensure that we can read the file. 

## My solve 

**Flag:** `pwn.college{UUzkXxOZwC0xvdBCTIxlvYebheS.QXzcjM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `id` command to figure out the basic details of who we are. 
- I then changed the cwd to root directory and then used the `chmod` command to give access to the owner read, write and execute access. I misunderstood the `u` argument here, assuming it meant that the current user gains these accesses. However when I ran the `cat` command I got an error. 
- On re-reading the challenge statement, I understood that `u` is used to change the *owner* permissions not current user permission. Hence I modified the command to change the access permission for `o` users. 
- On then running the `cat` command to get the flag. 

```bash 
hacker@permissions~changing-permissions:~$ id 
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ cd /
hacker@permissions~changing-permissions:/$ chmod u+r flag
hacker@permissions~changing-permissions:/$ cat flag
cat: flag: Permission denied
hacker@permissions~changing-permissions:/$ chmod o+r flag
hacker@permissions~changing-permissions:/$ cat flag
pwn.college{UUzkXxOZwC0xvdBCTIxlvYebheS.QXzcjM1wSO3gjNzEzW}
hacker@permissions~changing-permissions:/$

```

## What I learned 
From this challenge, I learned that we do not always need to change the ownership of a file to access it, instead we can change the access permissions of the file to allow us to access it. 

## References 
- https://pwn.college/linux-luminarium/permissions/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Executable files 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to give executable permissions to a file and then run it to be able to get the flag. 

## My solve 

**Flag:** `pwn.college{kn7QTQK51K9_LnGa3CoYy1xPdn2.QXyEjN0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first ran the `ls -l /challenge/run` command to understand who was the owner and what group did the file belong to. 
- After figuring this out, I ran the `chmod` command to give executable access to owner as the owner is the hacker account only. 
- On running the `cat` command, we get the correct flag. 

```bash 

hacker@permissions~executable-files:~$ ls -l /challenge/run 
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run 
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{kn7QTQK51K9_LnGa3CoYy1xPdn2.QXyEjN0wSO3gjNzEzW}
hacker@permissions~executable-files:~$

```

## What I learned 
From this challenge, I learned that we can change the executable permissions of a file as well to allow certain users permissions to run the programs. 

## References 
- https://pwn.college/linux-luminarium/permissions/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Permission Tweaking Practice 
To solve this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to follow through the 8 rounds of permission changing in the `/challenge/pwn` file to get the flag. 

## My solve

**Flag:** `pwn.college{8aX1hApM8D8qc-zFvCCVcsdggnt.QXwEjN0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the `/challenge/run` program to get the instructions on how to change the permissions of the `/challenge/pwn` file. 
- On following through those 8 rounds, we finally get instructions to change the permissions of the `/flag` file and `cat` it to get the flag. 

```bash 
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
.
.
.
hacker@permissions~permission-tweaking-practice:~$ chmod g+rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+r /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{8aX1hApM8D8qc-zFvCCVcsdggnt.QXwEjN0wSO3gjNzEzW}
hacker@permissions~permission-tweaking-practice:~$

```

## What I learned 
From this challenge, I just gained more practice for the `chmod` command. 

## References 
- https://pwn.college/linux-luminarium/permissions/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Permissions setting practice 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions Module,* we need to solve another challenge which has 8 rounds of usage of `chmod` command to get to the flag. 

## My Solve 

**Flag:** `pwn.college{opBeEQARcIUJC_nVmo2Ciu2KISL.QXzETO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as below: 
- I first ran the `/challenge/run` program to get the instructions. Following those instructions, I got the final access to `/flag`. 
- I then ran the `cat /flag` command to get the final flag. 

```bash 

hacker@permissions~permissions-setting-practice:~$ /challenge/run 
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

.
.
.
.
hacker@permissions~permissions-setting-practice:~$ chmod u=rx,g=rwx,o=- /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ 
hacker@permissions~permissions-setting-practice:~$ chmod a=r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{opBeEQARcIUJC_nVmo2Ciu2KISL.QXzETO0wSO3gjNzEzW}
hacker@permissions~permissions-setting-practice:~$

```

## What I learned 
From this challenge, I learned how to set the unique permissions for owner, group and others at the same time in one command. 

## References 
- https://pwn.college/linux-luminarium/permissions/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: The SUID bit 
In this challenge of the *Linux Luminarium Dojo, Perceiving Permissions module,* we need to add the SUID bit to the permissions of the program and then run it to get the flag. 

## My solve 

**Flag:** `pwn.college{s3H3t_YnudFaw5fw9g0pt7OzS8_.QXzEjN0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- This was a pretty straight forward challenge, where we simply ran the `chmod` command with the needed argument to change the permissions of the program. 
- After this, we invoked the program `/challenge/getroot` which opened our root shell. Navigating to the root directory and then using the `cat` command allowed us to get the flag. 

```bash 
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot 
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# cd /
root@permissions~the-suid-bit:/# cat flag
pwn.college{s3H3t_YnudFaw5fw9g0pt7OzS8_.QXzEjN0wSO3gjNzEzW}
root@permissions~the-suid-bit:/#
```

## What I learned
From this challenge, I learned about the 'Set User ID' bit or the SUID bit, which allows us to run any program as the owner of the program, irrespective of what present user we are. This can be deadly as it allows us to create any file, set its SUID bit, change its owner to root and then call that program, all while we are a simple user on the linux. 

## References 
- https://pwn.college/linux-luminarium/permissions/
----------------------------------------------------------------------------------------------------------------------------------
