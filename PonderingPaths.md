## Pondering Paths 

# Challenge 1: The Root
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we need to run a pwn program using an absolute path to get the flag. 

# MY SOLVE FLAG: pwn.college{Qyed82nJcRnha2NHIvdrVIPQRwB.QX4cTO0wSO3gjNzEzW}

# Process: 
I simply typed out '''/pwn''' following the instructions of the challenge to get the flag. This allowed me to paste the flag onto the flag field in the bar below the workspace area to get the challenge completed alert. 

# What I learned: 
This challenge, and the reading up before this on the file system taught me that Linux uses a tree type file storage where every file resides on some 'branch' of the root file (root file acts as the 'trunk'). These 'branches' are often directories. I also learned that there are two types of paths, a relative path and an absolute path. The absolute path always starts with '''/....''' to indicate that we are start from root. The relative path can start from current directory and does need / in front of the path. 

# References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 2: Program and Absolute Paths
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we need to run a /challenge/run program(using absolute path) to get the flag. 

# MY SOLVE FLAG: pwn.college{0KIc_du9Gi2vHR8EJJ0SSp1OQCT.QX1QTN0wSO3gjNzEzW}

# Process: 
I messed around a bit in this and I went on a tangent by first changing to the  /challenge directory using the '''cd /challenge''' command and then using the '''./run''' command. I knew these commands because of the professor in class teaching us about this so I decided to try this. However it gave me an error that I didnt call it using the absolute path, so I went back to the root directory using '''cd /''' command and then I ran the program using '''/challenge/run''' command. This gave me the flag that I copied and pasted onto the flag field in the bar below the work area and got the challenge completion alert. 

# What I learned: 
I actually learned a lot from this by messing around and trying to do different things in different ways. This challenge taught me that absolute paths will always start from the root directory, meaning that to call a program that is present in a different directory that what we are currently working in, we can simply start from '''/....''' and follow the path of the branches to get to the needed program. It also cleared a wrong notion in my head, the wrong notion being '''./''' is a type of a command for execution. '''.''' actually is used in relative path which meant '''./''' command literally translates to 'From current directory go to the next one'. This really broadened my horizons. 

# References: 
1. Used SENSAI to actually understand what does '''.''' actually mean and got the hint from SENSAI of not using dot and making a call using /challenge/run. 
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 3: Position Thy Self 
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we need to be in a specific cwd (current working directory) and then run the /challenge/run program to get the result. 

# MY SOLVE FLAG: pwn.college{UcWc_QjqZaqfm4lsY_Dr9yBq3qQ.QX2QTN0wSO3gjNzEzW}

# Process: 
To solve this challenge I first ran the '''/challenge/run''' command from my cwd (/home/hacker). This told me that I need to change my cwd to /usr/share/build-essential directory so I ran the command of '''cd /usr/share/build-essential'''. This changed the '~' to the path of the directory and then I again ran '''/challenge/run''' command. This gave me the flag which I copied onto the flag field in the bar below the work area to get the challenge completion alert. 

# What I learned: 
In this challenge, I learned a very useful part of the Tree-like file system of Linux. This system allows us to invoke any directory from any location in the system as long as we know its absolute path. This will actually save a lot of hassle of having to switch between directories just to run a program. I also got curious about why the '~' part only changed so I googled it up and found that the '~' symbol is just a short hand to denote the /home/hacker directory. The hacker directory here can keep on changing as it denotes the user logged in. 

# References: 
1. https://www.quora.com/What-do-and-mean-in-the-Linux-Terminal - for knowing what ~ command stands for. 
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 4: Position Elsewhere 
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we again need to be in a specific cwd and then run the /challenge/run to get the flag. 

# MY SOLVE FLAG: pwn.college{o4PtHbOvSXa4Cjh1Pv3ASBFvZZD.QX3QTN0wSO3gjNzEzW}

# Process:
To solve this challenge I first ran the '''/challenge/run''' command from my cwd (/home/hacker). This told me that I need to change my cwd to / directory so I ran the command of '''cd /'''. This changed the '~' to the path of the directory and then I again ran '''/challenge/run''' command. This gave me the flag which I copied onto the flag field in the bar below the work area to get the challenge completion alert. 

# What I learned: 
This was pretty similar to the previous challenge and hence became more like a practice for navigating the file system without getting lost in it. 

# References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 5: Position yet elsewhere 
In this challenge of Linux Luminarium Dojo, Pondering Paths module, we need to first run the /challenge/run to find the directory we need to run it from and then run the program from that directory. 

# MY SOLVE FLAG: pwn.college{0YwrnQVVID4v3LtRqdogEjLCUMW.QX4QTN0wSO3gjNzEzW}

