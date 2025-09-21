USING THE TERMINAL 

This is a part of the Start Here Dojo, Using The Dojo module, where we are taught the basics of how we are supposed to launch a terminal and how to find flags and paste them into the Flag section as needed to solve the problem.

MY SOLVE FLAG: pwn.college{0jlMdsVB25Qj9PF-p2m8cF_dbob.0lMwQDOxwSO3gjNzEzW}

This challenge did not require me to think much, I just followed the instructions on screen which told me to click the Start button, and the flag was simply in the terminal which I pasted into the Flag section to solve it. 

WHAT I LEARNED: 

I learned about the terminal in this challenge and how I am supposed to open it to get the flags after following a process and pasting that flag into the flag section to complete a challenge 

REFERENCES: N/A 

-----------------------------------------------------------------------------------------------------------------------------------
USING THE VSCode WORKSPACE 

This challenge is a part of Start Here Dojo, Using The Dojo module, where we are asked to switch our workshop from terminal mode to VSCode mode using the workshop selector on the bar below the terminal window. 

MY SOLVE FLAG: pwn.college{EVHG9nwtDqKljCygqIYAR8aytDg.QX2IzNzwSO3gjNzEzW}

This challenge was pretty simple, it showed me how to switch between various modes of a workshop(terminal, code, desktop, ssh), and we needed to follow the steps given to switch to VSCode workshop so we could get the flag. 

WHAT I LEARNED:

I learned about the various workshops that are accessible to us by solving this challenge, and that I can always choose what type of workshop I want to use to solve a particular challenge 

REFERENCES: N/A

-----------------------------------------------------------------------------------------------------------------------------------
USING THE GUI DESKTOP 

This challenge is part of the Start Here Dojo, Using the Dojo module, where our objective is to use the GUI desktop from workshop selector, and open a terminal in the desktop to get the flag 

MY SOLVE FLAG: pwn.college{8MpuEFzb6vGpyvl1fuIaqW1HEfX.QX3IzNzwSO3gjNzEzW}

This challenge was a bit different from the other two because of the unique way of getting the flag out of the terminal in the Desktop. We switched from VSCode workshop to Desktop workshop and then opened and XFCE terminal, this terminal on loading, gave us the flag, this flag we copied, and then we again copied this flag from the clipboard that was attached to the desktop. Finally pasting this into the flag section in the bar below the work area gave us the successful completion remark. 

WHAT I LEARNED: 

I learned that pwn.college remembers the workshop I used the last time instead of defaulting to a base terminal one, I also learned that opening a terminal gives the same result, irrespective of the location or method used to open it. We can choose any method we like to get the flag, which is the ultimate end goal. 

REFERENCES: N/A 
-----------------------------------------------------------------------------------------------------------------------------------
PASTING INTO THE DESKTOP 

This is a challenge of the Start Here Dojo, Using the Dojo module, where we need to paste a given token into the desktop when the terminal asks us for it

MY SOLVE FLAG: pwn.college{wKuM5xxMWODxxczlW90Y1PvgNxk.QX4IzNzwSO3gjNzEzW}

This challenge was in a way just the reverse of what we did to get the flag out of the desktop in the previous task. We first uploaded the given secret token into the clipboard and then we pasted the token into the terminal when prompted. This led us to our flag which we pasted into flag section in the bar below the the work area, which successfully completed the task. 

WHAT I LEARNED: 

I learned that using a GUI desktop sometimes becomes a hassle, especially when it comes to copying and pasting data into the terminal of the desktop. That being said, GUI Desktop may also have some benefits over other workshops that I am yet to discover. 

REFERENCES: N/A 
-----------------------------------------------------------------------------------------------------------------------------------
RESTARTING CHALLENGES

This is a challenge of the Start Here Dojo, Using the Dojo module, where we are required to restart a challenge after entering a wrong password and collecting the right one and then using it a second time to gain access to the system. 

MY SOLVE FLAG: pwn.college{I_ckjIu55L250YRM0FdqX84nsOz.QX1kDM1wSO3gjNzEzW}

