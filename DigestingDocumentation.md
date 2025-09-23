# Digest Documentation 

## Challenge 1: Learning from Documentation 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation Module,* we are taught the basics about documentation and need to call a command with the correct argument, provided in the challenge documentation, to get the flag. 

## My Solve

**Flag:** `pwn.college{Q02-r1ELkF4tpFlPJd6rvovz8hU.QX0ITO0wSO3gjNzEzW}`

To solve this challenge, I followed the instructions as given in the challenge statement and used the `/challenge/challenge` command along with `--giveflag` argument to get the flag. 

```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{Q02-r1ELkF4tpFlPJd6rvovz8hU.QX0ITO0wSO3gjNzEzW}
hacker@man~learning-from-documentation:~$ 
```

## What I learned 

From this challenge, I learned that we can access a manual page/documentation page for each command to understand what arguments a particular command can take. 

## References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Learning Complex Usage 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation module,* we are made aware about complex usage of arguments of a command, where we need to run a command in which the argument itself takes another argument. 

## My Solve: 

**Flag:** `pwn.college{QBxLKqEly_Ab5e0Spm8S76D6DpX.QX1ITO0wSO3gjNzEzW}`

To solve the above challenge, I first ran the command to get the documentation for a hint. However, seeing that it gave no useful hint, I snooped around and listed the contents of various other directories to find the flag. After finding the flag, I ran the command along with the argument and sub-argument to get the flag. 

```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](/linux-luminarium/commands).
`find` has a `-name` argument, and the `-name` argument itself takes an argument specifying the name to search for.
Many other commands are analogous.

Here is this level's documentation for `/challenge/challenge`:

> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the description of the level!

Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ ls /challenge
DESCRIPTION.md  challenge
hacker@man~learning-complex-usage:~$ ls /challenge/challenge
/challenge/challenge
hacker@man~learning-complex-usage:~$ ls /
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag 
Correct argument! Here is the /flag file:
pwn.college{QBxLKqEly_Ab5e0Spm8S76D6DpX.QX1ITO0wSO3gjNzEzW}
hacker@man~learning-complex-usage:~$ 
```

## What I learned 
I learned that even an argument of a command can take a sub-argument to enhance the functioning of a command that we are using. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Reading Manuals 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation module,* we are introduced to **Manual** pages or man pages. To solve this challenge, we need to read the man page of a command and then use it to get the flag. 

## My Solve: 

**Flag:** `pwn.college{wCOrzqpcwzNQ8uBHZUMbUDv2-rJ.QX0EDO0wSO3gjNzEzW}`

To solve this challenge, I used the `man` command to open the manual page for `challenge` and read the manual page. On opening the manual page, I read through the description and figured out that `--wrzqpc` argument when used with a specific sub-argument(820 in this case), would print out the flag. Hence creating a command with the correct arguments and sub-arguments, I got the flag.

```
hacker@man~reading-manuals:~$ man challenge
CHALLENGE(1)                                             Challenge Commands                                            CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --wrzqpc NUM
              print the flag if NUM is 820

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                   May 2024                                                 CHALLENGE(1)
 Manual page challenge(1) line 1/31 (END) (press h for help or q to quit)
hacker@man~reading-manuals:~$ /challenge/challenge --wrzqpc 820
Correct usage! Your flag: pwn.college{wCOrzqpcwzNQ8uBHZUMbUDv2-rJ.QX0EDO0wSO3gjNzEzW}
hacker@man~reading-manuals:~
```

## What I learned 
From this challenge, I learned that manuals exist for some commands and that these live on our computer in the `/usr/bin` directory. We do not need to directly go and access them, instead we use the `man` command to get the manual page of a particular command. These manual pages contain a lot of information in depth and thus, are very helpful for us. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Searching Manuals 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation module,* we need to learn how to navigate a man page to find the correct argument for a command. Usage of this command will give us the flag. 

## My Solve

**Flag:** `pwn.college{4RfIF7X7t1h2FUEjPAVhkW2SAFT.QX1EDO0wSO3gjNzEzW}`

To solve the above problem, I followed the steps as given below: 
- I read the man page of the `challenge` command using the `man` command 
```
hacker@man~searching-manuals:~$ man challenge
CHALLENGE(1)                                              Challenge Commands                                              CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right argument.

       --fortune
              read a fortune

       --version
              output version information and exit

       --nsh  A neat argument, but not the right one.

       --yptwqf
              A neat argument, but not the right one.

       --thjmda
              A neat argument, but not the right one.

       --mpj  A neat argument, but not the right one.

       --ftyd A neat argument, but not the right one.

       --wxz  A neat argument, but not the right one.

       -z     A neat argument, but not the right one.
.
.
.
.
.
.
.
       --mgiyh
              A neat argument, but not the right one.

       --wz   A neat argument, but not the right one.

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                    May 2024                                                   CHALLENGE(1)
```
- After opening the man page, I typed `/` on my keyboard to open the search bar. In the search bar I typed out "flag", because I felt that the description of the right argument would contain "flag" keyword.
- On executing the `/flag` in the man page and navigating to other finds by using `n` as mentioned in challenge, I found the right flag. 
```
.
.
       --jesyz
              A neat argument, but not the right one.

       --tzs  This argument will give you the flag!

       --sw   A neat argument, but not the right one.
.
.
.
```
- After finding the flag, I quit the man page by typing `q`. 
- I then ran the command with the argument to get the flag. 
```
hacker@man~searching-manuals:~$ /challenge/challenge --tzs
Initializing...
Correct usage! Your flag: pwn.college{4RfIF7X7t1h2FUEjPAVhkW2SAFT.QX1EDO0wSO3gjNzEzW}
hacker@man~searching-manuals:~$
```

