# Comprehending Commands 

## Challenge 1: Cat:not the pet, the Command
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands module,* we are introduced to the `cat` command which allows us to print out the results of the file onto the terminal. 

## My Solve:

**Flag:** `pwn.college{wVx5lsHCFqOtNix_3drW1eCWxwb.QXxcTN0wSO3gjNzEzW}`

To solve this, I used the `ls` command to first confirm the location of the flag file and then ran the `cat flag` command to get the flag.
 


```bash
hacker@commands~cat-not-the-pet-but-the-command:~$ ls
Desktop  flag  not-the-flag
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{wVx5lsHCFqOtNix_3drW1eCWxwb.QXxcTN0wSO3gjNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$ 
```
## What I learned: 
I learned about the usage of the `cat` command to get the contents of any file existing on our system. 

## References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 2: Catting absolute paths 
In this challenge of *Linux Luminarium Dojo, Comprehending Commands Module,* we need to find the flag by using `cat` command along with absolute paths. 

## My Solve

**Flag:** `pwn.college{8qcOPmtAl2xVS4gnRTykSxUWOe1.QX5ETO0wSO3gjNzEzW}`

To solve this, I simply ran the `cat /flag` command as mentioned in the challenge to get the flag. 

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{8qcOPmtAl2xVS4gnRTykSxUWOe1.QX5ETO0wSO3gjNzEzW}
hacker@commands~catting-absolute-paths:~$ 
```

## What I learned 
I learned that `cat` command can be used along with absolute paths to get the contents of any file from anywhere in the file system. 

## References: N/A 
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 3: more catting practice 
In this challenge of *Linux Luminarium Dojo, Comprehending Commands Module,* we need to find the flag by using `cat` command along with the path of the directory which we need to find. 

## My Solve

**Flag:** `pwn.college{8fIsjqU1zlbc-gT-CFvu7SHFbeJ.QXwITO0wSO3gjNzEzW}`

To solve this problem, I first started the challenge which gave me the directory in which I needed to scavenge, so I simply used the `cat` command along with the directory path to get the flag. 

```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/dict/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/dict/flag
pwn.college{8fIsjqU1zlbc-gT-CFvu7SHFbeJ.QXwITO0wSO3gjNzEzW}
hacker@commands~more-catting-practice:~$ 
```

## What I learned 
This was an extension of the previous challenge, which further fortified the working of the `cat` command for me. 

## References: N/A
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 4: Grepping for a needle in a haystack
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module,* we need to find the flag by using `grep` to search for the useful content of a file which contains thousands of lines of text. 

## My Solve 

**Flag:** `pwn.college{Yxe6DWTGXUQwjFdK6jaWgTD2pic.QX3EDO0wSO3gjNzEzW}`

To solve this challenge, I used the hint given in the challenge itself(every key starts with 'pwn.college'). So I used the `grep` command along with an argument of `pwn.college` and the file path as `/challenge/data.txt` as given in the question. 

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{Yxe6DWTGXUQwjFdK6jaWgTD2pic.QX3EDO0wSO3gjNzEzW}
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ 
```

## What I learned 
I learned about a command which I know is going to be very useful to filter out data in any event. This grep command will make it very easy to find specific keywords in a collection of files present on our file system. 

## References 
- Hint give in the question itself 
-----------------------------------------------------------------------------------------------------------------------------------
## Challenge 5: Comparing files 
In this challenge of *Linux Luminarium Dojo, Comprehending Commands module,* we are taught about the `diff` command and asked to use it to find a flag by comparing two similar files. 

## My Solve 

**Flag:** `pwn.college{sznTGQUSiYaBl8eua5552l6qMke.01MwMDOxwSO3gjNzEzW}`