The method of going about solving this challenge was opening it in a simple terminal mode, enter a '''password''' as password when prompted into the terminal and get the correct the password, copy the correct password, after which you press the restart button next to the fullscreen button at the bottom of the terminal area and then enter the correct password in the second run to get the flag. 

WHAT I LEARNED: 

I learned that there might be times where I damage the machine or the data in a challenge and I will need to restart the challenge again, so this method is useful to restart the challenge when needed to bring it to completion. 

REFERENCES: N/A
-----------------------------------------------------------------------------------------------------------------------------------
GETTING HELP 

This is a challenge of the Starting Here dojo, Using the Dojo module, where we are introduced to our SENSAI, our guide and mentor and we need to find the password from him to get the password. 

MY SOLVE FLAG: pwn.college{0e3GMcAhaNCirhkUlwad0FLAwGW.QXyIDN1wSO3gjNzEzW}

The method of solving this challenge was pretty straightforward where we asked the SENSAI to give us the password for the room. SENSAI automaticall detected the room that we were in and gave us the password (pwn-the-planet). Entering '''pwn-the-planet''' when asked to do so allowed us to find the flag which we entered into the flag section in the bar below our work area. 

WHAT I LEARNED: 

For any questions that I may have related to the problem or the challenge, I can ask SENSAI for hints and guides, or just discuss with the SENSAI and see if I am going in the right direction or not. 

REFERENCES: N/A
----------------------------------------------------------------------------------------------------------------------------------
CHALLENGE PROGRAMS 

This is a challenge in the Start Here Dojo, Using the dojo module, where are required to access the /challenge directory from root and run the solve program to get the flag. 

MY SOLVE FLAG: pwn.college{cysVtovtjfT-5hQ5qtgJnN2TwRC.QX0MDO0wSO3gjNzEzW}

This was fun challenge as the role of Linux commands and directories came into picture. We started off in the /home/hacker directory and switched to root by using '''cd /''' command. Here we listed out all other directories by using '''ls -a'''. I did find a flag file here and tried opening it using '''cat flag''' but I did not have permissions for it, so I followed the path as laid down in the problem statement. Using '''cd challenge''' I switched to challenge folder and then again used '''ls''' to find the required program which was solve. To run the solve program I used the command '''./solve''' where I got the required flag. Pasting this flag in the flag section allowed us to complete the challenge. 

WHAT I LEARNED: 

I used my existing knowledge about directories and programs to find out where the required directory was. This gave me practice for finding files/directories in a system by navigating to wherever I need to go.

REFERENCES: N/A 
----------------------------------------------------------------------------------------------------------------------------------
THE FLAG FILE 

This challenge is part of the Start Here Dojo, Using the dojo module, where we are building up on previous challenge of finding a flag. The only difference is that this time we are not acting directly as a root user and hence we first need to convert the flag to world-readable using the solve program. 

MY SOLVE FLAG: pwn.college{E3sYTTf4bhoSxB5HxY42UNoBeZe.QX5IzNzwSO3gjNzEzW}

To solve the above, we again navigate to the root using '''cd /''' (we started as /home/hacker). After reaching root, we change directories to challenge by using '''cd challenge'''. In this we list out contents using '''ls''' to find the solve file. We then execute the '''./solve''' command and then use the '''cat /flag''' command to find the required flag. Copying this flag and pasting back onto the flag section in the bar below workarea, we get the completion message. 

WHAT I LEARNED: 

In a normal computer system, there maybe multiple users, and each user or a group of users has a unique combination of permissions and access. The root user is the one who can go anywhere in the system and do anything without any restrictions, so to solve future challenges, I will have to gain access and become a root user in most cases. 

REFERENCES: N/A
----------------------------------------------------------------------------------------------------------------------------------
USING PRIVILEGED MODE 

This challenge is a part of the Start Here dojo, using the dojo module, and here we need to start the challenge as a privileged user and get a secret that we will then use in normal mode to get the actual flag. 

MY SOLVE FLAG: pwn.college{wkCQhteQwO-TEjNZZsa-xr9m_s0.QXwMzNzwSO3gjNzEzW}