# Process: 
To solve this challenge I first ran the '''/challenge/run''' command from my cwd (/home/hacker). This told me that I need to change my cwd to /var/lib/apt/lists directory so I ran the command of '''cd /var/lib/apt/lists'''. This changed the '~' to the path of the directory and then I again ran '''/challenge/run''' command. This gave me the flag which I copied onto the flag field in the bar below the work area to get the challenge completion alert. 

# What I learned: 
Similar to the previous two challenges, this became a practice for going to a new directory location and invoking the run program using the absolute path. 

# References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 6: Implicit relative paths, from / 
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we need to invoke the run program from a specific directory using the implicit relative path. 

# MY SOLVE FLAG: pwn.college{MWzGgjq8hHFQrBD9TbXr5wMVSLa.QX5QTN0wSO3gjNzEzW}

# Process: 
To solve this challenge I first ran the '''/challenge/run''' command from my cwd (/home/hacker). This told me that I need to change my cwd to / directory so I ran the command of '''cd /'''. This changed the '~' to the path of the directory. I tried running '''cwd''' to check my current location, but it gave an error of command not found so I ran '''pwd''' to get the result. I knew the '''pwd''' command from PPS Lab and hence tried it out to get the correct result. Then I ran '''challenge/run''' command. This command became an implicit relative path to my cwd/pwd as it does not start with '''/....'''. This command then gave me the flag which I copied onto the flag field in the bar below the work area to get the challenge completion alert. 


# What I learned: 
The relative paths are always invoked from you cwd/pwd, which makes it useful for wanting to invoke programs or access file present in the current directory. I also googled the fullform of pwd command as I had used it in the terminal which told me that pwd stands for Print Working Directory.

# References: 
1. https://www.geeksforgeeks.org/linux-unix/pwd-command-in-linux-with-examples/ - for reading up on pwd. 
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 7: Explicit Relative paths, from / 
In this challenge of the Linux Luminarium Dojo, Pondering Paths Module, we need to invoke the run program from a specific directory using the explicit relative path.

# MY SOLVE FLAG: pwn.college{kfVMNWzfkkPpcO7lHk7n72cRFQR.QXwUTN0wSO3gjNzEzW}

# Process: 
To solve this challenge I first ran the '''/challenge/run''' command from my cwd (/home/hacker). This told me that I need to change my cwd to / directory so I ran the command of '''cd /'''. This changed the '~' to the path of the directory. Then I ran '''./challenge/run''' command. This command became an explicit relative path to my cwd/pwd as it starts with '''./....'''. This command then gave me the flag which I copied onto the flag field in the bar below the work area to get the challenge completion alert. 

# What I learned: 
This challenge made the differences between implicit and explicit relative paths crystal clear. Contrasting and comparing it to the previous challenge, I understood that running a command in the form '''./dir/prgrm''' explicitly tells the terminal to start from this directory and look for a directory named dir in the cwd. 

# References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
# Challenge 8: Implicit relative path 
In this challenge of Linux Luminarium Dojo, Pondering Path Module, we need to invoke the run program from /challenge directory by using an explicit relative path. 

# MY SOLVE FLAG: pwn.college{8fHGYjCcr8pZ-mnJG6t1-rhyKdD.QXxUTN0wSO3gjNzEzW}

# Process: 
To solve this challenge, I changed my pwd to /challenge directory using the '''cd /challenge''' command and then simply ran the '''./run''' command to invoke the program. This gave me the flag which I copied and pasted onto the flag field in the bar below the work area and got the challenge completion alert. 

# What I learned: 
This clarified an old misconception of mine where I thought '''./''' stand for execute program but it actually is explicit reference to cwd and then telling terminal to look for programs in the cwd's branches. 

# References: N/A
----------------------------------------------------------------------------------------------------------------------------------
# Challenge 9: Home sweet home 
In this challenge of the Linux Luminarium Dojo, Pondering Paths module, we need to copy the contents of the run file to a file of our own and the read it to get the flag. 

# MY SOLVE FLAG: pwn.college{UAHaAgvQmez0OT6VRkf-MU9oC9L.QXzMDO0wSO3gjNzEzW}

# Process: 
To solve this problem I first created a file 'test' using the command '''touch test'''(which again I learned from professors) then I ran the command shown in the challenge '''/challenge/run ~/test'''. This however gave me an error as told me to give an argument which has only 3 characters. So I removed the 'test' file using '''rm test'''(learned from professors) command and then created a file 'a' using '''touch a'''. Then I ran the command '''/challenge/run ~/a''' and I got the flag back. I then copied the flag and pasted it into the flag field below the work area and got the challenge completion alert. 

# What I learned: 
I learned that I need to read the questions carefully to avoid making silly mistakes and wasting time. If I can get it right in the first go, it helps in saving time for doing other challenges. 

# References: N/A
----------------------------------------------------------------------------------------------------------------------------------