To solve this problem I simply ran the `diff` command along with the two file `/challenge/decoys_only.txt` and `/challenges/decoys_and _real.txt` to find the difference. 

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
36a37
> pwn.college{sznTGQUSiYaBl8eua5552l6qMke.01MwMDOxwSO3gjNzEzW}
hacker@commands~comparing-files:~$ 
```

## What I learned
This was actually a challenge which took me a while to solve as I wanted to understand what does `36a37` actually mean. I read up the challenge again after a short break and I understood that the line actually stood for 'after line 36, file 1 add line 37 of file 2'. I read up on the similar `2c2` result as well and found it that it means 'line 2 in file 1, changed line 2 in file 2'. This was a new thing which I have never come across before. 

## References 
- https://unix.stackexchange.com/questions/81998/understanding-of-diff-output - for understanding `diff` output. 
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 6: Listing Files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands module,* we are taught about the `ls` command and how to list all the files present in a directory to find the file we want. 

## My Solve 

**Flag:** `pwn.college{s0id-2NG1hPMLM3ErNtacmlfcqo.QX4IDO0wSO3gjNzEzW}`

To solve this challenge, I simply used the `ls` command with the argument of `/challenge` directory to get the result. After finding out the name, I tried running `cat /challenge/20282-renamed-run-18426` which gave me an error as shown below, so I changed it to run the program instead using `/challenge/20282-renamed-run-18426` command. This gave me the intended result. 

```
hacker@commands~listing-files:~$ ls /challenge
20283-renamed-run-18426  DESCRIPTION.md
hacker@commands~listing-files:~$ cat /challenge/20283-renamed-run-18426
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
hacker@commands~listing-files:~$  /challenge/20283-renamed-run-18426
Yahaha, you found me! Here is your flag:
pwn.college{s0id-2NG1hPMLM3ErNtacmlfcqo.QX4IDO0wSO3gjNzEzW}
hacker@commands~listing-files:~$ 
```

## What I learned 
In this challenge I learned that the `ls` command can be used with any directory path to print the elements of a directory on the terminal. 

## References: N/A 
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 7: Touching files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands module*, we are taught how to create files using the `touch` command and need to create two files `/tmp/pwn` and `/tmp/college`. 

## My solve 

**Flag:** `pwn.college{0W3rnTKLtI5_CtIbzlz0IMWV4OT.QXwMDO0wSO3gjNzEzW}`

To solve this I simply used the `touch` command along with directory paths to make both the files. Then I run the `/challenge/run` command to get the flag. 

```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{0W3rnTKLtI5_CtIbzlz0IMWV4OT.QXwMDO0wSO3gjNzEzW}
hacker@commands~touching-files:~$ 
```

## What I learned 
In this challenge I learned how to create a file in any directory I want by using the `touch` command along with the directory path. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 8: Removing files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module,* we need to learn how to remove files using the `rm` command. 

## My Solve

**Flag:** `pwn.college{0Sqs1hk7JvKsZ-fCg3RMxRUBuNd.QX2kDM1wSO3gjNzEzW}`

To solve this, I first ran the `ls` command to find the result and then deleted the required file using the `rm` command. After this I ran the `/challenge/check` command to get the flag. 

```
acker@commands~removing-files:~$ ls
Desktop  delete_me  not-the-flag
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{0Sqs1hk7JvKsZ-fCg3RMxRUBuNd.QX2kDM1wSO3gjNzEzW}
hacker@commands~removing-files:~$
```

## What I learned 
In this challenge I learned how to remove existing files in the file system using the `rm` command. This can be useful once we get a lot of extra files on our system that we do not require. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 9: Moving files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module,* we need to move a file from the root to a specific directory using the `mv` command. 

## My Solve 

**Flag:** `pwn.college{shIrAFpeRTS-xNO6DulIDJvbVGV.0VOxEzNxwSO3gjNzEzW}`

For solving this challenge I simply followed the process given in the question that tells us to move the `/flag` file to the `/tmp/hack-the-planet` directory. After moving it, I run the `/challenge/check` to get the flag. 

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{shIrAFpeRTS-xNO6DulIDJvbVGV.0VOxEzNxwSO3gjNzEzW}

hacker@commands~moving-files:~$ 
```

## What I learned 
I learned how to move files from one directory to another directory in the file system using the `mv` command. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 10: Hidden files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module,* we need to figure out how to print the hidden files in a directory using an argument `-a` along with `ls` command. 

