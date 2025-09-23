# File Globbing

## Challenge 1: Matching with * 
In this challenge of the *Linux Luminarium Dojo, File Globbing Module,* we need to solve the challenge by changing to a directory using 4 or less characters as an argument. 

## My Solve

**Flag:** `pwn.college{A7n-Gbe646lG2xqaZT1a2Umv2qZ.QXxIDO0wSO3gjNzEzW}`

To solve the above challenge, I read through the challenge material and understood how to solve it, then I simply ran the `cd /ch*` command to change my directory to `/challenge` directory, satisfying the constraints of the problem. Then I ran the `/challenge/run` command to get the flag. 

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{A7n-Gbe646lG2xqaZT1a2Umv2qZ.QXxIDO0wSO3gjNzEzW}
hacker@globbing~matching-with-:/challenge$
```

## What I learned 
I learned about the existence of the `*` wildcard glob. This glob allows for shortening the commands and saving time. 

## References
- https://pwn.college/linux-luminarium/globbing/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Matching with ?
In this challenge of the *Linux Luminarium Dojo, File Globbing Module,* we need to change our directory subject to constraints using the `?` glob. 

## My solve

**Flag:** `pwn.college{wBWKFSnJz-Fw2Skk4fe7JiedSI-.QXyIDO0wSO3gjNzEzW}` 

To solve the above challenge, I simply wrote a command to change my cwd which satisfied all the conditions given in the question. Then I ran the `/ch*/run` command to get the flag. 

```
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /ch*/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{wBWKFSnJz-Fw2Skk4fe7JiedSI-.QXyIDO0wSO3gjNzEzW}
hacker@globbing~matching-with-:/challenge$
```

## What I learned 
I learned the difference between `*` glob and `?` glob. `*` can be used to find any file which meets the name requirements, while `?` glob searches only for similar characters. 

## References
- https://pwn.college/linux-luminarium/globbing/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Matching with []
In this challenge of the *Linux Luminarium Dojo, File Globbing module,* we need to glob multiple files using `[]` glob to get the flag. 

## My solve 

**Flag:** `pwn.college{wH41Ivj5ODP8eIo_CdPxd824Lf5.QXzIDO0wSO3gjNzEzW}`

To solve the above challenge, I followed the steps given below: 
- change directory to intended one 
- tried to run the bracket glob in a wrong manner 
- corrected to pass `file_[]` as argument 
- got the flag 

```bash
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ ls
DESCRIPTION.md  files  run
hacker@globbing~matching-with-:/challenge$ cd ./files
hacker@globbing~matching-with-:/challenge/files$ /ch*/run/file_[abhs]
bash: /ch*/run/file_[abhs]: No such file or directory
hacker@globbing~matching-with-:/challenge/files$ /ch*/run file_[abhs]
You got it! Here is your flag!
pwn.college{wH41Ivj5ODP8eIo_CdPxd824Lf5.QXzIDO0wSO3gjNzEzW}
hacker@globbing~matching-with-:/challenge/files$
```

## What I learned 
In solving this challenge, I learned that I can use the `[]` glob to look for only certain characters in a specific space. This will be useful when I want to look for only certain names in a collection. 

## References
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Matching Paths with [] 
In this challenge of the *Linux Luminarium Dojo, File Globbing module,* we need to specify the correct path using `[]` in the argument of the program to get the flag. 

## My solve 

**Flag:** `pwn.college{wJNz15nsCbxwymJZpMTa6Sc7jtH.QX0IDO0wSO3gjNzEzW} `

To solve the above, I did the following steps: 
- tried running the program with absolute path of the files along with `*` glob to shorten the command. However I was getting some error in that. I analyzed and found I referenced `/files` instead of file so I corrected it and re ran the command. 
- Seeing that the re run also did not result in a solution, I removed the `*` glob and gave the full path along with required characters in the `[]` glob. 

```
hacker@globbing~matching-paths-with-:~$ /ch*/run /ch*/file/file_[absh]
Error: you will need to specify the path to the files as part of your glob 
argument, since they are in a different directory than your current working 
directory!
hacker@globbing~matching-paths-with-:~$ /ch*/run /ch*/files/file_[absh]
Error: you will need to specify the path to the files as part of your glob 
argument, since they are in a different directory than your current working 
directory!
hacker@globbing~matching-paths-with-:~$ /ch*/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{wJNz15nsCbxwymJZpMTa6Sc7jtH.QX0IDO0wSO3gjNzEzW}
hacker@globbing~matching-paths-with-:~$
```

## What I learned 
I learned that we can use `[]` glob to refer to multiple files, this can be especially useful for accessing multiple files at once in the commands that we want. 

## References 
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Multiple globs 
In this challenge of the *Linux Luminarium Dojo, File Globbing module,* we need to create a command to list a specific type of files in the `/challenge/files` directory subject to certain constraints in the name of the file. 

## My Solve 

**Flag:** `pwn.college{EAGqSmJZwC-hqWAa0P7t1g6gbex.0lM3kjNxwSO3gjNzEzW}` 

To solve the above challenge, I proceeded as below: 
- I first changed cwd to `/challenge/files`. Once there I ran the `/challenge/run` program with the necessary argument to get the flag. 
```
acker@globbing~multiple-globs:~$ cd /ch*/files
hacker@globbing~multiple-globs:/challenge/files$ /ch*/run *p*
You got it! Here is your flag!
pwn.college{EAGqSmJZwC-hqWAa0P7t1g6gbex.0lM3kjNxwSO3gjNzEzW}
hacker@globbing~multiple-globs:/challenge/files$
```

## What I learned 
I learned about the usage of multiple globs in a single command to enable us to search more efficiently and optimize our time so that we can achieve the result in the smallest amount of time. 

## References 
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Mixing globs 
In this challenge of the *Linux Luminarium Dojo, File Globbing module,* we need to create an argument that will allow us to find the common files, "challenging","educational", "pwning". 

## My Solve 

**Flag:** `pwn.college{c8KDfrUlXGuyLyuL4wUfOMwQwKA.QX1IDO0wSO3gjNzEzW}`

To solve the above challenge, I first changed my directory to the specified directory and then tried various combinations to satisfy the conditions. 
- The reason for `./[*cat*, *ing*]` argument was that two of the words end in ing and one word has cat in between, however, I understood after running that I was referencing ing in the middle of the name and of course the limit of 6 characters was crossed.
- The reason for `./[e*g]` argument was to first reach the limit of 6 characters, while keeping common letters in them.
- The reason for `./*n*` argument was to just use a single letter found in between all words to get the words, but I discovered a new constraint of needing to use the `[]` glob. 
- The reason for `[cep]` argument was two fold, one was to remove `./` to reduce the characters in argument, then it was to use the starting letters in a `[]` glob to find the result.
- The reason for `[cep*]` was to check for only the starting letters, but it was only after running the command that I realized I made the typo of keeping the `*` glob inside the `[]` glob. 
- Finally made the right argument and got the flag. 

```bash

hacker@globbing~mixing-globs:~$ cd /ch*/files
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run ./[*cat*,*ing*]
Error: your argument is too long! It must be 6 characters or less.
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run ./[e*g]
Error: your argument is too long! It must be 6 characters or less.
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run ./*n*
Error: you did not use a square bracket glob...
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run [cep]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[cep]
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run [cep*]
Your expansion did not expand to the requested files (challenging, educational, 
pwning). Instead, it expanded to:
[cep*]
hacker@globbing~mixing-globs:/challenge/files$ /ch*/run [cep]*
You got it! Here is your flag!
pwn.college{c8KDfrUlXGuyLyuL4wUfOMwQwKA.QX1IDO0wSO3gjNzEzW}
hacker@globbing~mixing-globs:/challenge/files$
```

## What I learned 
This was a really head banging challenge in which I had to think a lot to get the correct flag. I'm guessing I didn't understand the globs in the first go, but completing this challenge really made me understand how these globs work. 

## References
- https://pwn.college/linux-luminarium/globbing/
- Discussions with roommate
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Exclusionary Globbing 
In this challenge of the *Linux Luminarium Dojo, File globbing module,* we need to find files which do not start with p, w, n characters in a specific directory. 

## My Solve 

**Flag:** `pwn.college{4faEBDmJkccPdvZBFedt9fC6F_m.QX2IDO0wSO3gjNzEzW}`

To solve this problem, I first changed directories to the required one. Then I ran a command to get the resultant flag. 

```
hacker@globbing~exclusionary-globbing:~$ cd /ch*/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{4faEBDmJkccPdvZBFedt9fC6F_m.QX2IDO0wSO3gjNzEzW}
hacker@globbing~exclusionary-globbing:/challenge/files$