## What I learned 
From this challenge, I learned that we can use the `/` inside man pages to find relevant arguments, descriptions etc quickly, especially when man pages are very long. This will help in saving a lot of time and effort. 

## References
- Material given in challenge 
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Searching for manuals
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation module,* we need to first find the manual page for the command which we need to run, then read the manual page of the command and then finally use the command correctly to get the flag. 

## My Solve

**Flag:** `pwn.college{cFqvS8mwpA6e9glHQHGu5Dtzee2.QX2EDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as given below: 
- I first used the `man man` command to access the manual page of the `man` command itself. 
- On reading through the manual page, I found a hint in its **EXAMPLES** section. 
```
       man -k printf
           Search  the  short  descriptions  and  manual  page  names  for the keyword printf as regular expression.  Print out any matches. Equivalent to apropos printf.
```
- I assumed this a possible way of solving because of two reasons, first, it says that the `-k` argument searches descriptions and manual pages, second, `printf` was told a keyword, so I felt that we could replace it with our needed word to get the result. 
- Following this train of thought, I exited the man page and ran the `man -k flag` command, because I knew from previous challenge that "flag" keyword would allow us to get all manual pages which have "flag" anywhere in their names or descriptions. 
```
hacker@man~searching-for-manuals:~$ man -k flag
cqvmwpeglu (1)       - print the flag!
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour o...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behavi...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour ...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
hacker@man~searching-for-manuals:~$
```

- I found the name of the manual page as `cqvmwpeglu`. 
- Running the `man cqvmwpeglu` command to access the man page, I got the following result:


```
CHALLENGE(1)                                             Challenge Commands                                            CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --cqvmwp NUM
              print the flag if NUM is 869

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                   May 2024                                                 CHALLENGE(1)
 Manual page cqvmwpeglu(1) line 1/31 (END) (press h for help or q to quit)
```

- Taking the correct argument and sub-argument from the manual page, I ran the command in the correct format to get the flag. 
```
hacker@man~searching-for-manuals:~$ /challenge/challenge --cqvmwp 869
Correct usage! Your flag: pwn.college{cFqvS8mwpA6e9glHQHGu5Dtzee2.QX2EDO0wSO3gjNzEzW}
hacker@man~searching-for-manuals:~$
```

## What I learned
From this challenge, I learned that manual pages are going to be a great help to me in the future, whether it is for learning about new commands or its for recollecting the old ones. I also learned that the `man -k` command will enable me to find manuals with a specific keyword as well. 

## References:N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Helpful Programs 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation Module,* we are required to find the help regarding a particular command using the `-h` argument. Then we read the help section to get the correct arguments. 

## My solve 

**Flag:** `pwn.college{kQJnRXPKM2CY4hE1tRniXDj6IdH.QX3IDO0wSO3gjNzEzW}`

To solve the above, I first listed out the contents of the `/challenge` directory. Then I used the `-h` argument along with the program to get the help section. I wrongly jumped to a conclusion and instead of reading the whole section, just tried running the program with an incomplete and wrong argument. 

```
hacker@man~helpful-programs:~$ ls /challenge
DESCRIPTION.md  challenge
hacker@man~helpful-programs:~$ /challenge/challenge -h
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -g
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: expected one argument
hacker@man~helpful-programs:~$ /challenge/challenge -g GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge -p 
The secret value is: 241
hacker@man~helpful-programs:~$ /challenge/challenge -g 241
Correct usage! Your flag: pwn.college{kQJnRXPKM2CY4hE1tRniXDj6IdH.QX3IDO0wSO3gjNzEzW}
hacker@man~helpful-programs:~
```

## What I learned 
I learned that it is important to go through the whole help section to avoid making silly mistakes and wasting time. I also learned that there might be commands which do not have manpages and then we should try using `-h` argument to get help for the command. 

## References:N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Help for builtins 
In this challenge of the *Linux Luminarium Dojo, Digesting Documentation module,* we need to get help for a builtin and then proceed from there to get the flag. 

## My Solve

**Flag:** `pwn.college{kjGljIWNt-oXgqpMfCFg-CEsiVl.QX0ETO0wSO3gjNzEzW}`

To solve the above challenge, I simply ran the `help` command with the argument `challenge` to get the help section. Reading through the help section, I found the correct argument and sub-argument to get the flag in the first attempt. 

```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "kjGljIWN".
hacker@man~help-for-builtins:~$ challenge --secret kjGljIWN
Correct! Here is your flag!
pwn.college{kjGljIWNt-oXgqpMfCFg-CEsiVl.QX0ETO0wSO3gjNzEzW}

hacker@man~help-for-builtins:~
```

## What I learned
I learned about the existence of builtins and what they are, along with using help to access the help sections for builtins. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
