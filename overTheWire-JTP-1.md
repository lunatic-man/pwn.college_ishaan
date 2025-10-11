# Over The Wire Challenge
## Level 0: Connecting to Over The Wire host using ssh
In this level of the wargame, we need to use `ssh` command to connect to the host. We are given the hostname, the username and the password. 

## My solve 


**Flag:** `bandit0` 

I solved this challenge as under: 
- I first read through the challenge statement given on the website https://overthewire.org/wargames/bandit/bandit0.html 
- On reading through the challenge, I understood that we need to connect to the challenge using the `ssh` command and connect to a specific port. 
- I also learned that everytime we switch from one level to another, we will need to reconnect by utilizing a new username each time. 
- I did not know the argument we needed to add a port number to the `ssh` command and thus I first used the `man` command with `ssh` as an argument to understand how to add the port number to a username and hostname combo. 

```bash 
ishaan-mishra@ishaan-mishra-Lenovo-G505s:~$ man ssh

SSH(1)                                                 General Commands Manual                                               SSH(1)

NAME
       ssh — OpenSSH remote login client

SYNOPSIS
       ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address] [-c cipher_spec] [-D [bind_address:]port] [-E log_file]
           [-e  escape_char]  [-F  configfile]  [-I  pkcs11]  [-i  identity_file]  [-J  destination]  [-L  address] [-l login_name]
           [-m  mac_spec]  [-O  ctl_cmd]  [-o  option]  [-P  tag]  [-p  port]   [-R   address]   [-S   ctl_path]   [-W   host:port]
           [-w local_tun[:remote_tun]] destination [command [argument ...]]
       ssh [-Q query_option]
.
.
.
.
```
- In the SYNOPSIS of the `ssh` command, I saw that we can use the `-p` argument to add the port number to our command. Using this newfound knowledge, I crafted a command as below to login. 

```bash 
ishaan-mishra@ishaan-mishra-Lenovo-G505s:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit0@bandit.labs.overthewire.org's password: 

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit0@bandit:~$ 

```

- This completed the level, and the password needed to connect to the `bandit0` username was `bandit0` itself. 

## What I learned 
From this challenge, I learned about how we can add ports to the `username@hostname` combination that we are familiar with. 

## References 
- https://overthewire.org/wargames/bandit/bandit0.html
- Guidance from mentor
----------------------------------------------------------------------------------------------------------------------------------
## Level 0 -> Level 1 
In this level, we need to find the password of the next level which is stored in a `readme` file in the `home` directory. We need to use this password to connect to `bandit1`. 

## My solve 

**Flag:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If` 

To solve the level, I followed the steps as listed below: 
- I first changed my directory to `/home` by using the `cd` command. I then listed out all the contents present in the `/home` directory by using the `ls -l` command. 
- I then used the `ls /home/bandit0` to get the list of contents in the directory. 
- Finding the **readme** file, I used the `cat` command to get the password. 

```bash 
bandit0@bandit:~$ cd /home
bandit0@bandit:/home$ ls -l
total 592
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit0
drwxr-xr-x 2 root         root         4096 Aug 15 13:16 bandit1
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit10
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit11
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit12
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit13
drwxr-xr-x 3 root         root         4096 Aug 15 13:15 bandit14
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit15
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit16
drwxr-xr-x 3 root         root         4096 Aug 15 13:15 bandit17
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit18
drwxr-xr-x 2 root         root         4096 Aug 15 13:16 bandit19
drwxr-xr-x 2 root         root         4096 Aug 15 13:16 bandit2
drwxr-xr-x 2 root         root         4096 Aug 15 13:16 bandit20
drwxr-xr-x 2 root         root         4096 Aug 15 13:16 bandit21
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit22
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit23
drwxr-xr-x 2 root         root         4096 Aug 15 13:15 bandit24
.
.
.
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex23
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex24
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex25
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex3
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex4
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex5
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex6
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex7
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex8
drwxr-xr-x 2 root         root         4096 Aug 15 13:18 vortex9
bandit0@bandit:/home$ ls bandit0
readme
bandit0@bandit:/home$ cat bandit0/readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

bandit0@bandit:/home$ 

```

## What I learned 
From this challenge, I learned how to find the password as per the questions and I got a bit more comfortable navigating the file system of Over The Wire organization. 

## References
- https://overthewire.org/wargames/bandit/bandit1.html
- Guidance from mentor
----------------------------------------------------------------------------------------------------------------------------------
## Level 1 -> Level 2
In this level of the wargame, we need to find the password hidden in a file name `-` in the `/home` directory of the system. 

## My solve 

**Flag:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx` 

To find this flag, I followed the steps as listed below: 
- I first read the website to understand we need to look for the password. After understanding that we need to find a file named `-` in the home directory, I crafted a command using `find` to get all the files with `-` anywhere in there name. 
- Using `find /home -name -` command, I got all the files with `-` anywhere in there name. 

```bash 
bandit1@bandit:~$ find /home -name -
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/leviathan4/.trash’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/leviathan0/.backup’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
/home/bandit1/-
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
bandit1@bandit:~$

```

- Out of all these files/paths, there is only one file that we allowed to access. Hence using the `cat` command with the given path, I got the password. 

```bash 

bandit1@bandit:~$ cat /home/bandit1/-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
bandit1@bandit:~$ 

```

## What I learned 
From this challenge, I got more practice in using the `find` command along with needed arguments. 

## References
- https://overthewire.org/wargames/bandit/bandit2.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 2 -> Level 3 
In this level of the wargame, we need to find a file which has spaces in its file name. 

## My solve 

**Flag:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx` 

To solve this level, I followed the steps as listed below: 
- I first read the level statement to understand what was asked of us. In that level statement, the mentioned helpful reading material as google searching "spaces in filename". 
- Looking up the string as given in question, I got to know that when there are spaces in a file name, we enclose the file name in double quotes (""). 
- Utilizing this along with `find` command, I got the result as below: 

```bash 
bandit2@bandit:~$ find /home -name "--spaces in this filename--"
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/leviathan4/.trash’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/leviathan0/.backup’: Permission denied
/home/bandit2/--spaces in this filename--
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
bandit2@bandit:~$

```

- Analyzing the above results, I realized that we have access to only one file. Using `cat` command along with the path of this file as an argument, I found the password. 

```bash 
bandit2@bandit:~$ cat /home/bandit2/"--spaces in this filename--"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
bandit2@bandit:~$ 

```

## What I learned 
From this level, I learned how we can search for file names with space in their name and how we can utilize their name like any other file name without spaces. 

## References 
- https://overthewire.org/wargames/bandit/bandit3.html
- https://stackoverflow.com/questions/23019471/how-can-i-go-to-a-directory-whose-file-name-has-spaces-between-them-in-the-linux
----------------------------------------------------------------------------------------------------------------------------------
## Level 3 -> Level 4 
In this level, we need to find a hidden file in the `inhere` directory. 


## My solve 

**Flag:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ` 

To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge statement to understand what they want us to find. After reading the statement, I realized they wanted us to find a hidden file in the `inhere` directory. 
- Finding the directory using `find / -name inhere` command, we found a couple of directories to which we have access. However we need the password in the `/home/bandit3/inhere` directing. 
- Moving to that directory and using `ls -a` command, we find the file which contains the password. 

```bash 
bandit3@bandit:~$ find / -name inhere
find: ‘/sys/kernel/tracing/osnoise’: Permission denied
find: ‘/sys/kernel/tracing/hwlat_detector’: Permission denied
find: ‘/sys/kernel/tracing/instances’: Permission denied
find: ‘/sys/kernel/tracing/trace_stat’: Permission denied
find: ‘/sys/kernel/tracing/per_cpu’: Permission denied
find: ‘/sys/kernel/tracing/options’: Permission denied
.
.
.
find: ‘/home/bandit31-git’: Permission denied
/home/bandit5/inhere
find: ‘/home/bandit5/inhere’: Permission denied
/home/bandit3/inhere
find: ‘/home/leviathan4/.trash’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/leviathan0/.backup’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
/home/bandit4/inhere
bandit3@bandit:~$ cd /home/bandit3/inhere
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-you
cat: ...Hiding-From-you: No such file or directory
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
bandit3@bandit:~/inhere$ 

```

## What I learned 
This level was a practice level for the arguments of `ls` command and served as a nice refresher. 

## References
- https://overthewire.org/wargames/bandit/bandit4.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 4 -> Level 5 
In this level, we need to find the only human readable file in the `inhere` directory in user files. 

## My solve 

**Flag:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw` 

To solve this challenge, I followed the steps as listed below: 
- I first listed the contents of the home directory, usins `ls` command. I did this because in the previous few challenges, we always moved to the `/home` directory to end up in the original directory only. My assumption stood correct as I found the `inhere` directory listed as the contents. 
- I then used the `cd` command to get into the `inhere` directory. Once inside the directory, I used the `ls -l` command to find the contents of the directory. 
- Seeing that there were 9 files, I used the `cat` command with `[]` globs to go through all the files in one go. This actually gave me an error in the first go and I realized that the files are named in such a way that shell would assume these are arguments. To get around this issue, I used `cat ./-file0[0-9]` to get the outputs.

```bash 
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls -l
total 40
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file00
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file01
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file02
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file03
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file04
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file05
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file06
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file07
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file08
-rw-r----- 1 bandit5 bandit4 33 Aug 15 13:16 -file09
bandit4@bandit:~/inhere$ cat -file0[0-9]
cat: invalid option -- 'f'
Try 'cat --help' for more information.
bandit4@bandit:~/inhere$ cat ./-file0[0-9]
\�G�I�d�� �`"��g���	'�������Y��:bl�A��t�1�ν%gM�������
                                                         ��u.Tq�`h���Ee�+�<��"!^"�Jߑߟ����>jŠ���C�f�w��f>�<?��>��@F��kYq~Jjs�o��;���6���d�H@�9��I�}�v,��C�����Cy>f�|7�`i�}
                                  �ت�=ؑ�Hz����1�Uk�U���켼�U4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
x����/vSژ�5f`}�3Y�ׯ��=9]�
�qf�`HԿB�K�����E��\G��D

```

