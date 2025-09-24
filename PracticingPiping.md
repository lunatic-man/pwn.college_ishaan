# Practicing Piping

## Challenge 1: Redirecting Output 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to redirect the output of an `echo` command to the specified text file to get the result. 

## My Solve 

**Flag:** `pwn.college{Mtb_rUVE1QLcOa8nOcU2wtGOjd4.QX0YTN0wSO3gjNzEzW}` 

To solve the above challenge, I followed the given process 
- I typed out the command `echo PWN > COLLEGE` to get the flag in one simple step. 

``` 
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{Mtb_rUVE1QLcOa8nOcU2wtGOjd4.QX0YTN0wSO3gjNzEzW}
hacker@piping~redirecting-output:~$
```

## What I learned 
From reading the material given in this module, I learned that every process has three parts, the Standard Input "stdin", the Standard Output "stdout" and the Standard Error "stdout". I also learned how we can redirect the contents of one program to append them or add them to another file. 


## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Redirecting more output 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to redirect the output of a program to the file with a specified name. 

## My solve 

**Flag:** `pwn.college{ACBleudPOiLhm3mNqfwBaX3CHkY.QX1YTN0wSO3gjNzEzW}`

To solve the above challenge, I followed the steps as listed below: 
- I ran the `/challenge/run` program with `>` character to redirect the output to the `~/myflag` file. 
- I then ran the `cat` command with `myflag` file as argument to get the contents of the file on my terminal. 

```
hacker@piping~redirecting-more-output:~$ /challenge/run > ~/myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat ~/myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ACBleudPOiLhm3mNqfwBaX3CHkY.QX1YTN0wSO3gjNzEzW}

hacker@piping~redirecting-more-output:~$

```

## What I learned 
In this challenge, I learned that even if a file does not exist before hand in the file system, the redirect operator will create the file at the specified location and then put the stdout of the program in the file. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Appending Output 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping Module,* we need to "append" the output of a program to the intended file. 

## My Solve 

**Flag:** `pwn.college{EAnFYmORz0zkSJw3ubn1RMAnzKD.QX3ATO0wSO3gjNzEzW}`

To solve this challenge, I followed the steps as given below: 
- I ran the `/challenge/run` program in the append mode `>>` and I redirected the output to the `~/the-flag` file. 
- I then ran the `cat` command along with the `~/the-flag` argument to get the flag. 

```bash
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag
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
hacker@piping~appending-output:~$
```


## What I learned 
From this module, I learned that the `>` mode of redirection simple overwrites any existing file. To save our data, we should use `>>` mode to ensure that we do not overwrite previous data and lose it. This will allow us to save multiple stdout results in one file, which we can filter through later using `grep`. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Redirecting errors 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping Module,* we need to redirect the output messages as well the error/instructions messages to different files in the file system. 

## My Solve

**Flag:** `pwn.college{ILY9K1LBe0jP1MZbwUhhUi9KKaj.QX3YTN0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I used a single line command to get the flag as per the question.

```
hacker@piping~redirecting-errors:~$ /challenge/run 1> ~/myflag 2> ~/instructions
hacker@piping~redirecting-errors:~$ cat ./myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{ILY9K1LBe0jP1MZbwUhhUi9KKaj.QX3YTN0wSO3gjNzEzW}

hacker@piping~redirecting-errors:~$ cat ./instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$

```

## What I learned 
In this challenge, I learned about the communication channels of stdin, stdout, stderr and how we can redirect the results of the program to specific files and add the results to the needed files. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Redirecting Input 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping Module,* we need to first write the word "COLLEGE" to the "PWN" file and then give this file as in input to the `/challenge/run` program. 

## My solve 

**Flag:** `pwn.college{Y2vc_UQzWqcXYAel4a5PeAXgDzt.QXwcTN0wSO3gjNzEzW}`

To solve the challenge, I followed the steps as listed below:
- I first ran the `echo` command along with necessary arguments to put "COLLEGE" in the PWN file. 
- After that, I ran the syntax for putting input into a program using `<` operator. 

```bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN 
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{Y2vc_UQzWqcXYAel4a5PeAXgDzt.QXwcTN0wSO3gjNzEzW}
hacker@piping~redirecting-input:~$

