# Chaining Commands 
## Challenge 1: Chaining with semicolons
In this challenge of the *Linux Luminarium Dojo, Chaining Commands module,* we need to run two program in succession in the same line by separating the calls using semicolons. 

## My solve 

**Flag:** `pwn.college{A4i1_VQ13l42dcsPhyi-Fm2q6zQ.QX1UDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below:
- This was a fairly simple challenge, where I followed the steps in the challenge statement to craft a command and use semicolon in between to separate two commands. On executing that command, I got the flag back. 

```bash 
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college;
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{A4i1_VQ13l42dcsPhyi-Fm2q6zQ.QX1UDO0wSO3gjNzEzW}
hacker@chaining~chaining-with-semicolons:~$
```

## What I learned 
From this challenge, I learned that we can run multiple commands in one line using semicolon to separate them. 

## References
- https://pwn.college/linux-luminarium/chaining/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Building on Success 
In this challenge of the *Linux Luminarium Dojo, Chaining Commands Module,* we need to run the first program and if it succeeds, run the second program to get the flag. 

## My solve

**Flag:** `pwn.college{ovF35H86OiXQv7NBA1euhBkfmLj.0lM0MDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply followed the instructions in the challenge statement which allowed us to craft a command using `&&`. 

```bash 
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{ovF35H86OiXQv7NBA1euhBkfmLj.0lM0MDOxwSO3gjNzEzW}
hacker@chaining~building-on-success:~$
```

## What I learned 
From this challenge, I learned about how we can use the `&&` operator to chain commands to work only when the previous command has succeeded. 

## References 
- https://pwn.college/linux-luminarium/chaining/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Handling Failure 
In this challenge of the *Linux Luminarium Dojo, Chaining Commands module,* we need to use the `||` operator to chain commands for failure. 

## My solve 

**Flag:** `pwn.college{kLQZ3ZmAtlj5kxevvwLXe9Xvsyy.01M0MDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply crafted a command as per the challenge statement using the `||` operator to get the flag. 

```bash 
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{kLQZ3ZmAtlj5kxevvwLXe9Xvsyy.01M0MDOxwSO3gjNzEzW}
hacker@chaining~handling-failure:~$
```

## What I learned
From this challenge, I learned about `||` operator and how we can utilize it to handle errors and issues in our command flow. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Your first shell script 
In this challenge of the *Linux Luminarium Dojo, Chaining Commands module,* we need to create our first shell script to invoke `/challenge/pwn` and `/challenge/college` programs. 

## My Solve 

**Flag:** `pwn.college{UD6VkKNmvXvz0mGcs-fu04Jd4hz.QXxcDO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge statement and understood what do you mean by a shell script. I also took the help of ChatGPT to understand the format and syntax that I need to follow for writing a shell script. 
- After understanding the format, I created a `x.sh` file in the system and gave it executable permissions. 

```bash 
hacker@chaining~your-first-shell-script:~$ touch x.sh 
hacker@chaining~your-first-shell-script:~$ chmod a+x x.sh
hacker@chaining~your-first-shell-script:~$ ls -l x.sh
-rwxr-xr-x 1 hacker hacker 0 Sep 30 05:35 x.sh
hacker@chaining~your-first-shell-script:~$
```

- Then after creating this file, I used the nano editor to write the script. 

```bash 
hacker@chaining~your-first-shell-script:~$ nano x.sh


  GNU nano 8.4                                                     x.sh                                                                
#!/bin/bash

/challenge/pwn
/challenge/college













                                                           [ Read 4 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy

```

- After writing the script, I saved the script and exited the editor. Then I ran the `bash` command with the name of the script file as an argument to get the flag. 

```bash 
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{UD6VkKNmvXvz0mGcs-fu04Jd4hz.QXxcDO0wSO3gjNzEzW}
hacker@chaining~your-first-shell-script:~$
```

## What I learned 
From this challenge, I learned about the existence of scripts in linux and how we can write longer commands in a script and then ask linux to run that script. 

## References
- https://pwn.college/linux-luminarium/chaining/
- https://chatgpt.com/c/68db6bca-f0c0-8323-bb26-5ca2a388c845
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Redirecting Script Output
In this challenge of the *Linux Luminarium Dojo, Chaining commands module,* we need to send the output of a script to the input of another command to get the flag. 


## My solve 

**Flag:** `pwn.college{oMtQuP1DJ_K7sjybMp9DnMUbpei.QX4ETO0wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- Utilizing the file persistence characteristic of pwn.college, I knew that my script which invoked `/challenge/pwn` and `/challenge/college` already existed in the `/home/hacker` directory. 
- I simply invoked that script by using the `bash` command and piped it using the `|` operator to the `/challenge/solve` program to get the flag. 

```bash 
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{oMtQuP1DJ_K7sjybMp9DnMUbpei.QX4ETO0wSO3gjNzEzW}
hacker@chaining~redirecting-script-output:~$
```

## What I learned 
From this challenge, I learned that the output of a script can be treated as the output of any other command and all operations done for redirection or piping are valid on script outputs as well. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Executable Shell Scripts 
In this challenge of the *Linux Luminarium Dojo, Chaining commands module,* we need to give executable permissions to our shell script so that we can run it without having to call the `bash` command. 

## My solve

**Flag:** `pwn.college{UzUSOMQdN2CB8Mbz1Hb_5XU1T-R.QX0cjM1wSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first created a script with the name of `invoke.sh`. Then I opened the script in nano to put in the `/challenge/solve` command in it. 


```bash 
hacker@chaining~executable-shell-scripts:~$ touch invoke.sh
hacker@chaining~executable-shell-scripts:~$ nano invoke.sh

  GNU nano 8.4                                                   invoke.sh                                                             
#!/bin/bash

/challenge/solve







                                                           [ Read 3 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy
```

- After creating the `invoke.sh` script, I used `chmod` to give executable permissions to the owner. 
- Then I called the script by using `./invoke.sh` command. 

```bash
hacker@chaining~executable-shell-scripts:~$ chmod u+x invoke.sh
hacker@chaining~executable-shell-scripts:~$ ./invoke.sh
Congratulations on your shell script execution! Your flag:
pwn.college{UzUSOMQdN2CB8Mbz1Hb_5XU1T-R.QX0cjM1wSO3gjNzEzW}
hacker@chaining~executable-shell-scripts:~$
```

## What I learned 
From this challenge, I learned that I did not need to give executable permissions to my shell script in challenge 4, as it was an argument and did not necessarily need an executable permission. I also learned how to give these permissions to a file so I can run and invoke these shell scripts without needing the `bash` command. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Understanding Shebangs 
In this challenge of the *Linux Luminarium Dojo, Chaining commands Module,* we need to create a `solve.sh` script and make sure it invokes `/bin/bash` as the interpreter using shebangs. 

## My solve 

**Flag:** `pwn.college{4BHBUnlZRS4cPkfqgEQZA_lcxTU.0VOzMDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first created a shell script, `solve.sh` in the `/home/hacker` directory of the system. 
- I then edited the script using nano to add a shebang first, `#!/bin/bash` and then I added the `echo` command with necessary arguments. 
- I gave the script executable permissions and then I invoked the `/challenge/run` program to get the flag. 

```bash 
hacker@chaining~understanding-shebangs:~$ touch solve.sh
hacker@chaining~understanding-shebangs:~$ nano solve.sh 
  GNU nano 8.4                                                   solve.sh                                                              
#!/bin/bash

echo "hack the planet"



                                                           [ Read 3 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy



hacker@chaining~understanding-shebangs:~$ chmod a+x solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{4BHBUnlZRS4cPkfqgEQZA_lcxTU.0VOzMDOxwSO3gjNzEzW}

hacker@chaining~understanding-shebangs:~$
```

## What I learned 
From this challenge, I learned about the existence of **shebangs** and what they actually do. I learned how a script executes and how we can ensure that we are using the interpreter that we want by specifying it inside the script only. 

## References
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Scripting with Arguments 
In this challenge of the of the *Linux Luminarium dojo, Chaining Commands module,* we need to reverse the arguments that we get as input. 

## My solve 

**Flag:** `pwn.college{AhKXwYpSSveNCJMk3b592DFoUxq.0VNzMDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first read the challenge statement to understand how a script reads the arguments as input and in what variable it stores them. 
- After understanding this, I simply used the echo command to reverse the output order of the arguments. 

```bash 
hacker@chaining~scripting-with-arguments:~$ touch solve.sh
hacker@chaining~scripting-with-arguments:~$ nano solve.sh

  GNU nano 8.4                                                   solve.sh                                                              
#!/bin/bash



echo "$2 $1"











                                                           [ Read 5 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy


hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{AhKXwYpSSveNCJMk3b592DFoUxq.0VNzMDOxwSO3gjNzEzW}
hacker@chaining~scripting-with-arguments:~$

```

## What I learned 
From this challenge, I learned how a script stores the arguments given to it in variables and how we can access and manipulate those variables to get the intended result. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 9: Scripting with Conditionals 
In this challenge of the *Linux Luminarium Dojo, Chaining Commands Module,* we need to create a script which checks if the given argument is equal to a certain value or not. 

## My solve 

**Flag:** `pwn.college{Mx345dHYNwe8GtICxh0g3ccBCHM.0lNzMDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge statement to understand all the minute details about the syntax of a script. 
- After understanding the differences, I crafted a block of code using the `if` conditional to get the desired result. 
- After creating and saving the script, I invoked the `/challenge/run` program to get the flag. 

```bash 
hacker@chaining~scripting-with-conditionals:~$ touch solve.sh
hacker@chaining~scripting-with-conditionals:~$ nano solve.sh  
    GNU nano 8.4                                                   solve.sh                                                              
#!/bin/bash


if [ "$1" == "pwn" ]
then
        echo "college"
fi












                                                           [ Read 8 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy



hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{Mx345dHYNwe8GtICxh0g3ccBCHM.0lNzMDOxwSO3gjNzEzW}
hacker@chaining~scripting-with-conditionals:~$

```

## What I learned 
From this challenge, I learned about the existence of conditionals in a script. These conditionals allow us to manipulate the data that we receive as arguments in the way we deem fit. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 10: Scripting with default lines 
In this challenge of the *Linux Luminarium Dojo, Chaining commands module,* we need to create a conditional block of code which also includes default cases. 

## My solve 

**Flag:** `pwn.college{QcnAdeKhPBHFtcLrATKV-XCMbmD.01NzMDOxwSO3gjNzEzW}` 


To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge statement to understand what the challenge expected from us and how we can create a script to solve it. 
- Using the persistence principle applicable in the files in `/home/hacker` directory, I simply opened the `solve.sh` script in the nano editor to edit the previous script and add just an `else` conditional in it. 


```bash 
hacker@chaining~scripting-with-default-cases:~$ nano solve.sh

  GNU nano 8.4                                                   solve.sh                                                              
#!/bin/bash


if [ "$1" == "pwn" ]
then
        echo "college"
else
        echo "nope"
fi








                                                           [ Read 10 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy


hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{QcnAdeKhPBHFtcLrATKV-XCMbmD.01NzMDOxwSO3gjNzEzW}
hacker@chaining~scripting-with-default-cases:~$

```

## What I learned 
From this challenge, I learned about how we can create default cases in our scripts to ensure smooth handling of scenarios where the input of arguments is not what we want it to be. 


## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 11: Scripting with Multiple Conditions 
In this challenge of the *Linux Luminarium Dojo, Chaining Commands module,* we need to create a script in which we need to test if the argument satisfies any of the multiple conditions possible. 

## My solve 

**Flag:** `pwn.college{QINMnf6JeTcQqizB02xCloB7EQ_.0FOzMDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I first read through the challenge statement to understand how do we include multiple conditionals in our script. 
- After understanding that, I simply opened the script using nano editor. 
- After editing the script to suit our requirements, I saved the script and invoked the `/challenge/run` program to get the flag. 

```bash 
hacker@chaining~scripting-with-multiple-conditions:~$ nano solve.sh
  GNU nano 8.4                                                   solve.sh                                                              
#!/bin/bash


if [ "$1" == "hack" ]
then
        echo "the planet"
elif [ "$1" == "pwn" ]
then
        echo "college"
elif [ "$1" == "learn" ]
then
        echo "linux"
else
        echo "unknown"
fi










                                                           [ Read 16 lines ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy

hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{QINMnf6JeTcQqizB02xCloB7EQ_.0FOzMDOxwSO3gjNzEzW}
hacker@chaining~scripting-with-multiple-conditions:~$

```

## What I learned 
From this challenge, I learned about the usage of the `elif` conditional and how we can use it to handle cases where we a value may satisfy one of many conditions possible. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 12: Reading shell scripts
In this challenge of the *Linux Luminarium Dojo, Chaining Commands module,* we need to figure out the password needed to successfully invoke `/challenge/run` program and get the flag. 

## My solve 

**Flag:** `pwn.college{gUd3yZa-1Pet5aaeHQ1x66QzCOQ.0lMwgDOxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I read through the challenge to understand what the challenge expected us to do. 
- After reading through the challenge and figuring out, I opened the script of `/challenge/run` program in the nano editor to find the hardcoded password. 
- After getting the password, I first passed it as an argument assuming it wants us to do that, however, on pressing enter it did not give me any result and got stuck as show below: 

```bash 
hacker@chaining~reading-shell-scripts:~$ nano /challenge/run

  GNU nano 8.4                                                /challenge/run                                                           
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi







                                                [ File '/challenge/run' is unwritable ]
^G Help         ^O Write Out    ^F Where Is     ^K Cut          ^T Execute      ^C Location     M-U Undo        M-A Set Mark
^X Exit         ^R Read File    ^\ Replace      ^U Paste        ^J Justify      ^/ Go To Line   M-E Redo        M-6 Copy



hacker@chaining~reading-shell-scripts:~$ /challenge/run hack the PLANET

```

- I then pressed enter again and it gave me the error for the default case. I then realized that the use of the `read` keyword here signified something. Analyzing the result I got above, I realized that `read` tells the script to wait for an input from the user and then takes that value and stores it in the variable. 
- Following this new train of thought, I invoked the `/challenge/run` program, and then passed `hack the PLANET` as the input. This gave me the correct flag, thus completing the challenge. 

```bash 
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{gUd3yZa-1Pet5aaeHQ1x66QzCOQ.0lMwgDOxwSO3gjNzEzW}
hacker@chaining~reading-shell-scripts:~$

```

## What I learned 
From this challenge, I learned that we can create variables with a name of our choosing and use the `read` keyword to wait for input from the user in the terminal itself. This allows us to create variables with names which give a good description of what they do. 

## References 
- https://pwn.college/linux-luminarium/chaining/
----------------------------------------------------------------------------------------------------------------------------------
