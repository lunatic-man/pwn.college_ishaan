# Data Manipulation 

## Challenge 1: Translating characters 
In this challenge of the *Linux Luminarium Dojo, Data Manipulation Module,* we are taught about the `tr` command which stands for translate and how to use it. 

## My solve

**Flag:** `pwn.college{oxp41oD_K6IKNYM2hd9DEf7nV3q.01MxEzNxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- To understand more about `tr` command and what arguments it can take, I first opened and ran the Manual page of the command. I did this because I was not going to manually type out the entire alphabet in uppercase and then in lowercase. I found the argument that I wanted. 

```bash

hacker@data~translating-characters:~$ man tr more

.
.
.
       \v     vertical tab

       CHAR1-CHAR2
              all characters from CHAR1 to CHAR2 in ascending order

       [CHAR*]
              in SET2, copies of CHAR until length of SET1
.
.
.
```
- Using the `CHAR1-CHAR2` argument, I ran the `/challenge/run | tr A-Z a-z` command to toggle all the upper case alphabet to lowercase. However, the flag that I got was wrong as it did not convert the lower case letters to upper case. I realized this after trying the flag I found in the flag field below work area and getting incorrect as the alert. 

```bash
hacker@data~translating-characters:~$ /challenge/run | tr A-Z a-z
your case-swapped flag:
pwn.college{oxp41od_k6iknym2hd9def7nv3q.01mxeznxwso3gjnzezw}

hacker@data~translating-characters:~$
```
- I then went online to read about how to craft a toggle case command using the `tr` command as I was not able to find any more useful information on the manual page of the `tr` command. After a bit of searching, I came across the command which would allow me to simultaneously switch from upper to lower and lower to upper cases. This command was `tr 'A-Za-z' a-zA-Z'`. This command allows us to switch the cases in one go. Running the command, I found the correct flag. 

```bash 
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{oxp41oD_K6IKNYM2hd9DEf7nV3q.01MxEzNxwSO3gjNzEzW}

hacker@data~translating-characters:~$
```

## What I learned 
From this challenge, I learned about the usage of the `tr` command and how to pass multiple sets as the argument for the command. 

## References

- https://stackoverflow.com/questions/23178769/unix-tr-command-to-convert-lower-case-to-upper-and-upper-to-lower-case
- https://pwn.college/linux-luminarium/data/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Deleting Characters 
In this challenge of the *Linux Luminarium Dojo, Data Manipulation Module,* we need to delete the extra characters in the flag(% and ^) by using the `-d` parameter with the necessary arguments. 


## My solve 