## What I learned 
This challenge served as a practice for the `cat` and `ls` commands. One new thing I learned from this was how to we can give files with `-` in the start of their name as files for the commands instead of arguments. 

## References
- https://overthewire.org/wargames/bandit/bandit5.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 5 -> Level 6
In this level of the Bandit war game, we need to find a file which is 
- Human Readable 
- 1033 bytes in size 
- not executable 



## My solve 

**Flag:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG` 

To solve this challenge, I followed the steps as listed below:
- I first read through the manpage of `find` command as I had a gut feeling that this command would take an argument that would allow us to find files based on size. 
- Opening and reading the manpage using `man find` I found the argument I was looking for: 

```bash 

bandit5@bandit:~/inhere/maybehere07$ man find




.
.
.

       -size n[cwbkMG]
              File uses less than, more than or exactly n units of space, rounding up.  The following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for kibibytes (KiB, units of 1024 bytes)

              `M'    for mebibytes (MiB, units of 1024 * 1024 = 1048576 bytes)

              `G'    for gibibytes (GiB, units of 1024 * 1024 * 1024 = 1073741824 bytes)

              The  size is simply the st_size member of the struct stat populated by the lstat (or stat) system call, rounded up as
              shown above.  In other words, it's consistent with the result you get for ls -l.  Bear in mind that the `%k' and `%b'
              format specifiers of -printf handle sparse files differently.  The `b' suffix  always  denotes  512-byte  blocks  and
              never 1024-byte blocks, which is different to the behaviour of -ls.

              The  +  and  -  prefixes signify greater than and less than, as usual; i.e., an exact size of n units does not match.
              Bear in mind that the size is rounded up to the next unit.  Therefore -size -1M is not equivalent to -size -1048576c.
              The former only matches empty files, the latter matches files from 0 to 1,048,575 bytes.
.
.
.

```

- After finding out the necessary argument, I changed the directory to `inhere` using `cd` command. 
- Once inside the directory I listed out the contents of the directory using the `ls` command. 

```bash
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ 
```

- After seeing all these directories, I decided to craft a `find` command which would find all files which are 1033bytes in size. 
- Using the help from manpage, I created the command `find ~/inhere -size 1033c`.

```bash 
bandit5@bandit:~/inhere$ find ~/inhere -size 1033c 
/home/bandit5/inhere/maybehere07/.file2
bandit5@bandit:~/inhere$
```

- Since there was only file which was 1033 bytes in size, I did not have to do much else, simply used the `cat` command to get the result. 

```bash 
bandit5@bandit:~/inhere$ cd maybehere07
bandit5@bandit:~/inhere/maybehere07$ ls -a
.  ..  -file1  .file1  -file2  .file2  -file3  .file3  spaces file1  spaces file2  spaces file3
bandit5@bandit:~/inhere/maybehere07$ cat .file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

```

## What I learned 
From this level of the challenge, I learned about how we can use `-size` argument along with `find` command to find files which are of specific sizes

## References 
- Manpage of `find` command. 
----------------------------------------------------------------------------------------------------------------------------------
## Level 6 -> Level 7 
In this challenge level of the Bandit war game, we need to find a file hidden somewhere on the server which has the following properties 
- owned by bandit7 
- owned by group bandit6 
- is 33 bytes in size

## My solve 

**Flag:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj` 

To solve this challenge, I followed the steps as listed below: 
- I again read through the manpage of the `find` command to find necessary arguments as shown below

```bash 
bandit6@bandit:~$ man find

.
.
.
       -group gname
              File belongs to group gname (numeric group ID allowed).
.
.
.       -size n[cwbkMG]
              File uses less than, more than or exactly n units of space, rounding up.  The following suffixes can be used:

              `b'    for 512-byte blocks (this is the default if no suffix is used)

              `c'    for bytes

              `w'    for two-byte words

              `k'    for kibibytes (KiB, units of 1024 bytes)

              `M'    for mebibytes (MiB, units of 1024 * 1024 = 1048576 bytes)

              `G'    for gibibytes (GiB, units of 1024 * 1024 * 1024 = 1073741824 bytes)

              The  size is simply the st_size member of the struct stat populated by the lstat (or stat) system call, rounded up as
              shown above.  In other words, it's consistent with the result you get for ls -l.  Bear in mind that the `%k' and `%b'
              format specifiers of -printf handle sparse files differently.  The `b' suffix  always  denotes  512-byte  blocks  and
              never 1024-byte blocks, which is different to the behaviour of -ls.

              The  +  and  -  prefixes signify greater than and less than, as usual; i.e., an exact size of n units does not match.
              Bear in mind that the size is rounded up to the next unit.  Therefore -size -1M is not equivalent to -size -1048576c.
              The former only matches empty files, the latter matches files from 0 to 1,048,575 bytes.
.
.
.
       -user uname
              File is owned by user uname (numeric user ID allowed).
.
.
.
```
- After reading the manpage, I crafted a command `find / -user bandit7 -group bandit6 -size 33c` which satisfies all needed arguments to find the file. 
- A lot of files showed up, but most of them were inaccessible to us, so I read through files to find only one file was accessible to us. 
- Using `cat` to get the contents of the file, I found the password for the next level. 

```bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 
find: ‘/sys/kernel/tracing/osnoise’: Permission denied
find: ‘/sys/kernel/tracing/hwlat_detector’: Permission denied
find: ‘/sys/kernel/tracing/instances’: Permission denied
.
.
.
find: ‘/var/lib/amazon’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
.
.
.
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
bandit6@bandit:~$ ls -l /var/lib/dpkg/info/bandit7.password
-rw-r----- 1 bandit7 bandit6 33 Aug 15 13:16 /var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$

```

## What I learned 
From this challenge, I learned how to use the `-user` argument and `-group` argument along with `find` command to find files which are owned by specific users or groups. 

## References
- Manpage of `find` command
----------------------------------------------------------------------------------------------------------------------------------
## Level 7 -> Level 8 
In this challenge, we need to find a file with the name `data.txt` and then find the password for the next level in it, by using `grep` command.


## My Solve

**Flag:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc` 

To solve this challenge, I followed the steps as listed below: 
- I first ran the find command to look for files with the name `data.txt.` 

```bash 
bandit7@bandit:~$ find / -name data.txt
find: ‘/sys/kernel/tracing/osnoise’: Permission denied
find: ‘/sys/kernel/tracing/hwlat_detector’: Permission denied
find: ‘/sys/kernel/tracing/instances’: Permission denied
.
.
.
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
/home/bandit9/data.txt
find: ‘/home/leviathan4/.trash’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
/home/bandit11/data.txt
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/leviathan0/.backup’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/ubuntu’: Permission denied
/home/bandit7/data.txt
find: ‘/home/bandit28-git’: Permission denied
/home/bandit12/data.txt
find: ‘/home/bandit29-git’: Permission denied
/home/bandit8/data.txt
find: ‘/home/drifter8/chroot’: Permission denied
/home/bandit10/data.txt
bandit7@bandit:~$

```
- On analyzing the results, I understood that we needed to look for the password in the `/home/bandit7/data.txt` file. 
- Using `cat` along with piping for `grep` I found the password next to `millionth` keyword. 

```bash 
bandit7@bandit:~$ cat /home/bandit7/data.txt | grep millionth
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
bandit7@bandit:~$ 
```

## What I learned 
This challenge served as a practice for basic piping and `grep` command. 

## References 
- https://overthewire.org/wargames/bandit/bandit8.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 8 -> Level 9 
In this challenge, we need to list out the unique flag in the entire list of data and fake passwords.


## My solve 


**Flag:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM` 

To solve this challenge, I followed the steps as listed below: 
- I first read the manpage of the `uniq` command to understand what it does and how I can use it. 
- On reading the manpage of the command, I realized that this is exactly the command I needed. Creating a command `uniq -u /home/bandit8/data.txt`, I tired finding the password, however I got a the entire list as shown below

```bash 
bandit8@bandit:~$ uniq -u /home/bandit8/data.txt
ZzQDv5Imr9y5XSYGD3r61uP1fjXAhuod
bjQCibPw40urmZNBNNpv8zTOaFVFWSbv
uG6s7CFzkh4lqmcJtwLIxa4sU1v8gkhU
WkcJmDs54n2OynP1oYNjZ64kXa4KjVJY
KtzxzcvxasfTcGEobGpZ9SDoCGtiCqoa
ZzQDv5Imr9y5XSYGD3r61uP1fjXAhuod
EVUICc3XWvOsOyCzwfBk4lP9Phrq0yrx
.
.
.
yPp4j25oBTCzQdXC6fpsn4fJMJG037ld
piNbRUIYbHzsniIMBDOObx7BgDSWa40H
3PhmgEv7YEbzIl0pjAZ6ik3atmygedX1
ukWEPonuKwvEKvX0eNw6NNbChvzltM5M
3PRLMUKYoKCLPW9mJBO6lwJ8YphI6uQV
5kxIqMtP95PnmEXDVn1CcbNiHabFQgvl
08DeKfqaKdvvCatYWrGgkKe8pPDKmUDx
BgX32zPP0P13h0JPX51VAeyGREH5HINC
wGkPzkDSLDmsfycqfhPLrnX5AnT2U5ei
aGQCdiWCF03SXJqQmHABE5gbAEDq8Vhz
gXy9cjec58lCUZttQXB6kojhJUTFsD14
bandit8@bandit:~$ 

```
- Confused, I googled up how to find unique lines in a file and found a command which told us to first sort the data, then use `uniq -u`. 
- I ran the command `sort /home/bandit8/data.txt | uniq -u` and found the password. 