```

## What I learned 
In this challenge, I learned that for giving the input of the contents of the file to a program, we use the `<` operator. This allows us to run saved content without having to type it out, thus saving time. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Grepping stored results 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to store the results of a program in a specific file and then run the `grep` file to find the flag. 

## My solve 

**Flag:** `pwn.college{AaGTPhUyYadXCX0AuZSoj9s5g1M.QX4EDO0wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first ran the output redirection command as told in the challenge statement to send the result to `/tmp/data.txt`. 
- After doing that, I ran the `grep` command with the `pwn.college` argument along with file path to get the result as needed. The reason for using `pwn.college` as my search string was because I knew that the flag would be of the format `pwn.college{}`. 

```bash
hacker@piping~grepping-stored-results:~$ /challenge/run 1> /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{AaGTPhUyYadXCX0AuZSoj9s5g1M.QX4EDO0wSO3gjNzEzW}
hacker@piping~grepping-stored-results:~$ 

```

## What I learned
In this challenge, I learned that it is often easier to send the results of a program to a file and then find the needed line using `grep` as compared to manually searching through hundreds of thousands of lines of results. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Grepping live output 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to use the `grep` command without saving the results in a file. 

## My solve 

**Flag:** `pwn.college{ccAkRMokUEzJtuXytV-NpnbqnlN.QX5EDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I created a command using the `|` operator to *pipe* the result of the `/challenge/run` program into `grep` command. 
- The `grep` command takes `pwn.college` as the search string because the flag is of the format `pwn.college{}`. 

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{ccAkRMokUEzJtuXytV-NpnbqnlN.QX5EDO0wSO3gjNzEzW}
hacker@piping~grepping-live-output:~$ 

```

## What I learned 
In this challenge, I learned the usage of the `|` operator and how we can utilize it to send the output of certain programs directly as input of other programs or commands to get the result without having to save the results. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Grepping errors 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping Module,* we need to use a `>&` operator to convert one file descriptor to another file descriptor and then finally pipe it through `grep` command. 

## My solve

**Flag:** `pwn.college{kdvJxo1dB1Hxr82lNvXrt2MvANq.QX1ATO0wSO3gjNzEzW}` 

To solve the above challenge, I followed the steps as listed below: 
- First of all, I read through the challenge a second time to actually understand what the `>&` operator does. Once I understood what it actually does, I created a command to get the flag. 
- For the `grep` command I gave the argument as `pwn.college` because I know that a flag is in the format of `pwn.college{}` 

```bash
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{kdvJxo1dB1Hxr82lNvXrt2MvANq.QX1ATO0wSO3gjNzEzW}
hacker@piping~grepping-errors:~$

```

## What I learned 
In this challenge, I learned the usage of the `>&` operator to convert a file descriptor from one type to another type very easily. This allows us to pipe the result through the `|` operator, which only takes stdout(file descriptor is 1) as the input. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 9: filtering with grep -v
In this challenge of *Linux Luminarium Dojo, Practicing Piping modules,* we need to find the real flag by filtering out all the decoy flags by using the `-v` argument in the `grep` command. 

## My solve 

**Flag:** `pwn.college{0-71rU0-Lt2k_FkE5K1-i4rbrUa.0FOxEzNxwSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first ran the command, but I ended up setting the string in small letters, i.e., `decoy`. After realizing my mistake(by seeing a thousand flags printed out), I corrected the command and changed it to `DECOY`. 
- final command `/challenge/run | grep -v DECOY` 

```bash 
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v decoy
pwn.college{ExjrNiOgtkNkOEKU.zDECOYE0xU-15WF-z2FrwzS0L4a_b3}
pwn.college{2.--EF0FONwbUEtL_OxN3Ukjkr4DECOYWiKrz1x5SzazE0g}
pwn.college{KOLz-x_NUrEgkOrDECOYxE-F2j.aSbz41kU5tNE03FzwiW0}
pwn.college{tr1O-_Wb2FxSzgK4-r5zjEwExENN0U3Lakz0iDECOYUOF.k}
pwn.college{Ez5DECOYLESK_-zw0ikUrEFUbNj2.zN-30g1OtrxOx4FWak}
pwn.college{5j-0F3t1.WNx-Sz2ikUEa4rz_0OErNDECOYUzFbwKxOLgEk}
pwn.college{UxEK4FkbaLNUEx2Ni10r3z.0jDECOY-WzOgEFkrz_OSw-5t}
pwn.college{tw_-0OON1SFiDECOYz.N4bzj5WLxErEkF3k0x-UaKrEg2zU}
pwn.college{3zi0z52aEkwrKUSxgNOkL41._-zxUrFO-tWE0jEFNbDECOY}
pwn.college{-z.5iOSNxOLDECOYKNgF01Wkzr3-0UUkF2wEzjr_xtEaE4b}
pwn.college{baE_xxzrEgDECOY0zjkU5wtiOSF3UzLNK2r4.-k1O0E-NFW}
pwn.college{.kaK01LSEE-r25jFzzDECOY-O3xwbNzgFx4iNtUOrk_E0UW}
pwn.college{jzxULKkt-kESz0rFrO-3U1W_zNDECOYN4FOEb5iwga.E02x}
pwn.college{zFNjkWawUOr-t-gzN3bO_k2F4KU10xDECOYEri.xz5EL0ES}
pwn.college{gz0WN3z5UDECOYEi-2Ka0wOE.bNtFkUErLrOk4zjF_Sx-1x}
pwn.college{UKFrk21Ez4_b-gzOaN0UjxEz.SFN3Er-t0WwkOxLDECOYi5}
.
.
.
.
pwn.college{0ELjxzEUOg4r-.tbEkDECOY51Szr3z_i-0FUwkOaN2xWNFK}
pwn.college{U-ELgk.OrrSK3aFFN_5Okj1EzDECOYt24bEzx-Ux0WNizw0}
pwn.college{tr-SDECOYjkkFa5.-Nzxr4_3NFEEzi2bOWUO0xLUzEgwK10}
pwn.college{2xFU1_kzr0-gaO.FiS-0z4LUDECOYjt3OEEzbwNxWE5rKNk}
pwn.college{--5O2j_Wtzrar.kO1EFLEFUi30SEDECOY0zxUK4wzkgbNxN}
pwn.college{KzFazUzjtE-kLrF4b-xgk_02Sx1NUwO5E3EOr0NDECOY.Wi}
pwn.college{Sk-gwLOrNNkar1zxKF_WFDECOYEzzxEU2UEbt30jO0.5-i4}
pwn.college{kz3gk-FE4S5E2xK0rDECOYa-_iUbW1z.Nwj0ONxUOELzFrt}
pwn.college{-xziOzULNWE_1t.zODECOYrkbrE0FFK5kxgU2jN4Ea3-wS0}
pwn.college{EE0kEUUN5zO0DECOYtz_KrFNkb.zSgF3a-4rxwWj-iO2xL1}
pwn.college{.wW01iE0DECOYEOg_2Lr-UxkKUNzaz4xFN5tSr-Ebz3FkjO}
pwn.college{ztOKFx1.rz0bFkLUg0j5_aE4DECOYEkSNWw2N-z3xrU-OiE}
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{0-71rU0-Lt2k_FkE5K1-i4rbrUa.0FOxEzNxwSO3gjNzEzW}
hacker@piping~filtering-with-grep-v:~$

```

## What I learned 
In this challenge, I learned the usage of the `-v` argument of the `grep` command to find the line NOT containing a specific keyword. I also learned that string arguments in the `grep` command are case sensitive. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 10: Duplicating piped date with tee 
In this challenge of the *Linux Luminarium Dojo, Practicing Pipe module,* we need to use the `tee` command along with `|` operator to get the output of the file and analyze it to get the result. 

## My solve

**Flag:** `pwn.college{QnwJL9PNN256qoK6AW5p5POqAfX.QXxITO0wSO3gjNzEzW}` 

To solve the above challenge, I used the following steps: 
- I first typed out the pipe command as mentioned in the challenge to get the output stored in the `~/error` file. 

```bash 
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee ~/error | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$
```

- However, I went on a slight tangent here because of the misunderstanding of how the `tee` works. I thought that `tee` would print the output to the terminal and then send the same output to the next pipe. So reading the terminal as shown above, I got thoroughly confused and ended up trying a few commands as shown below. 
- I ran the `/challenge/pwn | tee ~/output` command assuming that it would save the output to the `~/output` file and also write it out the same terminal. 

```bash
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee ~/output
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between* 
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$

```

- After reading the error report, I realized that my original syntax was correct, it just needed some modification. So I sat and thought about this for a while and re-read the challenge statement. 
- On re-reading the challenge statement, I realized that `tee` takes an argument with it. So I read the example syntax to understand that this argument is actually the name of the file in which it stores the output. But I knew that `tee` was named after T splitter, meaning it can only give output at two places. 
- What this basically meant was that I wrongly assumed that I get the output on the terminal, instead this gets saved to a file which I passed as the argument, and the errors get printed out to the terminal.
- Based on above reasoning, I decided to cat the `~/error` file (because I knew this contained output, not errors and the hint told us to read the output of pwn program) and got the following result

```bash 
hacker@piping~duplicating-piped-data-with-tee:~$ cat ./error
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "QnwJL9PN"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret QnwJL9PN | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{QnwJL9PNN256qoK6AW5p5POqAfX.QXxITO0wSO3gjNzEzW}
hacker@piping~duplicating-piped-data-with-tee:~$

```
- I followed through the process to finally get the flag. 

## What I learned 
I learned how to save the output of a particular program in the system when we are running the system through the `|` operators using the `tee` command. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 11: Process substitution for input 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping Module,* we need to find the difference between two programs by using `diff` and *named pipe*. 

## My Solve 

**Flag:** `pwn.college{81L2xOYwgV2UouotWElFECpbX7i.0lNwMDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the given steps: 
- I first read through the challenge statement twice to understand what do we mean by the philosophy of "everything is a file" and named pipe. 
- After understanding the two concepts, I then used the `diff` command with the necessary arguments to find the flag. 
```bash
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
15a16
> pwn.college{81L2xOYwgV2UouotWElFECpbX7i.0lNwMDOxwSO3gjNzEzW}
hacker@piping~process-substitution-for-input:~$
```

- From the output, I can tell you that the first file has only 15 lines and the actual flag is present in the 16th line in the second file. 

## What I learned
In this challenge, I learned about the concept of "everything is a file" in the linux systems, and how to utilize this concept to give the inputs to a command as the named pipe files. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 12: Writing to multiple programs 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to write the output of one program simultaneously to two other programs. 

## My Solve 

**Flag:** `pwn.college{A2U7wfLNa-ohwlLQf0x5QLFtFov.QXwgDN1wSO3gjNzEzW}` 

To solve the challenge, I followed the steps as listed below: 
- I first read through the challenge material in depth to understand how exactly does a named pipe take an input. I was happy to see it was similar to the process I had imagined in my mind in the previous challenge. 
- Armed with this knowledge and understanding, I wrote the command and got it write in the first go. 

```bash 
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
1450610845308322005
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{A2U7wfLNa-ohwlLQf0x5QLFtFov.QXwgDN1wSO3gjNzEzW}
hacker@piping~writing-to-multiple-programs:~$

```

## What I learned 
In this challenge, I learned that the named pipes are very useful concepts which allow us to either make the output of a program as a temporary file or give the input to a program by fooling the commands to think it is a file. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 13: Split-piping stderr and stdout 


## My solve

**Flag:** `pwn.college{co5oLSM0duxMBYihn2_d8kjhzFS.QXxQDM2wSO3gjNzEzW}` 

To solve this challenge, I followed the steps given below: 
- This was one of the longest challenges I ever solved as it took me a long while to understand what I was doing wrong and how to correct it. 
- To solve this challenge I first ran the `/challenge/hack | /challenge/planet 2> >(/challenge/the)` command and tired to run it but got the following error. 


```bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack | /challenge/planet 2> >(/challenge/the)
You must redirect my standard error into '/challenge/the'!
You are redirecting standard error *of /challenge/planet*! Instead, you must 
redirect standard error of 'hack'. This must be done *before* any |. The right 
side of the pipe is a different command, with its own redirection, than the 
left side!
Are you sure you're properly redirecting /challenge/hack's standard error into 
'/challenge/the'?
hacker@piping~split-piping-stderr-and-stdout:~$
```

- After seeing the above error, I decided to close the challenge for the night and revisit it the next day. When I started the next day I again re read the material and discussed the challenge with my roommate, as well as re read all the information in the challenges. On re reading I found out that the pipe operator sends the stdout of the *previous* command to the next one, while the `>` operator does it for the original command. This is a simple sentence to put in this report right now, but it took me 30 mins of reading to understand this difference. 

- Armed with my newfound knowledge, I scripted another command, `/challenge/hack > >(/challenge/planet) 2> >(/challenge/the)` and then ran it to get the result. 

- What the above command essentially does is that it first runs the `/challenge/hack` program and gives us a stdout as well as stderr. I then specify that the stdout(represented by the `>` operator) should be sent to the `>(/challenge/planet)` file. I also specified that the original error (represented by the `2>` file descriptor) should be sent to the `>(/challenge/the)` file. 

```bash 
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{co5oLSM0duxMBYihn2_d8kjhzFS.QXxQDM2wSO3gjNzEzW}
hacker@piping~split-piping-stderr-and-stdout:~$
```

- I also re-read my original command (`/challenge/hack | /challenge/planet 2> >(/challenge/the)`) to understand what it meant. This program first runs the `/challenge/hack` program to get a stdout and a stderr. However, using the `|` operator only forwards the stdout of the program to the `/challenge/planet` program and when we use the `2>` file descriptor, we are actually redirecting the error of the `/challenge/planet` program and not the `/challenge/hack` program. 

## What I learned 
I learned the full usage and utilization of the `>` operator and the `|` operator to find the results that we need and how we can craft a command to get the results that we want. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
- Discussions with roommate 
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 14: Named pipes 
In this challenge of the *Linux Luminarium Dojo, Practicing Piping module,* we need to redirect the output of the program to a FIFO (First in, First out) file and then read the data from the same file using a different terminal. 

## My Solve 

**Flag:** `pwn.college{cVKvARSOmqRprLIRR55Sha9CNj_.01MzMDOxwSO3gjNzEzW}` 

To solve this challenge, I used the steps as listed below: 
- I first read the challenge and understood what exactly is meant by FIFO type files and how exactly they are different from the normal files. 
- After reading through the challenge statement, I used the `mkfifo /tmp/flag_fifo` command to make a FIFO file in the required directory. 
- Then I ran the `/challenge/run > /tmp/flag_fifo` to send the output of the program to the FIFO file. This made my terminal freeze as shown below

```bash
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo! 
Bash will now try to open the FIFO for writing, to pass it as the stdout of 
/challenge/run. Recall that operations on FIFOs will *block* until both the 
read side and the write side is open, so /challenge/run will not actually be 
launched until you start reading from the FIFO!

```

- Then I opened another terminal on my laptop and connected using SSH. After having securely connected to `hacker@dojo.pwn.college` I ran the `cat /tmp/flag_fifo` file to get the flag.

```bash 
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at 
/tmp/flag_fifo! Here is your flag:
pwn.college{cVKvARSOmqRprLIRR55Sha9CNj_.01MzMDOxwSO3gjNzEzW}
hacker@piping~named-pipes:~$

```

## What I learned 
In this challenge, I learned about the existence of the FIFO type files and what they are used for. I learned that the data in FIFO is ephemeral, and that once it has been read, it is deleted, this is really useful for analyzing data without having to worry about how to handle it once we have analyzed it. 

## References
- https://pwn.college/linux-luminarium/piping/
- https://web.archive.org/web/20220629044814/http://bencane.com:80/2012/04/16/unix-shell-the-art-of-io-redirection/
----------------------------------------------------------------------------------------------------------------------------------
