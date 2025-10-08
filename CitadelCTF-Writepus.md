# Citadel-CTF 
This was a Capture The Flag event organized by Cryptonite from 4th Oct to 8th Oct of 2025. My team was Dedsec and my hacker name was Delta. This was my first CTF and it was a lot of to do it with me teammates, yaml and chill247. We also had a fourth teammate who did not show up. We were finally finished as 46th team and this was quite an enriching experience. The writeups for each individual challenges are provided below.

## Zahard's welcome 
To solve this challenge, we needed to find the first flag which was hidden in the discord server of the Citadel-CTF. 

### Team Solve

- To solve this challenge, my teammate chill247 found the flag in the name tab of rules of discord server. 
- We pasted that flag into the challenge statement to mark our first solve. 


## The Social Network 
This challenge was based on OSINT, and we need to find the flag from both Instagram and X.

### Team solve 

- To solve this challenge, my teammate yaml, found the first half of the flag on the Instagram story itself while I found the second half of the flag in the bio of X account. 

## Omniscient's Flag Metadata 
In this challenge, we needed to find the flag hidden inside another image. 

### Team Solve 
- To solve this challenge, I first used the `exiftool` to get the hint from the files metadata. This hint was that kdj had a habit of hiding image inside an image.
- My teammate yaml then used online tools to get the hidden image inside an image, thus finding the flag. 


## track 8 
To solve this challenge, we needed to decrypt the cipher text given to us. 

### Team Solve
- This was a pretty simple solve where I figured out the name of Panchiko's latest album, and found the track 8 as Vinegar. This pointed to a Vinegere Cipher which my teammate decoded using cyberchef.io 



## Test of sweetness
To solve this challenge, we needed to edit the cookies to let the server read us as an admin. 

### Team Solve
- To solve this challenge, I simply opened Developer Tools by pressing `F12` and then went to Storage tab to access cookies. I did this because it gave us the hint as editing cookies. 
- I then refreshed the site to get the flag. 

## Rotten Apple
To solve this challenge, we needed to change the cipher text. 

### Team Solve 
- To solve this challenge, my teammate yaml, first ran the cipher text through a ROT13 and then ran the result through ROT47 to get the flag. 

## Randomly Accessed Memories
To solve this challenge, we had to go through the history of the commits of a repository.

### Team Solve 
- I simply read through the history of the commits to find the flag. The flag was encoded in base64 format so my teamate, chill247, simply ran it through online decoders and we got the flag.

## Selected Ambient Work 
To solve this challenge, we needed to decode the morse code embedded in the song. 

### Team Solve

- To solve this we first learned how to filter out the morse code from the whole wav file. Using tips from AI tools, we realized we can use `sox` to filter out the morse code out using frequencies. The exact command we ran was `sox challenge.wav output.wav sinc 600-1000`. 
- This command is basically a band pass filter and it allows all sounds from 600 Hz to 1000 Hz to pass through and stores them in output.wav file.
- We then decoded this file to a get a whole description about Richard D James, and in that description, was the flag, I love idm, ofc in leetspeak. 


## The Robot's Trail 
This was a really fun challenge, where we learned about Local File Inclusion Vulnerability. 

### Team Solve
- To solve this challenge, we visited the website and opened Developer Tools to find data. My teammate chill247 found a hidden file, robots.txt which we accessed by directly changing the path of the URL of the website. I'm proud to say I knew about how to do this because of watching youtube videos on this. 
- After going to the robot.txt file, we found another hint which told us /etc/passwd can reveal interesting info.
- Going to /etc/passwd by changing to /file?path=/etc/passwd, we got another hint which told us to check the /var/www/html/config.php:/home/webadmin:/bin/bash. 
- Doing this, we went to another page which told us to check the logs for unusual activity. 
- accessing the log we got another hint which told us that interesting hints may be found at /proc/self/environ. 
- Going to the told directory, we got the secret location as /home/ctf/.secret. here we found the list of all files in the directory, one of which was flag.txt, changing the path to append /flag.txt, we found the flag. 


## Rotting in the deep 100 
In this challenge, we need to reverse the process that has gone into creating the ciphertext. 

### Team Solve
- We first read through the program to understand what it did, once we understood it, we simply reversed those processes, i.e, unshifted and converted bytes back to get the flag. This was done mostly by my teammate yaml.


## Coco Conjecture 100 
To solve this challenge, we needed to create a script which would satisfy the conditions given. 

### Team Solve
- This challenge was mostly solved by my teammate yaml as he had knowledge of python, while I did not. This was the first place where we got stuck because instead of working as a team, we were forced to let yaml work solo while chill247 and I just sat there. 


## Schlagenheim 
To solve this challenge, we need to manipulate headers of the given file. 

### Team Solve
- This challenge turned out to me quite interesting as this was very new to me. We first ran the wav file but did not get any result. We then opened the file in a hex editor to analyze the raw bytes. Most of it was just gibberish, but it gave us on crucial clue, Magic Bytes MIDI. Following through on this hint, we changed the header of the file from MIDI to MThd. 
- We then opened this file using music software which can analyzed MIDI format and got the flag. 