```bash 
bandit8@bandit:~$ sort /home/bandit8/data.txt | uniq -u 
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

```

## What I learned 
From this challenge, I learned about the existence of `uniq` command and how we can use it to filter out and find specific lines in a file. 

## References
- https://stackoverflow.com/questions/13778273/find-unique-lines
- AI discussions
----------------------------------------------------------------------------------------------------------------------------------
## Level 9 -> Level 10 
In this challenge, we need to find a flag which is human readable format and has a lot of '=' at its starting.


## My Solve 

**Flag:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey` 

To solve this challenge, I followed the steps as below: 
- I first read the challenge statement to figure out the possible commands that we can use. 
- On reading the challenge, I understood that I needed to use the `strings` command somewhere to get the flag. 
- I then proceeded to read the manpage of `strings` command and understood that this command filters out all data and prints only printable characters. Using this with `cat` command and basic piping, I got all printable characters. 
- In these random chars, I saw the lines starting with many '=' and found the flag by simply scrolling down. 

```bash 
bandit9@bandit:~$ man strings
bandit9@bandit:~$ cat /home/bandit9/data.txt | strings
tvFJ
*M'Jg
>Id#{
VN5ZTH
9~T4
LkoV
$.`[
>K3Z
6tO/
PCa/
Z56Tn
q$A2
nx!d
Nf&c
wQ\_
:7{4
\KL/
qN%y,J
========== theg
>5&y
A\~pd
VQ=97
.
.
.
+`Z{
o5(r
?"v8
#F9\*
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
w@RU
YxP{
uI,'\
KMFZ/
.
.
.
igar[
&b0R
&x,[g
O5W^%
bandit9@bandit:~$ 

```

## What I learned 
From this challenge, I was introduced to the `strings` command and how to use it. 

## References 
- https://overthewire.org/wargames/bandit/bandit10.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 10 -> Level 11
In this challenge, we need to decode the data which is base64 encoded. 


## My solve 

**Flag:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr` 

To solve this challenge, I used the steps as listed below: 
- I first read through the challenge to figure out what command we needed to use to decode the data. I found `base64` as the command that we would require. 
- I then read the manpage of `base64` command. This told me that the command follows syntax of `base64 [OPTION] [FILENAME]`.
- Using this, I crafted a command, `base64 -d /home/bandit10/data.txt` and got the password. 

```bash 
bandit10@bandit:~$ man base64
bandit10@bandit:~$ base64 -d /home/bandit10/data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
bandit10@bandit:~$ 

```

## What I learned 
From this challenge, I learned about the existence of the `base64` command and how we can use it to decode the data given to us in base64 format, as well as encode data to base64 format. 

## References 
- https://overthewire.org/wargames/bandit/bandit11.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 11 -> Level 12 
In this challenge, we need to decode the data which has been rotated by 13 positions to get the flag.

## My solve 

**Flag:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4` 

To solve this challenge, I followed the steps as listed below: 
- I first used `cat` command to get the entire string printed out on the terminal. 
- I then copied this string and used https://cyberchef.io/ to get the password un-rotted. 

```bash 
bandit11@bandit:~$ cat /home/bandit11/data.txt
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
bandit11@bandit:~$ 

```
## What I learned 
From this challenge, I learned about the rotation of positions and how we can rotate some encoded data back to get the original message back. 

## References 
- https://overthewire.org/wargames/bandit/bandit12.html
----------------------------------------------------------------------------------------------------------------------------------
## Level 12 -> Level 13 
In this challenge, we need to consistently unzip a file until we are able to find a file with ASCII text. 

## My solve 

**Flag:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

To solve this challenge, I followed the steps as below: 
- I first created a directory in `/tmp` of the instance, called `unzip` (`/tmp/unzip` is the path). In this directory, I copied `data.txt` file using the `cp` command. 
- Now I did not know how decompression and compression works in Linux before solving this challenge. So I took help of an AI tool to discuss how it works. 
- I then re-read the challenge statement to understand that the data inside the `data.txt` file is actually a hexdump of another file. 
- Realizing this, I used the `cat` command to read the hexdump. On reading the first few bytes of the hexdump, called as the magic bytes as I learned, I understood that this file was `gzip` compressed. 
```bash
bandit12@bandit:~$ cat data.txt
00000000: 1f8b 0808 0933 9f68 0203 6461 7461 322e  .....3.h..data2.
00000010: 6269 6e00 0148 02b7 fd42 5a68 3931 4159  bin..H...BZh91AY
00000020: 2653 59be 9d9d 9600 001f ffff fe7f fbcf  &SY.............
00000030: af7f 9eff f7ee ffdf bff7 fef7 ddbe 9db7  ................
00000040: bf9f 9f5f ca6f fffe d6fb feff b001 3ab3  ..._.o........:.
00000050: 0403 40d0 0000 00d0 01a0 03d4 0000 0346  ..@............F
00000060: 41a1 9000 0000 1900 0190 0686 8191 a326  A..............&
00000070: 1340 0c8c 4d0f 4d4c 4403 468d 0d1a 0001  .@..M.MLD.F.....
.
.
.
000001b0: 6241 3876 4edf 6038 0b60 277c d2ca 7908  bA8vN.`8.`'|..y.
000001c0: b1f3 a93c 23d0 277b 215c 7498 b2a1 01dd  ...<#.'{!\t.....
000001d0: 563b be47 3fdc a008 0f08 82c7 2044 c8da  V;.G?....... D..
000001e0: a241 c91c c3ee f1a1 9b98 25eb 5212 3fb1  .A........%.R.?.
000001f0: e545 2469 108f 7f01 e7c9 faed cd3e 9f08  .E$i.........>..
00000200: 97bc 1b04 a087 e826 0993 65d3 13b6 5365  .......&..e...Se
00000210: 3c6d 10e5 1d85 66ab 0497 6242 8799 8112  <m....f...bB....
00000220: 61a0 87dc fcfb 9274 774a c918 d5ce 3c0f  a......twJ....<.
00000230: d346 95c8 1e30 42a6 a3b7 a93b 67f3 186c  .F...0B....;g..l
00000240: 904c 842c 30c5 e1b2 b841 05e0 7144 2a60  .L.,0....A..qD*`
00000250: ca14 0a52 f589 fe2e e48a 70a1 217d 3b3b  ...R......p.!};;
00000260: 2c19 d8f7 0e48 0200 00                   ,....H...
bandit12@bandit:~$ 
```
- I then tried out a few commands which failed, I even read up the manpages of these commmands to realise what mistake I was doing, but I was not able to figure it out. So I took the help of AI tools to get advice.
- After discussing with AI, I learned that we cannot directly send the data of a hexdump to `gunzip`. This is because `gunzip` expects its input to be raw GZIP-compressed binary data. 
- Using this knowledge, I first read through all the manpages of the command available in the challenge statement, and learned how to use each one, along with how to use `xxd` command to reverse the hexdump into raw binary. 
```bash 
bandit12@bandit:/tmp/unzip$ man xxd 
bandit12@bandit:/tmp/unzip$ xxd -r data1.txt
�       3�hdata2.binH��BZh91AY&SY��������ϯ�����߿���ݾ�����_�o�������:�@����FA�������&@
�����dbhhh�P���                                                                      �MMLDF�
��4��hѣM4�x�2  �  '����d���*�-�u��g#�Ƌ|b��u8�e�R$��
                                                   3�!�6�����[<���\A�
                                                                     t�bV�R�7��Z��ؓ&&籏�v����<,�%�̇Y�T6Jg��:�أh��g�Q�+ѲL��03�z��bş�	ï�v��i�hͶm^;���zEqp��L����
�,3����
�1`�F<���C;���Z���Y/���c�I�y�8bA8vN�`8
                                      `'|����<#�'{!\t����V;�G�� D�ڢA���񡛘%�R?��E$i������>����&	�e��Se<m��f��bB���a������twJ���<�F��0B����;g�l�L�,0�ᲸA�qD*`�
R���.�p�!};;,��Hbandit12@bandit:/tmp/unzip$
```
- On seeing the above, I realized that this is the output of the `xxd -r` command. Thus piping it to another file, i.e. `data1.bin` and then using the `file` command to figure out what type of compression it is, we get the following result: 

```bash 
bandit12@bandit:/tmp/unzip$ xxd -r data1.txt > data1.bin
bandit12@bandit:/tmp/unzip$ file data1.bin
data1.bin: gzip compressed data, was "data2.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 584
bandit12@bandit:/tmp/unzip$
```

- On trying to solve the challenge using the command `gunzip data1.bin > data2.bin` I was not getting the result, and it was showing an error as below: 

```bash 
bandit12@bandit:/tmp/unzip$ gunzip data1.bin > data2.bin 
gzip: data1.bin: unknown suffix -- ignored
bandit12@bandit:/tmp/unzip$ 
```
- I then discussed this with AI and realized that this is because `gunzip` also expects the files to have `.gz` as the final extension. The workaround for this, with help of AI tools is creating a command which sends the data of the file to `gunzip` without needing to change the extension. 
- With the above knowledge, I created a command `cat data1.bin | gunzip > data2.bin` and ran it to get the data uncompressed once. 
```bash 
bandit12@bandit:/tmp/unzip$ cat data1.bin | gunzip > data2.bin
bandit12@bandit:/tmp/unzip$ file data2.bin 
data2.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/unzip$
```
- Continuing the above process 8 times, and changing the decompression method each time, we got the final data as plain ASCII text which contained the flag. 

```bash 
bandit12@bandit:/tmp/unzip$ cat data2.bin | bunzip2 > data3.bin
bandit12@bandit:/tmp/unzip$ file data3.bin 
data3.bin: gzip compressed data, was "data4.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/unzip$ cat data3.bin | gunzip > data4.bin 
bandit12@bandit:/tmp/unzip$ file data4.bin 
data4.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/unzip$ tar -rf data4.bin 
bandit12@bandit:/tmp/unzip$ ls
data1.bin  data1.txt  data2.bin  data3.bin  data4.bin
bandit12@bandit:/tmp/unzip$ file data4.bin 
data4.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/unzip$ tar -rf data4.bin > data5.bin 
bandit12@bandit:/tmp/unzip$ ls
data1.bin  data1.txt  data2.bin  data3.bin  data4.bin  data5.bin
bandit12@bandit:/tmp/unzip$ file data5.bin
data5.bin: empty
bandit12@bandit:/tmp/unzip$ rm data5.bin 
bandit12@bandit:/tmp/unzip$ cat data4.bin 
data5.bin0000644000000000000000000002400015047631411011242 0ustar  rootrootdata6.bin0000644000000000000000000000033615047631411011251 0��V�+�ц��2ԶZ��"2�:%'�t*T���0Y�����i�2'����JR�Y  �ܑN$Wx�bandit12@bandit:/tmp/unzip$ man tar
bandit12@bandit:/tmp/unzip$ tar -xf data4.bin > data5.bin 
bandit12@bandit:/tmp/unzip$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/unzip$ tar -xf data5.bin > data6.bin 
bandit12@bandit:/tmp/unzip$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/unzip$ cat data6.bin | bunzip2 > data7.bin 
bandit12@bandit:/tmp/unzip$ file data7.bin 
data7.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/unzip$ tar -xf data7.bin > data8.bin
bandit12@bandit:/tmp/unzip$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Fri Aug 15 13:15:53 2025, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/unzip$ cat data8.bin | gunzip > data9.bin 
bandit12@bandit:/tmp/unzip$ file data9.bin 
data9.bin: ASCII text
bandit12@bandit:/tmp/unzip$ cat data9.bin 
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
bandit12@bandit:/tmp/unzip$
```

## What I learned 
From this challenge, I learned about the existence of a lot of commands, like `xxd`, `gzip/gunzip`, `bzip2/bunzip2`, `tar`. I also learned about data works in Linux Systems and what is the crucial difference between hexdump and the hexdump converted to raw binary. Along with this, I learned about the _Magic Bytes_ of a hexdump file as well to figure out what type of a file it is. 

## References 
- https://overthewire.org/wargames/bandit/bandit13.html
- https://gemini.google.com/app/14aabf9556397701
----------------------------------------------------------------------------------------------------------------------------------
## Level 13 -> Level 14 
To solve this challenge, we need to simply use the private sshkey given to us to connect to the next level by using `ssh` 

## My solve 

**Flag:** `SSH Private Key` / `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS` (Found from next level)

To solve this challenge, I followed the steps as listed below: 
- I first ran the `ls` command to check if the private key existed in the cwd or not. 

```bash 
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$
```
- I then used the `ssh`command with the necessary arguments to connect to the next level. 

```bash 
bandit13@bandit:~$ ssh bandit14@bandit.labs.overthewire.org -p 2220 -i ./sshkey.private
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

backend: gibson-1

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit14@bandit:~$ 

```

## What I learned 
I read through the Helpful Reading Material given in the challenge to understand how `ssh` works and what you actually mean by that, which turned out to be very informative. 

## References 
- https://overthewire.org/wargames/bandit/bandit14.html
- https://help.ubuntu.com/community/SSH/OpenSSH/Keys
---------------------------------------------------------------------------------------------------------------------------------
## Level 14 -> Level 15
In this challenge, we need to submit password of the current level to a localhost on port 30000 to gain the password for the next level. 

## My solve 

**Flag:** `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo` 

To solve the challenge, I followed the steps as listed below: 
- I first tried using `ssh` command to connect to the `localhost` on `port 30000`. However, it failed at that. So I read up on the reading material of the challenge, which introduced me to the concept of loopback. 
- This did not really get me the answer to why this failed so I asked the help of AI and tried to understand why `ssh` fails. I learned that this failed because the service running on the port was not a SSH, and hence it fails. 
- I then used the `nc` command, i.e., `nc localhost 30000` and it kept on waiting for an input from me, hence I gave the password I found in `/etc/bandit_pass/bandit14` as the input and I got the flag. 

```bash 
bandit14@bandit:~$ ssh localhost -p 30000
Connection closed by 127.0.0.1 port 30000
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

^Z
[2]+  Stopped                 nc localhost 30000
bandit14@bandit:~$ 
```

## What I learned 
Due to this challenge, I got curious about the differences between `nc` and `ssh` command, so I read up on the differences to make sure I understand how they work differently, because `nc` just established a connection, while `ssh` ensured it was a secure connection. The downside of `ssh` is that it can only run on ports which are listening for `ssh` connections, while `nc` works on almost all. I also read up on the Helpful Reading Material to understand how exactly the internet works, what are ports, IP Addresses and hosts. 

## References 
- https://overthewire.org/wargames/bandit/bandit15.html
- https://gemini.google.com/app/14aabf9556397701
---------------------------------------------------------------------------------------------------------------------------------
## Level 15 -> Level 16 
In this challenge, we need to establish a connection to the localhost on port 30001 and submit the password of `Bandit15` to get the password for `Bandit16` 

## My solve 

**Flag:** `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx` 

To solve this challenge, I followed the steps as listed below: 
- From reading the challenge statement, I could figure out that we had to use `openssl` command in our solution, thus I read up on its manpage to understand how it works. I didnt fully understand the `openssl` but I could find a subcommand `s_client` which seemed like it could work. 
- This hypothesis was confirmed as `s_client` was also one of the commands given in the challenge statement. Then I tried running the commands as shown below: 

```bash 
bandit15@bandit:~$ man openssl
bandit15@bandit:~$ openssl s_client localhost 30001
s_client: Use -help for summary.
bandit15@bandit:~$
```
- This however did not work as I did not pass the host and ports in the expected format. Thus I ran the following command to get the help as the stderr told us to. 

```bash 
bandit15@bandit:~$ openssl s_client -help
Usage: s_client [options] [host:port]

General options:
 -help                      Display this summary
 -engine val                Use engine, possibly a hardware device
 -ssl_client_engine val     Specify engine to be used for client certificate operations
.
.
.
 -provider-path val         Provider load path (must be before 'provider' argument if required)
 -provider val              Provider to load (can be specified multiple times)
 -propquery val             Property query used when fetching algorithms

Parameters:
 host:port                  Where to connect; same as -connect option
bandit15@bandit:~$ 
```
- From the above help, I could figure out that I needed to pass the host and port as `host:port` to get the connection. Doing that, I could establish a connection to `localhost:30001` and gave the password of the current level to get the password of the next level. 

```bash 
bandit15@bandit:~$ openssl s_client localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 1E7F573225D28580855F3CB1CE3734D5AF1C9D42B84864F2A551A85E1A182A51
    Session-ID-ctx: 
    Resumption PSK: 846D17D7A5C9A1FBE074E96E671EF3B101D9A0CC23ADF51B3A871F28B315ECFEDE5984A365D3CAC18793E02CBB7D246F
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - fd 2d 15 cd 32 69 17 b3-ac 5c 33 bf 46 51 e4 76   .-..2i...\3.FQ.v
    0010 - 54 65 9d 0a 15 97 bf 49-36 66 7a a3 37 92 b0 c1   Te.....I6fz.7...
    0020 - 38 df 4e 7c df 28 49 1b-a4 3d 5d 55 9f 94 a0 fa   8.N|.(I..=]U....
    0030 - af 91 ac 5f 46 88 dd 05-af 06 c1 0e 11 4e e3 1a   ..._F........N..
    0040 - 9f cc 13 aa 0c be 2b 6e-76 c3 b7 4e c6 68 6a f8   ......+nv..N.hj.
    0050 - 6d 77 77 5f ae 62 e9 30-74 57 7c 2f 20 a8 3c e7   mww_.b.0tW|/ .<.
    0060 - 9d d0 f1 47 d0 b3 bf 35-ee d2 0d ec 85 4e bc cd   ...G...5.....N..
    0070 - 03 5c 59 c9 94 85 dd 33-28 24 88 6b 75 1e df 6e   .\Y....3($.ku..n
    0080 - 5a 3d b2 97 0a ac 16 24-88 34 db 29 d0 6c c1 b0   Z=.....$.4.).l..
    0090 - 6f a7 e2 29 32 94 62 2a-63 a9 85 bd 76 46 00 84   o..)2.b*c...vF..
    00a0 - 9a 5c 20 62 93 73 e7 5a-4a 97 cf 85 3e 77 7b 95   .\ b.s.ZJ...>w{.
    00b0 - d7 9a 49 8b e0 42 e2 e8-f7 07 b8 25 87 64 e8 df   ..I..B.....%.d..
    00c0 - 2d ce 83 52 84 4d 7e 2d-41 fc b7 83 f1 df 78 86   -..R.M~-A.....x.
    00d0 - bf af 1f fd 5a 7f ac 5c-bb a7 bc 03 94 02 1a 38   ....Z..\.......8

    Start Time: 1760012629
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: EDF139A77161D65358AE43866F0042A45505E9FFD2CD02240605D20578FC7A01
    Session-ID-ctx: 
    Resumption PSK: E240D11659951DC5C6F2B32EF907EC9998FC8DBB92D8EDCCA297C2C0EC183993C070E0286BDC9F9EB04977DD735FF831
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - fd 2d 15 cd 32 69 17 b3-ac 5c 33 bf 46 51 e4 76   .-..2i...\3.FQ.v
    0010 - 04 6c 7b 81 8e 71 a0 46-56 f5 52 c6 2c c1 46 85   .l{..q.FV.R.,.F.
    0020 - 5d 73 c4 4a a6 14 e6 5d-3f 44 14 f9 75 fd 5c 3f   ]s.J...]?D..u.\?
    0030 - 0e e9 0e 40 2a 63 86 b8-ac 8f 44 3a 82 75 ee b5   ...@*c....D:.u..
    0040 - 62 06 41 0d b6 f8 30 eb-df 12 5e 4d cd 8c 9c 79   b.A...0...^M...y
    0050 - 9a c2 3b e5 d7 66 af 4e-c1 58 83 cc 7b 19 e5 5e   ..;..f.N.X..{..^
    0060 - 7e c4 20 44 3c 28 08 0b-33 bb 44 98 2c d0 db 8a   ~. D<(..3.D.,...
    0070 - f6 5e 33 e1 47 68 f8 1f-23 22 35 27 00 f6 32 2b   .^3.Gh..#"5'..2+
    0080 - e0 a9 35 8f 5e ac f7 e6-89 86 e5 93 0f f7 51 a2   ..5.^.........Q.
    0090 - 1c 31 d4 75 4c 84 cc 17-59 b9 9f ee 70 74 66 3a   .1.uL...Y...ptf:
    00a0 - d0 91 c5 97 6a 99 5e 0c-5a 8d 0f 8a 61 b5 b8 7e   ....j.^.Z...a..~
    00b0 - 58 df 80 43 f9 db a4 f4-2a b0 54 33 3c 6d 01 af   X..C....*.T3<m..
    00c0 - 69 b5 44 d7 1c 54 59 7b-d7 a7 b2 7d f7 55 8a e3   i.D..TY{...}.U..
    00d0 - de 8a 27 4e 82 b4 f0 b7-68 9e c7 8d 12 6d 98 24   ..'N....h....m.$

    Start Time: 1760012629
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
bandit15@bandit:~$ 
```

## What I learned 
From this challenge, I learned the crucial difference between `ssh`, `nc` and `openssl` commands. `ssh` command is used to establish control over the machine located remotely, similar to RDP(Remote Desktop Protocol) of Windows systems, while `nc` and `openssl` are used to establish connection to the ports of a host to access data or services being delivered on them. `nc` establishes an unsecure connection while `openssl` established as secure connection using SSL/TlS protocols.

## References
- https://overthewire.org/wargames/bandit/bandit16.html
- https://en.wikipedia.org/wiki/Transport_Layer_Security
---------------------------------------------------------------------------------------------------------------------------------
## Level 16 -> Level 17 
In this level we need to find the password of the next level by connecting to a port which is giving us the password back. 

## My solve 

**Flag:** `RSA key` / `EReVavePLFHtFlFsjn3hyzMlvSuSAcRD` (found after logging in using RSA key)

To solve this challenge, I followed the steps as listed below: 
- I first tried running a normal `nmap` scan to see what ports were open on `localhost`. I had some prior experience with `nmap` so I ran the basic command `nmap localhost` and got the following result.

```bash 
bandit16@bandit:~$ nmap localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-10-09 15:02 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
Not shown: 990 closed tcp ports (conn-refused)
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
8888/tcp  open  sun-answerbook
11111/tcp open  vce
12345/tcp open  netbus
30000/tcp open  ndmps
50001/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
bandit16@bandit:~$ 

```

- However this did not give any fruitful results as I knew that the port was between 31000-32000. So I changed the command slightly to include the port range specified, as well as the `-sV` argument to get the verbose results back.

```bash 
bandit16@bandit:~$ nmap -p 31000-32000 -sV localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-10-09 15:04 UTC
Stats: 0:02:10 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 80.00% done; ETC: 15:06 (0:00:33 remaining)
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00088s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.94SVN%T=SSL%I=7%D=10/9%Time=68E7CEF8%P=x86_64-pc-linu
SF:x-gnu%r(GenericLines,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x2
SF:0current\x20password\.\n")%r(GetRequest,32,"Wrong!\x20Please\x20enter\x
SF:20the\x20correct\x20current\x20password\.\n")%r(HTTPOptions,32,"Wrong!\
SF:x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n")%r(RTS
SF:PRequest,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20
SF:password\.\n")%r(Help,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x
SF:20current\x20password\.\n")%r(FourOhFourRequest,32,"Wrong!\x20Please\x2
SF:0enter\x20the\x20correct\x20current\x20password\.\n")%r(LPDString,32,"W
SF:rong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\.\n")
SF:%r(SIPOptions,32,"Wrong!\x20Please\x20enter\x20the\x20correct\x20curren
SF:t\x20password\.\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 135.98 seconds
bandit16@bandit:~$ 

```
- Based on the results, I figured out that it was port 31790 which was offering the correct service. So I first tried connecting to it using `openssl s_client localhost:31790` and offering the password. This gave me the following result 

```bash 
bandit16@bandit:~$ openssl s_client localhost:31790 
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 55CFF799F0294615FD1D912046CE5AA52469EB6D4B40537C901CED93D69A0555
    Session-ID-ctx: 
    Resumption PSK: 7FE389FD25A77BF78114B550E67327C315F0BD8EA52FDBF5E3D542716D6A7BBF9EEA8E4A1245A75F32596B14BE76FFF6
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 12 78 e0 37 ae 6b ed b8-1d 6f 2d 8d 8b 96 63 cc   .x.7.k...o-...c.
    0010 - 46 fe ff 79 2b 32 8b c2-3b 14 7f 9d 64 5e 6a 45   F..y+2..;...d^jE
    0020 - cc c1 1b 5a 47 62 20 36-ff 8a ec 88 f9 ce 2f f0   ...ZGb 6....../.
    0030 - 4a ad e7 b6 04 78 70 cd-09 6a 3a 3d 64 24 40 83   J....xp..j:=d$@.
    0040 - a4 0f 09 54 cc 4c 39 ba-9e 75 4a 70 4b 86 ea 24   ...T.L9..uJpK..$
    0050 - 50 e8 e4 95 5b ef 0b 56-e1 6b 40 57 76 60 8c c3   P...[..V.k@Wv`..
    0060 - f1 8a db 03 c1 3d 3f 7a-5a 33 b6 3b 3f 43 46 e5   .....=?zZ3.;?CF.
    0070 - 55 11 0b c8 cb 12 05 db-cc d1 89 b4 20 e9 17 c0   U........... ...
    0080 - f0 1e 32 84 c1 da 70 39-ea 4d b0 6f e1 c9 41 cc   ..2...p9.M.o..A.
    0090 - 57 5e 51 d4 91 1f 8d 35-aa ec 72 50 4f a9 fe 5b   W^Q....5..rPO..[
    00a0 - 8d 4c e3 01 73 a3 25 52-fc fb c7 ba b3 39 b6 a0   .L..s.%R.....9..
    00b0 - 64 25 cc 1c 16 67 0b a2-fb d1 2d 35 16 00 f4 a3   d%...g....-5....
    00c0 - a4 cc 23 11 f2 db 5e ae-fc d2 32 6e db a7 72 a2   ..#...^...2n..r.
    00d0 - 91 7a c9 72 6c c1 c0 30-f9 61 f9 0a ec d6 bc c7   .z.rl..0.a......

    Start Time: 1760022523
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 2CD3B2E6F39F8AB60CA9C4DC13CBA999408894ABD6995600ED1B9690B1841139
    Session-ID-ctx: 
    Resumption PSK: 49B11AEF2CA57694AF70EA5A2B19F63184E2989017F9338DEC4082A9976B489DDF94710CA11EF6B90674D5BD466449FF
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 12 78 e0 37 ae 6b ed b8-1d 6f 2d 8d 8b 96 63 cc   .x.7.k...o-...c.
    0010 - 6e 02 63 c4 9f 46 33 a6-b8 14 81 98 6a 11 ce 63   n.c..F3.....j..c
    0020 - 5d 08 59 5c 6c af d5 44-4c ca 3a e6 52 3e 73 7a   ].Y\l..DL.:.R>sz
    0030 - 91 f1 17 4a 7b ac 17 81-ad 4e 7a 6f 9f 56 cb 2e   ...J{....Nzo.V..
    0040 - f7 5f f4 29 ed be 38 9f-38 2d 0d 14 ed 34 c7 51   ._.)..8.8-...4.Q
    0050 - 7f e0 9e ae 82 fe 4e cc-2d 48 aa cb a3 0b 15 f1   ......N.-H......
    0060 - 7f a0 2f 34 7a 12 54 ea-ea 44 e7 38 48 c4 28 f7   ../4z.T..D.8H.(.
    0070 - 21 03 d8 29 06 9c 53 a6-ce 3f a2 29 1b a1 b3 93   !..)..S..?.)....
    0080 - 07 67 63 7c d9 60 7a da-58 d4 e7 9d da a2 2f 97   .gc|.`z.X...../.
    0090 - bb 40 6a d6 22 7c bb 10-ec 14 48 92 8c 65 6d fc   .@j."|....H..em.
    00a0 - 43 8b 99 72 26 82 4d 6f-c0 aa b3 2e 11 60 2a c2   C..r&.Mo.....`*.
    00b0 - fd a3 32 54 fe b4 fb 44-0b 6a f6 ec f1 5d 06 75   ..2T...D.j...].u
    00c0 - 8a 0b 5f 1f f8 b3 8b 77-a2 57 c8 5e 7b 01 7c 33   .._....w.W.^{.|3
    00d0 - 24 1b 40 ad af 8c 1f ee-4d 35 31 09 43 a8 bd 15   $.@.....M51.C...

    Start Time: 1760022523
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
KEYUPDATE
^Z
[1]+  Stopped                 openssl s_client localhost:31790
bandit16@bandit:~$ 

```
- I discussed this with my mentor and he told me to use `-connect` argument as well to ensure I can connect properly. I then spent the next half an hour understanding why this happened the way this happened. So I read up the manpage of `openssl-s_client`(specifically the connected Commands section as given in challenge statement) to understand it. 

```bash 
bandit16@bandit:~$ man openssl-s_client
.
.
.
CONNECTED COMMANDS
       If a connection is established with an SSL server then any data received from the server is displayed and  any  key  presses
       will  be  sent  to  the  server.  If end of file is reached then the connection will be closed down. When used interactively
       (which means neither -quiet nor -ign_eof have been given), then certain commands are also recognized which  perform  special
       operations. These commands are a letter which must appear at the start of a line. They are listed below.

       Q   End the current SSL connection and exit.

       R   Renegotiate the SSL session (TLSv1.2 and below only).

       k   Send a key update message to the server (TLSv1.3 only)

       K   Send a key update message to the server and request one back (TLSv1.3 only)
.
.
.
bandit16@bandit:~$ 

```
- The above result is what made me realize why I was getting this error. The key of level 16 starts with a letter `k`. This letter `k` is used to send a key update message to the server. I did not really understand what it means by this, but I'm happy atleast I figured out why it is happening. The solution is also given in this part of the manpage, where we add `-quiet` to our argument to get the result. 

```bash 

bandit16@bandit:~$ openssl s_client -quiet -connect localhost:31790 
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:~$ 

```
- The above result is a RSA key while I was expecting a simple password, as such I got annoyed, closed my laptop and got to it again the next day. On getting this key, I took the help of AI to understand how we can use this key to login to the next level. 
- I learned that we can save this key in the `/tmp` directory, give it permissions so that only the owner can read it, and then use it to connect to the next level using `ssh`. I did this using the steps as below 
- I first copied the flag of level 16 into a file `curPass.txt` using echo command as show below

```bash 
bandit16@bandit:/tmp$ echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx > curPass.txt
bandit16@bandit:/tmp$ cat curPass.txt
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
bandit16@bandit:/tmp$ 
```
- I did this because I needed to send this as an input to the `openssl s_client` command and get the resultant RSA key stored in a `.txt` file. 

```bash 
bandit16@bandit:/tmp$ cat curPass.txt | openssl s_client -quiet -connect localhost:31790 > /tmp/bandit17.key
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
bandit16@bandit:/tmp$ cat /tmp/bandit17.key
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:/tmp$ 

```

- This allowed me to save the RSA key in a file, I then changed the permissions of the key to allow it to be readable/writeable only by the owner. This is necessary when using the key with `ssh`. From this I also learned about the numeric value for read, write, executable permissions, i.e., 4 for read, 2 for write, 1 for executable. 

```bash 
bandit16@bandit:/tmp$ chmod 600 bandit17.key
bandit16@bandit:/tmp$ ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit16/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.

backend: gibson-1

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit17@bandit:~$ 

```
- This allowed me to successfully connect to the next level and then I used the `cat` command to find the password for this flag as all passwords are stored in `/etc/bandit_pass` 

```bash 
bandit17@bandit:~$ cat /etc/bandit_pass/bandit17 
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
bandit17@bandit:~$ 

```

## What I learned 
This was one of the longest challenges I have done so far and it turned out to be very frustrating (almost convinced me that cybersec is not for me ;-;). However, with patience and time I was able to learn a lot from this challenge and solve it. The first thing that I learned from this challenge was that `openssl s_client` command has command sections where certain keys are mapped and they cause certain changes to occur on the server, so I learned how to navigate that. The second thing I learned from this challenge was that a server may not always return a password but return a key type which we need to know how to use. The third thing I learned from this challenge is that I can use numeric values along with `chmod` to change the permissions in one go without having to worry about using alphabets. 

## References 
- https://overthewire.org/wargames/bandit/bandit17.html
- https://gemini.google.com/app/3ebbdd30583b4d57
- Manpages of `nmap`, `openssl-s_client` and `chmod`
---------------------------------------------------------------------------------------------------------------------------------
## Level 17 -> Level 18 
In this challenge, we simply need to compare two text files and find the differences so that we can find the new password. 

## My solve 

**Flag:** `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO` 

To solve this challenge, I followed the steps as listed below: 
- This was a pretty simple challenge, where we first connected to `bandit17` using `ssh` command. 
- Then I listed out the files present in the home directory. 
- Using the `diff` command to compare the two outputs, I gained info that the new password was at the 42nd line of `passwords.new` file

```bash 
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< CgmS55GVlEKTgx8xpW8HuWnHlBKP924b
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
bandit17@bandit:~$ 
```

## What I learned 
This challenge was more of a practice for the `diff` command than an actual challenge, and hence I solved this in two mins. 

## References
- https://overthewire.org/wargames/bandit/bandit18.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 18 -> Level 19 
In this challenge, we need to learn how to execute a command on the bandit18 level without every opening an interactive shell session. 

## My solve

**Flag:** `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

To solve this I followed the steps as listed below: 
- I first tried running the command `ssh bandit18@bandit.labs.overthewire.org -p 2220; cat readme`. This however gave an error to me, and I realised that `cat readme` was trying to read a `readme` file on my computer, not on `bandit.labs.overthewire.org`. 
- I had no clue about this challenge, so I put this challenge into AI and I learned that we can execute commands on the target machine without needing to open an interactive shell session. 
- This allowed me to get the flag. 

```bash 
21:16:14 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/crypto/writeups/extraWork  → ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat readme';
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit18@bandit.labs.overthewire.org's password: 
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
21:18:15 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/crypto/writeups/extraWork  → 

```

## What I learned
From this challenge, I learned that we can execute commands remotely on a system without needing to start an interactive shell session. I think it can be very useful when logging in discreetly to other machines, but I am not sure about it. Cool thing to learn anyways

## References
- https://overthewire.org/wargames/bandit/bandit19.html
- https://gemini.google.com/app/efd256b734a87cae
---------------------------------------------------------------------------------------------------------------------------------
## Level 19 -> Level 20 
In this challenge, we need to find the password of the next level using a setuid without invoking `setuid` command. 

## My solve 

**Flag:** `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`


To solve this challenge, I followed the steps as listed below: 
- I first listed out all the programs present in the home directory by using the `ls` command.
- This gave me a program called as `bandit20-do`. I invoked this program and found an example usage. This told me how to use this program. Thus using it with `cat` command, we get the password. 

```bash 
bandit19@bandit:~$ ls 
bandit20-do
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
bandit19@bandit:~$ 

```

## What I learned 
From this challenge, I learned that we can create programs that can manipulate the uid bit to set it so that we can open a file or run a program as the owner. 

## References
- https://overthewire.org/wargames/bandit/bandit20.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 20 -> Level 21 
In this challenge, we need to figure out to ensure that the program sends the password correctly when needed to ensure that we can get the correct flag transmitted back.


## My solve 


**Flag:** `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

To solve this challenge, I followed the steps as listed below: 
- I first read the challenge and the listed commands to figure out how we can solve this challenge. Reading up, I understood that we would need to have a `tmux` session running in the background which is sending out the correct password of level 20 to any program which tries to connect. The issue I faced here is that I was totally unaware what command could be used to solve this. 
- I took slight help from AI here, where I asked what command could be used to set up a listening service and I learned about the `-l` argument, which stands for listening, in `nc` command. Reading the manpage of `nc` I understood how to use it. 
- Thus to create a `tmux` session which will `echo` the correct password, I did it as below

```bash
bandit20@bandit:~$ man nc
bandit20@bandit:/tmp$ nc -l -p 31330 < /etc/bandit_pass/bandit20 > bandit20.txt


```
- This is the command in a `tmux` session. Detaching it using control code `Ctrl-B` and then `D`. I came back to my original shell. 
- Running the `./suconnect 31300` command in the shell, I got the following output

```bash 
bandit20@bandit:~$ ./suconnect 31330
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
bandit20@bandit:~$
```

- Attaching the `tmux` session back using `tmux attach` command, and then running `cat bandit20.txt`, we find the password.

```bash 
bandit20@bandit:/tmp$ cat bandit20.txt
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
bandit20@bandit:/tmp$
```

## What I learned 
From this challenge, I learned that we can also use `nc` command to set up listeners, which allows us to send data as and when needed to whoever is connecting to us. This can be useful when we need to share data and files with others

## References 
- https://overthewire.org/wargames/bandit/bandit21.html
- https://gemini.google.com/app/7eb68f241e732965
---------------------------------------------------------------------------------------------------------------------------------
## Level 21 -> Level 22
In this challenge, we need to figure out the process which is running at regular time intervals to get the password. 

## My solve 

**Flag:** `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q` 

To solve this challenge, I followed the steps as listed below: 
- I first read the challenge, and looked up manpages of the commands given to us. This taught me that `cron` is a type of a `daemon`. The `daemons` was a new term for me and hence I googled it to understand what it means. According to my understanding, `daemons` are basically background processes that run without interaction with the primary user. 
- I first ran `ls /etc/cron.d` command as this was the directory we were told to look in. Listing out the contents, I found a file called `cronjob_bandit22`. Since there was not any `cronjob_bandit21` I decided to cat the previous file and got a unique result which I had not seen so far. 

```bash 
bandit21@bandit:~$ ls -l /etc/cron.d
total 40
-r--r----- 1 root root  47 Aug 15 13:16 behemoth4_cleanup
-rw-r--r-- 1 root root 123 Aug 15 13:09 clean_tmp
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit22
-rw-r--r-- 1 root root 122 Aug 15 13:16 cronjob_bandit23
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit24
-rw-r--r-- 1 root root 201 Apr  8  2024 e2scrub_all
-r--r----- 1 root root  48 Aug 15 13:17 leviathan5_cleanup
-rw------- 1 root root 138 Aug 15 13:17 manpage3_resetpw_job
-rwx------ 1 root root  52 Aug 15 13:19 otw-tmp-dir
-rw-r--r-- 1 root root 396 Jan  9  2024 sysstat
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$
```

- Googling to understand what this result meant, I understood that this is a format where the first column specifies time, the second column specifies what user the process is being executed as, the third column gives the path of the script that needs to be run, and the `&> /dev/null` tells the `cron daemon` to throw away all the stdout and stderr msgs. 
- Following the path of the script, and using `cat` command to find what is written in the script. 

```bash 
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:~$
```

- Reading the above script, I realized that the password of the level `/etc/bandit_pass/bandit22` is being sent to a file in `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`. 
- Using `cat` command on the specified file, I got the password for the next level. 

```bash 
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
bandit21@bandit:~$
```

## What I learned 
From this challenge, I learned about what are `daemons` and that `cron` is a type of a `daemon`. `cron` is basically a utility that is analogous to a watchman, i.e., it is always checking that whether a job is supposed to be running right now or not. `cronjobs` are the processes that need to be running and they specify what time the processes need to be running as well. These `cronjobs` are configurations file that tell the `cron daemon` what script to be run, as what user to be run and what time to run the script. The `cronjob_bandit22.sh` is the script which needs to be run to finish/do certain processes. 

## References
- https://overthewire.org/wargames/bandit/bandit22.html
- https://en.wikipedia.org/wiki/Daemon_(computing)
- https://gemini.google.com/app/b3dc56be250d7a26
---------------------------------------------------------------------------------------------------------------------------------
## Level 22 -> Level 23 
To solve this challenge, we again have to figure out what `cronjob` is running what script and how we can use it to solve the challenge. 

## My solve 

**Flag:** `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga` 

To solve this challenge, I followed the steps as given below 
- I first listed out the contents of the `/etc/cron.d` directory. Proceeding as done in the previous challenge, I used `cat` command on `/etc/cron.d/cronjob_bandit23` to figure out the path of the script. 
- On finding the path, I used the `cat` command again to get the contents of the script. 

```bash 
bandit22@bandit:~$ ls -l /etc/cron.d
total 40
-r--r----- 1 root root  47 Aug 15 13:16 behemoth4_cleanup
-rw-r--r-- 1 root root 123 Aug 15 13:09 clean_tmp
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit22
-rw-r--r-- 1 root root 122 Aug 15 13:16 cronjob_bandit23
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit24
-rw-r--r-- 1 root root 201 Apr  8  2024 e2scrub_all
-r--r----- 1 root root  48 Aug 15 13:17 leviathan5_cleanup
-rw------- 1 root root 138 Aug 15 13:17 manpage3_resetpw_job
-rwx------ 1 root root  52 Aug 15 13:19 otw-tmp-dir
-rw-r--r-- 1 root root 396 Jan  9  2024 sysstat
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$

```
- On reading the script, I understood that the password would be saved in a file name `/tmp/$mytarget` where `mytarget` is the variable that we need to find out, I first tried using the variable directly only to hit a roadblock. 

```bash 
bandit22@bandit:~$ cat /tmp/$mytarget
cat: /tmp/: Permission denied
bandit22@bandit:~$
```
- I then realized that I can calculate the value of the `mytarget` variable as I knew how it works. Using this, I copied the exact same command, and replaced `$myname` with the actual username that we needed to find, i.e., `bandit23` (since `myname` variable is also used in `cat` command to store the password)
- Using this knowledge, I got the result as the name of the `/tmp` file which had stored the password. 

```bash 
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
bandit22@bandit:~$
```
- Using `cat` on this file gave me the password.

## What I learned 
This challenge was a good test of all the skills I had learned so far as this tested multiple aspects of Linux systems. It served as a good revision. 

## References 
- https://overthewire.org/wargames/bandit/bandit23.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 23 -> Level 24 
In this challenge, we need to figure out a way to run a script so that we can get the password. 

## My solve 


**Flag:** `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8` 

To solve this challenge, I followed the steps as listed below:
- I first ran the `ls` command to find out the configuration file that we needed. Following the same logic as the previous two questions, I learned what user the script was running it. I actually learned it by some trial and error where I first tried to run my script first as `bandit23`. 
- I then used `cat` command on the script path to figure out what was happening in the system. 

```bash 
bandit23@bandit:~$ ls -l /etc/cron.d
total 40
-r--r----- 1 root root  47 Aug 15 13:16 behemoth4_cleanup
-rw-r--r-- 1 root root 123 Aug 15 13:09 clean_tmp
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit22
-rw-r--r-- 1 root root 122 Aug 15 13:16 cronjob_bandit23
-rw-r--r-- 1 root root 120 Aug 15 13:16 cronjob_bandit24
-rw-r--r-- 1 root root 201 Apr  8  2024 e2scrub_all
-r--r----- 1 root root  48 Aug 15 13:17 leviathan5_cleanup
-rw------- 1 root root 138 Aug 15 13:17 manpage3_resetpw_job
-rwx------ 1 root root  52 Aug 15 13:19 otw-tmp-dir
-rw-r--r-- 1 root root 396 Jan  9  2024 sysstat
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh 
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done

bandit23@bandit:~$ 

```
- Now after reading this script, I got a bit confused as I was not aware what `/var/spool/bandit24/foo` directory was, so I took the help of AI agents to understand what that directory is. From this I learned that `/var/spool` directory is basically the standard directory for holding scripts. Spooling term is used to refer holding data or a job until a system or program is ready to process them. 
- The AI also gave me the hint that I needed to place my password stealing script in this directory to get the password. 
- Proceeding according to these instruction, I got the following results

```bash 
bandit23@bandit:~$ cd /tmp 
bandit23@bandit:/tmp$ nano bandit24Pass.sh 
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp$ cat bandit24Pass.sh
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass.txt
bandit23@bandit:/tmp$ cp bandit24Pass.sh /var/spool/bandit24/foo 
bandit23@bandit:/tmp$ 

```
- I then had to wait a minute as the scripts would get executed each minute. However, my script in `/var/spool/bandit24/foo` directory would also get deleted as the script `cronjob_bandit24.sh` would ensure any script with owner as `bandit23` is removed. 
- using `cat` on `/tmp/bandit24_pass.txt`, I got the flag

```bash 
bandit23@bandit:/tmp$ cat /tmp/bandit24_pass.txt
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
bandit23@bandit:/tmp$ 

```

## What I learned 
From this challenge, I learned about the existence of the standard Unix directory used for spooling data. Creating the script was a revision for me, but figuring out where to place this script was something entirely new for me. 

## References 
- https://overthewire.org/wargames/bandit/bandit24.html
- https://gemini.google.com/app/8a1b9baff107b456
---------------------------------------------------------------------------------------------------------------------------------
## Level 24 -> Level 25 
In this challenge, we need to find the correct pincode so we can login to the service and get the password. 


**Flag:** `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4` 
---------------------------------------------------------------------------------------------------------------------------------
## Level 25 -> Level 26 
In this challenge, we first had to login to bandit26 level, figure out how to use the `vim` editor, then escape that program. 


## My solve 

**Flag:** `RSA key login` / `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ` (found after logging in to bandit26)

To solve this challenge, I followed the steps as listed below: 

- I first used the `ls` command to find the contents of the home directory. This gave the RSA login key. Copying this key into a file on my system and using it to login to the next level, I got stuck, as it returned me back to my own shell. 
- I then took the help of AI and realized that this is a program which writes out the text of a file using `more` command. Reading the manpage of this command, I learned that this command presents the data so that it can fit our screen. So minimizing the screen could stop us from escaping the connection immediately. 
- Hence I tried using a smaller window size and it worked. Inside the window, using `v` to enter the vim editor, and then using `:set shell=/bin/bash` we were able to change the default shell that we were using. To escape the editor, simply using the `:sh` command was enough. 
- This allowed us to exit the editor and open a bash shell on the challenge. 
- Using `cat /etc/bandit_pass/bandit26`, we got the password. 

```bash 
21:11:26 ishaan-mishra@ishaan-mish21:11:26 ishaan-mishra@ishaan-mishra-Lenovo-G505s /tmp  → ssh -i bandit26rsakey bandit26@bandit.labs.overthewire.org -p 2220 
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
:sh
[No write since last change]
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
bandit26@bandit:~$ 
```

## What I learned 
From this challenge, I learned about the VIM Editor and how we can use it to directly execute commands. This is useful for various types of instances where we get stuck as shown in challenge. 

## References 
- https://overthewire.org/wargames/bandit/bandit26.html
- https://gemini.google.com/app/d709feb1dbc42fd2
---------------------------------------------------------------------------------------------------------------------------------
## Level 26 -> Level 27 
To solve this challenge, we simply had to use the `bandit27-do` file present in level `bandit26` to get the password. 


## My solve 

To solve this challenge, I followed the steps as listed below: 
- I followed the same steps as previous challenge to login and get a shell working on `bandit26`. Once in the home directory, I used the `ls` command to find the basic files. In that, I found a `bandit27-do` file. Using that file along with `cat`, I got the password for `bandit27`

```bash
.
.
.~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
~                                                                                                                                      
:sh
[No write since last change]
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
bandit26@bandit:~$ 

```

## What I learned
This challenge was simply a revision of the previous challenges. 

## References 
- https://overthewire.org/wargames/bandit/bandit27.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 27 -> Level 28 
To solve this level, we just had to clone the directory and get the password from the `repo` directory. 

## My solve 

**Flag:** `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN` 

To solve this challenge, I followed the steps as below: 
- I first read the manpage of `git` command to understand how we can clone a repository. 

```bash 
. 
. 
.

       git-clone(1)
           Clone a repository into a new directory.

.
.
.
```

- Using the above command, I tried crafting a command, but it failed because I simply copied the path from the question without changing the `localhost` to `bandit.labs.overthewire.org`. I added the port value by simply following the same syntax of a website. 

```bash 
21:43:14 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~  → git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo 
Cloning into 'repo'...
ssh: connect to host localhost port 2220: Connection refused
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
21:45:10 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~
```

- Realizing my stupidity, I changed the required criteria and was able to clone into the `repo` and get the password. 

```bash 
21:45:57 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~  → git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo 
Cloning into 'repo'...
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit27-git@bandit.labs.overthewire.org's password: 
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
21:46:49 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~  → cd repo
21:46:55 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → ls
README
21:46:56 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → cat README
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
21:47:00 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master)

```

## What I learned 
From this challenge, I learned how we can clone a repository from git. 

## References 
- https://overthewire.org/wargames/bandit/bandit28.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 28 -> Level 29 
To solve this challenge, you need to find the password hidden in the log history of the repository. 

## My solve 

**Flag:** `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7` 

To solve this challenge, I followed the steps as shown below:
- I first cloned the repo following the steps as the previous challenge, and then spent half an hour going through each directory and file present in the repo to check if the flag was there (it was painful)
- Then I realized that the password could also be hidden in the commits of the repo (thanks to a certain challenge in the Citadel). Using that thought process, I looked up the logs of the repo using `git log` command to get the result shown: 

```bash 
22:01:30 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git log 
commit 710c14a2e43cfd97041924403e00efb00b3a956e (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    fix info leak

commit 68314e012fbaa192abfc9b78ac369c82b75fab8f
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    add missing data

commit a158f9a82c29a16dcea474458a5ccf692a385cd4
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    initial commit of README.md
22:01:35 ishaan-mishra@ishaan-mishra-Lenovo-G505s
```
- From this, I checked the info leak commit using `git show` command. This gave me the password. 

```bash 
22:02:09 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git show 710c14a2e43cfd97041924403e00efb00b3a956e
commit 710c14a2e43cfd97041924403e00efb00b3a956e (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx
 
22:06:01 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → 

```

## What I learned
From this challenge, I learned how we can check the logs of any repository to understand what happened, and how we can also view those logs. 

## References
- manpage of `git`
- https://overthewire.org/wargames/bandit/bandit29.html
---------------------------------------------------------------------------------------------------------------------------------
## Level 29 -> Level 30 
To solve this challenge, you need to change to a different branch from main and find the password in `README.md` in the new branch. 


## My solve 
To solve this challenge, I followed the steps as listed below: 
- I first cloned the repo using the steps as above, I then used the `cat` command to get the contents of `README.md` of the main branch. 

```bash 
22:09:18 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

22:09:23 ishaan-mishra@ishaan-mishra-Lenovo-G505s

```

- I knew a bit about *production* but not enough, so I took the help of AI to understand what production is and where can we find the next password. 
- After understanding about production, I used the `git branch -a` command to see all the branches available. Then changing my branch from main to `remotes/origin/dev` I found the password. 

```bash 
22:09:57 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git branch -a 
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
22:11:04 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git checkout remotes/origin/dev
Note: switching to 'remotes/origin/dev'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at d9fa2d0 add data needed for development
22:11:17 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (HEAD) → ls
code  README.md
22:11:26 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (HEAD) → cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

22:11:32 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo

```

## What I learned 
From this challenge, I learned that *production* is used to refer to the main, stable code that is facing the public. I also learned about how we can see other branches and how to switch into them. 

## References
- https://overthewire.org/wargames/bandit/bandit30.html
- https://gemini.google.com/app/f8225c2d10f8c9b9
---------------------------------------------------------------------------------------------------------------------------------
## Level 30 -> Level 31 
To solve this challenge, we need to find the password hidden amongst tags of the repo. 


## My solve 
To solve this challenge, I followed the steps as below: 
- I first cloned the repo as needed, and used `cd` to go into it. 
- Since I had zero clue, I asked AI to check the question and I learned that I have to use the `git tag` command to find the password. 
- Using the command as told, I found a tag `secret`. Using `git show` on this, I got the flag. 

```bash 
22:19:37 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → cat README.md
just an epmty file... muahaha
22:22:49 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git branch
* master
22:22:56 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git tag
secret
22:23:00 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
22:23:06 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → 

```

## What I learned 
From this challenge, I learned that something known as tags exist for a repository. 

## References 
- overthewire.org/wargames/bandit/bandit30.html
- https://gemini.google.com/app/f8225c2d10f8c9b9
---------------------------------------------------------------------------------------------------------------------------------
## Level 31 -> Level 32
To solve this challenge, we needed to `push` a file to the repo. 

## My solve 

**Flag:** `3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`

To solve this challenge, I followed the steps as listed below: 
- I had no clue about this challenge, apart from cloning the repo, so I asked AI to help me solve this. 
- Using the hints AI gave me, I used `git add`, `git commit` and finally `git push` after creating the file as needed. The hint for file creation was give in `README.md` 
```bash 
22:36:20 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

22:40:49 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → echo 'May I come in?' > key.txt
22:41:14 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → rm .gitignore
22:35:35 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git add 
Nothing specified, nothing added.
hint: Maybe you wanted to say 'git add .'?
hint: Turn this message off by running
hint: "git config advice.addEmptyPathspec false"
22:35:42 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git add key.txt 
22:35:49 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git commit -m "As per ques"
[master 201e758] As per ques
 2 files changed, 1 insertion(+), 1 deletion(-)
 delete mode 100644 .gitignore
 create mode 100644 key.txt
22:36:01 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → git push 
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit31-git@bandit.labs.overthewire.org's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 295 bytes | 295.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo'
22:36:20 ishaan-mishra@ishaan-mishra-Lenovo-G505s ~/repo (master) → 

```

## What I learned 
From this challenge, I learned how we can add and remove file from a repository and the order of the commands to be followed while doing so. 

## References
- https://overthewire.org/wargames/bandit/bandit32.html
- https://gemini.google.com/app/336bb34db2ab0c12
---------------------------------------------------------------------------------------------------------------------------------
## Level 32 -> Level 33 
To solve this challenge, we need to escape an uppercase jail. 

## My solve 

**Flag:** `tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0` 

To solve this challenge, I followed the steps as below: 
- Seeing that this was another jail, and because it mentioned that it was an uppercase shell, I first typed out the `ls` command to see how it works. 

```bash 
>> ls
sh: 1: LS: Permission denied
>> 

```
- From the stderr output, I was able to figure out that all my commands are getting converted to uppercase before being executed. Therefore to switch to a shell, or to escape this program, I first typed out `$shell` to get it to execute the path in shell variable.

```bash 
>> $shell 
WELCOME TO THE UPPERCASE SHELL
>> 
```

- I got this output, but it did not seem very useful, so I typed out `$0` to revert to whatever shell is being used. This allowed me to escape the jail.
- From that, it was a cakewalk to get the password. 

```bash 
>> $0
$ whoami 
bandit33
$ cat /etc/bandit_pass/bandit33 
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0

```

## What I learned 
Because of `$shell` not working, I googled and tried to understand the difference between `$shell` and `$0`. I learned that `$0` is dynamic and holds the path of the current shell where as `$shell` holds the default shell. 
---------------------------------------------------------------------------------------------------------------------------------