```

## What I learned 
In this challenge, I learned the usage of the `!` and `^` globs to exclude specific characters in the `[]` glob. 

## References 
- pwn.college{4faEBDmJkccPdvZBFedt9fC6F_m.QX2IDO0wSO3gjNzEzW}
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 9: Tab Completion 
In this challenge of the *Linux Luminarium Dojo, File Globbing Module,* we need to use the tab to complete the command to get the result. 

## My Solve 

**Flag:** `pwn.college{oEB_X91O_I2pCwipcAMBZlZy8jI.0FN0EzNxwSO3gjNzEzW}` 

To solve this I simply typed `cat /challenge/pwn<TAB>` to get the command completed. This gave me the resultant. 

```bash
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{oEB_X91O_I2pCwipcAMBZlZy8jI.0FN0EzNxwSO3gjNzEzW}
hacker@globbing~tab-completion:~$
```

## What I learned 
I learned the usage of Tab completion to complete the command. 

## References 
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 10: Multiple options for tab completion 
In this challenge of the *Linux Luminarium Dojo, File Globbing module,* we need to use tab completion command to get the flag. 

## My Solve 

**Flag:** `pwn.college{MT_QjLe5G6AmMfxBKKx3T1nQkc7.0lN0EzNxwSO3gjNzEzW}` 

To solve this I used the `cat /challenge/file/p<TAB>` as first test, then I built up on it and added college and then used the tab completion to get the list of possible files. Then I finally completed the command to get the flag. 

```
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
No flag in this file!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-
cat: /challenge/files/pwncollege-: No such file or directory
hacker@globbing~multiple-options-for-tab-completion:~$ ls /challenge/files/pwncollege-
No ls for you in this level! Use tab-completion instead!
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-
pwncollege-family      pwncollege-flag        pwncollege-flamingo    pwncollege-flyswatter  pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{MT_QjLe5G6AmMfxBKKx3T1nQkc7.0lN0EzNxwSO3gjNzEzW}
hacker@globbing~multiple-options-for-tab-completion:~$
```

## What I learned 
I learned more about tab completion and how we can use it automatically to get the results, even with multiple options. 

## References 
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 11: Tab Completion 
In this challenge of the *Linux Luminarium Dojo, File Globbing Module,* we need to use the tab completion on a command to get the flag. 

## My solve 

**Flag:** `pwn.college{EzHrn1N9YvG4ayId3cEafkWvc0H.0VN0EzNxwSO3gjNzEzW}` 

To solve this challenge, I simply typed out the `pwncollege<TAB>` to complete the command and get the flag. 

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-11976 
Correct! Here is your flag:
pwn.college{EzHrn1N9YvG4ayId3cEafkWvc0H.0VN0EzNxwSO3gjNzEzW}
hacker@globbing~tab-completion-on-commands:~$
```

## What I learned 
I learned that we can also use tab completion to complete commands as well. 

## References 
- https://pwn.college/linux-luminarium/globbing/
----------------------------------------------------------------------------------------------------------------------------------