## XOR Slide 
To solve this challenge, we had to use XOR encryption/decryption to get the flag. 

### Team Solve 
- This challenge was a fun challenge where we analyzed the program to get the flag. However because we were stuck on this and wasting time as we solved this at midnight, we simply put it in AI tools and followed the steps given to get the flag. 

## The sound of music 
In this challenge, we needed to find parts of the file in the various websites.

### Team Solve 
- To solve this we first analyzed the challenge statement and then googled up websites where you can give rating to your music and which websites keep track of the last listened to songs. 
- I managed to find the middle part of flag for `citadweller` user on rateyourmusic.com and this also led me to the spotify album where I found the last part of the flag. My teammate yaml found the first part of the flag on last.fm. 

## Echos and pings 
To solve this challenge, we need to find flag hidden in image by first finding the packet which contained image.

### Team Solve 
- I analyzed the packets using Wireshark to figure out which packet had the, I initially thought it was in packet 24, but it wasnt giving any fruitful result. 
- So I googled what are the signature bytes of a file and realised I should look for `ff d8 ff e0`. Then I searched through the raw data and found a file starting with `ff d8 ff e0` but no ending byte. I then searched for the next byte which I found in a different packet. 
- Analyzing those two packets, I found that they were ICMP protocols, so I extracted them to get the file which contained the flag.

## Ripper 
To solve this challenge, we needed to use the `John-the-Ripper` tool to crack the hash. 

### Team Solve 
- I am really proud of being able to solve this on the first attempt itself. The hash given to us was of unknown format, so I asked my teammate to find the hashtype, and he gave it to me as a bcrypt format. 
- Using this data along with the given wordlist to crack the hash, I created a command `john --format=bcrypt filename --wordlist=givenWordlist` 
- I do not really remember the names of the files hence I used the above format where `filename` is the file we want to crack and `givenWordlist` is the wordlist that was available in challenge.
- This gave me the flag, and allowed us to solve this in under 5 mins.

## AetherCorp NetProbeX
To solve this challenge, we needed to first figure out the command separator then the location of the secret. 

### Team Solve
- We were actually stuck on this for the night, and it was only after sleeping and getting back to it did my teammate yaml figure out the command separator `%0A`. Using these to chain commands, we listed out the contents using `ls -a` to find the briefing. 
- However the `cat` command failed so my teammate chill247 found an alternative using `less`. We read the briefing to understand that it lies hidden in AetherCorp network so we used the `find` command to get any data related to aethercorp. 
- Finding the directory in `/var/lib` we listed out contents using `ls -a`. This gave us a few directories, I looked through the archive directory while my teammates looked in others. 
- The flag was in a `.secrets` directory inside the archive which allowed me to find the flag in `blacksite_key.dat` file. 


## Feels like we only go backward
To solve this challenge, we need to solve 3 levels to get the flag. 

### Team Solve
- This was mostly handled by my teammate yaml where he ran this through Ghidra to get the flag. I was not of any help in this. 

## Database Incursion 
To solve this, we needed to manipulate the database and run different commands to find the results.

### Team Solve
- I was able to figure how to terminate the command and comment out whatever was next available in the command, i.e, if we wanted to insert any command, we first had to use `'` to end the previous command and then use `--` to comment out any thing else. 
- My teammates then researched and found out that we could use the `OFFSET` to get the data of other people available in the database. Using this yaml crafted a command which allowed us to find password from Kiwi of Management. 


## Bratcha 
To solve this challenge, we needed to figure out the correct pastebin.

### Team Solve
- I first figured out that we had total 256 combinations possible out of which, one is a valid pastebin. Using this I told AI tools to craft all possible links. 
- Creating these links, I sent them to my teammate chill247 who was able to find the correct link which gave us the flag. 


## A Memory's a Heavy Burden
To solve this challenge, we needed to find out what is the exact coordinates of the photo. 

### Team solve 
- My teammate chill247 found out it was in Japan by directly looking at the picture, I used the `exiftool` to try and find the exact location. 
- I was not able to get the actual location as the coordinates I entered the first time failed. 
- My teammate yaml then found the actual coordinates by using google maps to find the temple. 


## Case Sensitivity 
To solve this challenge, we needed to find the password in this python jail. 

### Team Solve
- Happy to say that despite not knowing python, I was able to figure out that `print`, and `FLAG` had to be involved in the solution somehow by trying them out and getting the `..(althought print is close)` error.
- I gave these clues to my friend yaml who then sat and worked and figured out the `exec` as well as `lower` function. He then crafted a command, `exec("PRINT(ENVIRON".lower() + "['FLAG'])"` to get the flag.

## Viral Bionic Anomaly 
**This challenge was solved by my teammates as I had classes on Monday for the whole day and I was not able to contribute at all** 