To solve this challenge I initially started the challenge in Privileged mode, then I used the '''cd /''' to navigate to root, and then used the '''cd challenge''' to reach the intended directory. Then I used the '''ls''' command to see all the files available in the directory. I tried running '''cat secret''' but it showed me permission denied. After this I re-read the problem statement and found out a mention of '''sudo''', I ended up googling what does sudo mean and how to use it. After reading a bit on sudo, which originally stood for SuperUserDO, I found that '''sudo cat secret''' should allow me to gain access to the contents of the secret file. This worked like a charm and I got a weird looking combination of characters which I copied to my clipboard. Then I changed the mode from privileged user to unprivileged user by using the Lock button next to the fullscreen button at the bottom of the work area. This shifted me back to unprivileged user. I started off in the /home/hacker directory, changed to root using '''cd /''', then moved to /challenge by running '''cd challenge''' and finally ran the solve file using '''./solve''' where it asked me for a password and I entered the password I had copied from the original privileged mode. This gave me the flag I needed. Copying and pasting the flag in the required field, I got the challenge complete message. 

WHAT I LEARNED: 

I learned that certain actions can only be performed by root user or superuser, and to do the commands as a superuser, we use the '''sudo''' command in front of normal commands. This allows us to do a lot of tasks which we would not have been able to do otherwise. 


REFERENCES: 1. https://en.wikipedia.org/wiki/Sudo#:~:text=sudo%20(/su%CB%90du%CB%90,system%20invokes%20the%20requested%20command.
            2. https://www.reddit.com/r/linuxquestions/comments/revbx0/what_does_sudo_mean/
----------------------------------------------------------------------------------------------------------------------------------
PERSISTENT DIRECTORIES - ONE

This is a challenge in the Start Here dojo, Using the Dojo module, where we need to run the program solve to find the instructions. In the instructions we are told to create a leap directory and copy the /challenge/secret file into the leap directory. 

MY SOLVE FLAG: pwn.college{gNVwG0Q0T691vjeZy-Wz3rJ-V6y.QXxMzNzwSO3gjNzEzW}

To solve this problem, I first changed the directory to root by running the '''cd /''' command. Then I navigated to the challenge directory by using '''cd challenge''' and then ran the solve program using '''./solve'''. Here I received the instructions to create a leap directory in the home and having a path of /home/hacker/leap. I did this using the '''cd /home/hacker''' command to navigate to the required directory then using the '''mkdir leap''' command when I was in the /home/hacker directory. Then I was told to copy the file /challenge/secret to /home/hacker/leap which I achieved by first navigating to root using '''cd /''' and then using '''cp /challenge/secret /home/hacker/leap'''. After this I navigated to /challenge directory using '''cd /challenge///''' and then running the solve program using '''./solve'''. This gave me the flag and copying this flag into the flag field in the bar below the work area completed the challenge.


WHAT I LEARNED: 

I learned that the files and directories present in the /home/hacker directory are persistent, meaning that the files and directories we make will stay in the storage for the next tasks as well and we wont need to make these files again.

REFERENCES: N/A
----------------------------------------------------------------------------------------------------------------------------------
PERSISTENT DIRECTORIES - TWO

This is a challenge in the Start Here dojo, Using the Dojo module, where we need to launch the terminal and run the solve program 
to test if a the file we created in the previous challenge exists or not. 

MY SOLVE FLAG: pwn.college{sYX3JgNeJ6q_osn5jJK4FRRYGnf.QXyMzNzwSO3gjNzEzW}

To get the flag, we first change to the root directory by using '''cd /''' command(we started from /home/hacker directory). After changing to the root directory we navigate to challenge directory using '''cd /challenge'''. Here we run the command '''./solve''' to get the flag. We get the flag directly because the file already exists in the /home/hacker directory. 

WHAT I LEARNED: 

I learned that the directories and files we make in the /home/hacker directory are not removed from a system unless we remove them on our own. Also files and directories in other directories like /tmp, /challenge do not get saved. 

REFERENCES: N/A
----------------------------------------------------------------------------------------------------------------------------------