## My Solve 

**Flag:** `pwn.college{E_SNdOEGOlBmFv_RzxINRb8uWVW.QXwUDO0wSO3gjNzEzW}`

To solve this challenge, I simply used the `ls` command with the needed arguments to get the resultant flag. 

```
hacker@commands~hidden-files:~$ ls / -a
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-269362888515672  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat .flag-269362888515672
cat: .flag-269362888515672: No such file or directory
hacker@commands~hidden-files:~$ cat /.flag-269362888515672
pwn.college{E_SNdOEGOlBmFv_RzxINRb8uWVW.QXwUDO0wSO3gjNzEzW}
hacker@commands~hidden-files:~$ 
```

## What I learned 
I learned that we need to always check every directory using `ls -a` command to find juicy details which might be hidden in that directory. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 11: An Epic File system quest 
In this challenge of *Linux Luminarium Dojo, Comprehending Commands Module,* we need to use all the commands we have learned so far to find the flag. 

## My Solve

**Flag:** `pwn.college{kUju1XuvmNWX1Kuc1rdKV2arsF0.QX5IDO0wSO3gjNzEzW}`

To solve this process, we had multiple steps which are listed as below: 
- We first navigate to the root directory and look around there to find any hidden clues or traces. 
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  TRACE       boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cat TRACE
Congratulations, you found the clue!
The next clue is in: /opt/linux/linux-5.4/arch/arm/plat-orion/include

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ 
```

- For the next step in the run, we change the directory to what we found out. 

```bash
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/arch/arm/plat-orion/include
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/plat-orion/include$ ls -a
.  ..  POINTER  plat
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/plat-orion/include$ cat POINTER
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/networkx/algorithms

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/plat-orion/include$ 
```
- For the next step, we change our cwd to the one found in the previous step. 

```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/plat-orion/include$ cd /usr/lib/python3/dist-packages/networkx/algorithms
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/networkx/algorithms$ ls -a
.              chains.py               cycles.py               isolate.py                  planar_drawing.py   tests
..             chordal.py              dag.py                  isomorphism                 planarity.py        threshold.py
MESSAGE        clique.py               distance_measures.py    link_analysis               reciprocity.py      tournament.py
__init__.py    cluster.py              distance_regular.py     link_prediction.py          richclub.py         traversal
__pycache__    coloring                dominance.py            lowest_common_ancestors.py  shortest_paths      tree
approximation  communicability_alg.py  dominating.py           matching.py                 similarity.py       triads.py
assortativity  community               efficiency_measures.py  minors.py                   simple_paths.py     vitality.py
asteroidal.py  components              euler.py                mis.py                      smallworld.py       voronoi.py
bipartite      connectivity            flow                    moral.py                    smetric.py          wiener.py
boundary.py    core.py                 graphical.py            node_classification         sparsifiers.py
bridges.py     covering.py             hierarchy.py            non_randomness.py           structuralholes.py
centrality     cuts.py                 hybrid.py               operators                   swap.py
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/networkx/algorithms$ cat MESSAGE
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/networkx/algorithms$ 
```
- For the next step, we change our cwd to the one found in the previous step. 

```
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/networkx/algorithms$ cd /opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ ls -a
.  ..  GIST  arch-support.txt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ cat GIST
Great sleuthing!
The next clue is in: /usr/share/racket/pkgs/srfi-lib/srfi/%3a39

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ 
```

- Following up on the instructions given above about self destruction, we list the contents using `ls` without changing our cwd. 

```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ ls -a /usr/share/racket/pkgs/srfi-lib/srfi/%3a39
.  ..  SECRET-TRAPPED  compiled  parameters.rkt
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ cat /usr/share/racket/pkgs/srfi-lib/srfi/%3a39/SECRET-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/Size7/Regular

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ 
```

- Again following the instructions of self destruction, we list out contents using `ls -a` command. 

```bash 
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ ls -a /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/Size7/Regular
.  ..  LEAD-TRAPPED  Main.js
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ cat /usr/share/javascript/mathjax/unpacked/jax/output/SVG/fonts/Latin-Modern/Size7/Regular/LEAD-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/X11/locale/iso8859-9

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ 
```

- Changing our cwd to the new one, we get 

```bash 
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/Documentation/features/vm/ioremap_prot$ cd /usr/share/X11/locale/iso8859-9
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/iso8859-9$ ls -a
.  ..  .ALERT  Compose  XI18N_OBJS  XLC_LOCALE
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/iso8859-9$ cat ./.ALERT
Tubular find!
The next clue is in: /usr/share/cmake-3.16/Modules/Compiler

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/iso8859-9$ 
```

- Changing our cwd to the new one, we get 

```bash
hacker@commands~an-epic-filesystem-quest:/usr/share/X11/locale/iso8859-9$ cd /usr/share/cmake-3.16/Modules/Compiler
hacker@commands~an-epic-filesystem-quest:/usr/share/cmake-3.16/Modules/Compiler$ ls -a
.                                      Flang-FindBinUtils.cmake                   PGI-Fortran.cmake
..                                     Flang-Fortran.cmake                        PGI.cmake
.INSIGHT                               Fujitsu-DetermineCompiler.cmake            PathScale-C.cmake
ADSP-DetermineCompiler.cmake           G95-Fortran.cmake                          PathScale-CXX.cmake
ARMCC-ASM.cmake                        GHS-C.cmake                                PathScale-DetermineCompiler.cmake
ARMCC-C.cmake                          GHS-CXX.cmake                              PathScale-Fortran.cmake
ARMCC-CXX.cmake                        GHS-DetermineCompiler.cmake                PathScale.cmake
ARMCC-DetermineCompiler.cmake          GHS.cmake                                  QCC-ASM.cmake
ARMCC.cmake                            GNU-ASM.cmake                              QCC-C-FeatureTests.cmake
ARMClang-ASM.cmake                     GNU-C-DetermineCompiler.cmake              QCC-C.cmake
ARMClang-C-FeatureTests.cmake          GNU-C-FeatureTests.cmake                   QCC-CXX-FeatureTests.cmake
ARMClang-C.cmake                       GNU-C.cmake                                QCC-CXX.cmake
ARMClang-CXX-FeatureTests.cmake        GNU-CXX-DetermineCompiler.cmake            QCC.cmake
ARMClang-CXX.cmake                     GNU-CXX-FeatureTests.cmake                 SCO-C.cmake
ARMClang-DetermineCompiler.cmake       GNU-CXX.cmake                              SCO-CXX.cmake
ARMClang.cmake                         GNU-FindBinUtils.cmake                     SCO-DetermineCompiler.cmake
Absoft-Fortran.cmake                   GNU-Fortran.cmake                          SCO.cmake
AppleClang-ASM.cmake                   GNU-OBJC.cmake                             SDCC-C-DetermineCompiler.cmake
AppleClang-C-FeatureTests.cmake        GNU-OBJCXX.cmake                           SunPro-ASM.cmake
AppleClang-C.cmake                     GNU.cmake                                  SunPro-C-DetermineCompiler.cmake
AppleClang-CXX-FeatureTests.cmake      HP-ASM.cmake                               SunPro-C-FeatureTests.cmake
AppleClang-CXX.cmake                   HP-C-DetermineCompiler.cmake               SunPro-C.cmake
AppleClang-DetermineCompiler.cmake     HP-C.cmake                                 SunPro-CXX-DetermineCompiler.cmake
AppleClang-OBJC.cmake                  HP-CXX-DetermineCompiler.cmake             SunPro-CXX-FeatureTests.cmake
AppleClang-OBJCXX.cmake                HP-CXX.cmake                               SunPro-CXX.cmake
Borland-DetermineCompiler.cmake        HP-Fortran.cmake                           SunPro-Fortran.cmake
Bruce-C-DetermineCompiler.cmake        IAR-ASM.cmake                              SunPro.cmake
Bruce-C.cmake                          IAR-C.cmake                                TI-ASM.cmake
CCur-Fortran.cmake                     IAR-CXX.cmake                              TI-C.cmake
CMakeCommonCompilerMacros.cmake        IAR-DetermineCompiler.cmake                TI-CXX.cmake
Clang-ASM.cmake                        IAR-FindBinUtils.cmake                     TI-DetermineCompiler.cmake
Clang-C-FeatureTests.cmake             IAR.cmake                                  TinyCC-C-DetermineCompiler.cmake
Clang-C.cmake                          IBMCPP-C-DetermineVersionInternal.cmake    TinyCC-C.cmake
Clang-CXX-FeatureTests.cmake           IBMCPP-CXX-DetermineVersionInternal.cmake  VisualAge-C-DetermineCompiler.cmake
Clang-CXX-TestableFeatures.cmake       Intel-ASM.cmake                            VisualAge-C.cmake
Clang-CXX.cmake                        Intel-C-FeatureTests.cmake                 VisualAge-CXX-DetermineCompiler.cmake
Clang-DetermineCompiler.cmake          Intel-C.cmake                              VisualAge-CXX.cmake
Clang-DetermineCompilerInternal.cmake  Intel-CXX-FeatureTests.cmake               VisualAge-Fortran.cmake
Clang-FindBinUtils.cmake               Intel-CXX.cmake                            Watcom-DetermineCompiler.cmake
Clang-OBJC.cmake                       Intel-DetermineCompiler.cmake              XL-ASM.cmake
Clang-OBJCXX.cmake                     Intel-Fortran.cmake                        XL-C-DetermineCompiler.cmake
Clang.cmake                            Intel.cmake                                XL-C.cmake
Comeau-CXX-DetermineCompiler.cmake     MSVC-ASM.cmake                             XL-CXX-DetermineCompiler.cmake
Compaq-C-DetermineCompiler.cmake       MSVC-C-FeatureTests.cmake                  XL-CXX.cmake
Compaq-CXX-DetermineCompiler.cmake     MSVC-C.cmake                               XL-Fortran.cmake
Cray-C.cmake                           MSVC-CXX-FeatureTests.cmake                XL.cmake
Cray-CXX.cmake                         MSVC-CXX.cmake                             XLClang-C-DetermineCompiler.cmake
Cray-DetermineCompiler.cmake           MSVC-DetermineCompiler.cmake               XLClang-C.cmake
Cray-Fortran.cmake                     NAG-Fortran.cmake                          XLClang-CXX-DetermineCompiler.cmake
Cray.cmake                             NVIDIA-CUDA.cmake                          XLClang-CXX.cmake
CrayPrgEnv-C.cmake                     NVIDIA-DetermineCompiler.cmake             XLClang.cmake
CrayPrgEnv-CXX.cmake                   OpenWatcom-DetermineCompiler.cmake         zOS-C-DetermineCompiler.cmake
CrayPrgEnv-Fortran.cmake               PGI-C.cmake                                zOS-CXX-DetermineCompiler.cmake
CrayPrgEnv.cmake                       PGI-CXX.cmake
Embarcadero-DetermineCompiler.cmake    PGI-DetermineCompiler.cmake
hacker@commands~an-epic-filesystem-quest:/usr/share/cmake-3.16/Modules/Compiler$ cat .INSIGHT
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/include/linux/phy/tegra
hacker@commands~an-epic-filesystem-quest:/usr/share/cmake-3.16/Modules/Compiler$
```

- Changing our cwd to the new one, we get 

```bash 
hacker@commands~an-epic-filesystem-quest:/usr/share/cmake-3.16/Modules/Compiler$ cd /opt/linux/linux-5.4/include/linux/phy/tegra
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/phy/tegra$ ls -a]
ls: invalid option -- ']'
Try 'ls --help' for more information.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/phy/tegra$ ls -a
.  ..  SPOILER  xusb.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/phy/tegra$ cat SPOILER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{kUju1XuvmNWX1Kuc1rdKV2arsF0.QX5IDO0wSO3gjNzEzW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/linux/phy/tegra$
```

## What I learned 
In this challenge I learned that sometimes you need to be patient and follow every trail to get to the final result. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 12: Making directories 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module,* we need to make a directory and create a file in it, then run the `/challenge/run` to get the flag 

## My Solve 

**Flag:** `pwn.college{EXIwcRGAhth1A-mwWVi8bP9NHjI.QXxMDO0wSO3gjNzEzW}`

To solve this, I first ran the command to create a file using `mkdir` then I created a file using the `touch` command. 

```bash 
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{EXIwcRGAhth1A-mwWVi8bP9NHjI.QXxMDO0wSO3gjNzEzW}
hacker@commands~making-directories:~$ 
```

## What I learned 
From this challenge, I learned how to make a directory in the file system using the `mkdir` command. 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 13: Finding Files
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands Module* we need to find a file using the `find` command to get the final flag. 

## My Solve 

**Flag:** `pwn.college{EE48NFwFJeVwXstbnX03wCiNm9V.QXyMDO0wSO3gjNzEzW}`

To solve this I ran the `find` command with proper arguments first, then used `cat` on each file. 

```bash 
hacker@commands~finding-files:~$ find / -name flag
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/share/racket/pkgs/srfi-lib/srfi/54/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/root’: Permission denied
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/nix/store/ka6xbd6z6wj5d6frl7ym4nzfc6p2wkdx-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/f31j0igg7ms3yrj5gm3cm76bjcmdl8w5-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/7ns27apnvn4qj4q5c82x0z1lzixrz47p-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/5z3sjp9r463i3siif58hq5wj5jmy5m98-python3.12-pwntools-4.13.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/n6vb30rd7kkwjj595pgm0dmsmfaqi6i5-rizin-0.7.3/share/rizin/flag
/nix/store/5n5lp1m8gilgrsriv1f2z0jdjk50ypcn-rizin-0.7.3/share/rizin/flag
/nix/store/bnlabj2vsbljhp597ir29l51nrqhm89w-rizin-0.7.4/share/rizin/flag
/nix/store/s8b49lb0pqwvw0c6kgjbxdwxcv2bp0x4-radare2-5.9.8/share/radare2/5.9.8/flag
/nix/store/8qvj9mzdq2qxgjigw4ysqgbkcx1zi80y-python3.13-pwntools-4.14.1/lib/python3.13/site-packages/pwnlib/flag
/nix/store/1hyxipvwpdpcxw90l5pq1nvd6s6jdi5m-python3.12-pwntools-4.14.1/lib/python3.12/site-packages/pwnlib/flag
/nix/store/dz2qxywk6d8hc1gkarpwbhyxb50sh2ak-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/share/racket/pkgs/srfi-lib/srfi/54/flag
pwn.college{EE48NFwFJeVwXstbnX03wCiNm9V.QXyMDO0wSO3gjNzEzW}hacker@commands~finding-files:~$ 
```

## What I learned 
Patience is sometimes my best bet, because if I am not patient, I might pivot even when I am on the right track 

## References: N/A
----------------------------------------------------------------------------------------------------------------------------------
## Challenge 14: Linking Files 
In this challenge of the *Linux Luminarium Dojo, Comprehending Commands module,* we need to link a particular file to another file because the `/challenge/catflag` reads that particular file only. 

## My solve 

**Flag:** `pwn.college{IM4Qy_q6_zui9E9tbVP0KMy9yce.QX5ETN1wSO3gjNzEzW}`

To complete this challenge, I used the `ln -s` command to link the flag file to the needed file, then I ran the `/challenge/catflag` to get the flag 

```bash 
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
hacker@commands~linking-files:~$
```

## What I learned 
I learned a new thing today, which was how to symbolically link files to other files. This was a new thing and very interesting to learn. I also learned that there are two types of links, hard links and soft links, with hard links linking directly to the memory address of the file, while soft links go through the file. 

## References 
- Took help from mentor because of symbolic link issues.
----------------------------------------------------------------------------------------------------------------------------------