**Flag:** `pwn.college{0KMd9q8ewTRJRjAO70QTY4RzPe9.0FNxEzNxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 

- I simply crafted a command as per the challenge requirements, the command being `/challenge/run | tr -d %^`. This command removed any extra characters and gave me the flag as needed. 

```bash
hacker@data~deleting-characters:~$ /challenge/run | tr -d %^
Your character-stuffed flag:
pwn.college{0KMd9q8ewTRJRjAO70QTY4RzPe9.0FNxEzNxwSO3gjNzEzW}
hacker@data~deleting-characters:~$
```

## What I learned 
From this challenge, I learned about the usage of the `-d` argument in the `tr` command to remove certain characters as per our wish. 

## References
- https://pwn.college/linux-luminarium/data/
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: Deleting Newlines 
In this challenge of the *Linux Luminarium Dojo, Data Manipulation module,* we need to delete the newline characters and figure out the correct flag after deleting the the new lines. 

## My solve 

**Flag:** `pwn.college{0N_PzOiqiiR0me9g611mOZme9CN.0VNxEzNxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply ran the `/challenge/run | tr -d "\n"` command as per the question to get the flag without any extra newlines. 

```bash 
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{0N_PzOiqiiR0me9g611mOZme9CN.0VNxEzNxwSO3gjNzEzW}hacker@data~deleting-newlines:~$
```

## What I learned 
From this challenge, I learned about the existence of standins and how we can also pass standins as an argument to the `-d` argument of the `tr` command. 

## References 
- https://pwn.college/linux-luminarium/data/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Extracting the first lines with head 
In this challenge of the *Linux Luminarium dojo, Data Manipulation Module,* we need to use the `head` command along with pipes to send the first 7 lines of one program to another program. 

## My solve 

**Flag:** `pwn.college{wKI3lefKaDuQxcCHpJ2Ms4DaLGk.0lNxEzNxwSO3gjNzEzW}` 

To solve this challenge, I followed the steps as listed below: 
- I simply crafted a command as per the instructions given in the challenge, the command being `/challenge/pwn | head -n 7 | /challenge/college`. This command is used to select the first 7 lines from the `/challenge/pwn` program's output and send them to `/challenge/college` program. 

```bash 
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{wKI3lefKaDuQxcCHpJ2Ms4DaLGk.0lNxEzNxwSO3gjNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$

```

## What I learned 
From this challenge, I learned the usage of the `head` command to select only the starting few lines of data of any program and use them for further operations. 

## References 
- https://pwn.college/linux-luminarium/data/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Extracting specific sections of text 
In this challenge of the *Linux Luminarium dojo, Data manipulation module,* we need to select particular columns from the output of the program, and then remove extra newline standins to get the flag in proper format. 

## My Solve 

**Flag:** `pwn.college{AOFhjdATTg91rn6YVhOudK8wMJh.01NxEzNxwSO3gjNzEzW}`

To solve this challenge, I followed the steps as listed below: 
- I first ran the `/challenge/run` command to find out the columns and the columns delimiter.
- A very massive hint was given the in the question itself where they told us how to craft our command. Following that blueprint, I created a command `/challenge/run | cut -d " " -f 1 | tr -d "\n"`. 
- On running the above command, I got the result as follows: 

```bash 
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
18334 p
4846 w
31321 n
6374 .
13062 c
21812 o
25051 l
10164 l
11520 e
28071 g
28668 e
5577 {
17487 A
15847 O
6244 F
28762 h
10410 j
20096 d
14612 A
32686 T
2583 T
8344 g
5354 9
11490 1
20809 r
14820 n
10216 6
12723 Y
2961 V
27576 h
7836 O
6012 u
28901 d
534 K
6716 8
30927 w
25605 M
14770 J
5738 h
12210 .
31502 0
558 1
22549 N
26886 x
11796 E
24562 z
14518 N
25499 x
28736 w
3352 S
10623 O
30953 3
10146 g
5691 j
15255 N
27774 z
1318 E
12644 z
10820 W
22111 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 1 | tr -d "\n" 
2603129808258881697530934156263157429365259503262254287046532517593135014877262383083118432749325621205063383218741360918601237631053258611604327597841225159257402152311435577630605201081606544825492148652674125501274183931083929989856129711301197911168432819595291022618636998415hacker@data~extracting-specific-sections-of-text:~$
```

- I got a bit confused about the result as I was sure that I had crafted the right command, but I realized that columns start from 1, not 0 as is the case in a few programming languages. To get the correct answer, I changed my `-f 1` to `-f 2` and got the correct flag as shown below: 

```bash 
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n" 
pwn.college{AOFhjdATTg91rn6YVhOudK8wMJh.01NxEzNxwSO3gjNzEzW}hacker@data~extracting-specific-sections-of-text:~$

```

## What I learned 
From this challenge, I learned about the usage of the `cut` command along with the needed arguments to filter out the columns on the basis of their numbering. I also realized from this challenge, that with the usage of `head`, `tail` and `cut` command, we can find any value in a text file. 

## References 
- https://pwn.college/linux-luminarium/data/
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Sorting data 
In this challenge of the *Linux Luminarium Dojo, Data Manipulation module,* we need to find the correct flag by sorting the data available in the text file in arranging order and then getting the last value. 

## My solve

**Flag:** `pwn.college{8zMPY5aSS8qRd6s2twxNJv2Jc6J.0FM0MDOxwSO3gjNzEzW}` 

To solve the above challenge, I followed the steps as listed below: 
- I first read through the question to understand what exactly sort does. Then on reading the question, I realized that they want us to find only the last value in all the data when arranged in ascending order, and this last value is our flag. 
- Following the above logic, I crafted a command `sort /challenge/flag.txt | tail -n 1`. This command first sorts all the data in alphabetical order, using the `sort` command. I then pipe the data to the `tail` command with necessary arguments to get only the last value, which is our flag. 

```bash 
hacker@data~sorting-data:~$ sort  /challenge/flags.txt | tail -n 1
pwn.college{8zMPY5aSS8qRd6s2twxNJv2Jc6J.0FM0MDOxwSO3gjNzEzW}
hacker@data~sorting-data:~$

```

## What I learned 
From this challenge I learned about the usage of the `sort` command to arrange data in ascending or descending order, either alphabetically or numerically. This will make it easier for us to select values from a random data set. 

## References 
- https://pwn.college/linux-luminarium/data/
----------------------------------------------------------------------------------------------------------------------------------
