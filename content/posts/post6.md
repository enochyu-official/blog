---
author: Enoch Yu
title: "OverTheWire Bandit: Level 0-4"
date: 2026-01-06
categories: ["Computer Science"]
tags: ["OverTheWire Bandit"]
---

One of the most recommended way to learn Linux commands and basics in CTF is completing [Bandit](https://overthewire.org/wargames/bandit/) from [OverTheWire](https://overthewire.org/wargames/). Therefore, I decided to complete this challenge first before any other CTF challenges. Here, I am planning to share task, my approach, and lessons that I learned from each level. Moreover, I sincerely wish to express my gratitude towards the developers of this platform! Then, let's get started!

## Level 0
### Task
Below is the task for [Level 0](https://overthewire.org/wargames/bandit/bandit0.html).

> Log into the game using SSH with the host to bandit.labs.overthewire.org on port 2220. The given username and the password is bandit0 and bandit0 respectively.

### My Solution
SSH, which stand for Secure Shell, is a cryptographic network protocol that ensures secure connections between remote devices over unsecure network.

By reading through `man ssh`, I was able to know that `-p` is a flag that will allow me to connect on a port. Therefore, I ran the following command.
```
ssh bandit.labs.overthewire.org -p 2220
```
However, I realized that I need to utilize the username *bandit0*. Therefore, I tried the following command.
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
After typing in the password, I was able to join the game.

### Takeaways
SSH is a protocol that allows encrypted connections between remote devices. With flag `-p`, connection on a desired port is possible.


## Level 1
### Task
Below is the task for [Level 1](https://overthewire.org/wargames/bandit/bandit1.html).

> Find the password that is stored in a file named "readme" in the home directory.

### My Solution
As a NeoVim user, I realized that `ls -a` will help me find the password. After locating the file, I ran
```
cat readme
```
to display the content of the file in terminal. As you probably have guessed, `nano readme` works too!

With the password, I was able to login to the next level.

### Takeaways
`ls` is a command to list the files in the directory. Moreover, `cat file` will display the content of the file named "file" in terminal.


## Level 2
### Task
Below is the task for [Level 2](https://overthewire.org/wargames/bandit/bandit2.html).

> Find the password that is stored in a file named "-" in the home directory.

### My Solution
Similar to Level 1, I used `ls` to display the visible files. However, `cat -` did not work this time as it started with a dash. Therefore, I explicitly identified the file with the following command.
```
cat ./-
```
With the password, I was able to move on to the next level.

### Takeaways
A file with a name that starts with a dash needs different approach when reading with `cat` as `-` will consider the file name as a flag. When using commands to open or read a file that starts with a dash, we must explicitly identify the file to prevent it being recognized as an option.


## Level 3
### Task
Below is the task for [Level 3](https://overthewire.org/wargames/bandit/bandit3.html).

> Find the password that is stored in a file name "-- spaces in this filename --" in the home directory.

### My Solution
In command line, either quotations or backslash `\` is required to use space in name of a file. Therefore, both
```
cat ./"-- spaces in this filename --"
cat ./--\ spaces\ in\ this\ filename--
```
gives the password.

### Takeaways
When opening or reading a file that starts with a dash, `cat "-"` is not valid as the dash is still considered as a standard input. Moreover, a backslash or quotations are required to properly read a file with spaces in the name.


## Level 4
### Task
Below is the task for [Level 4](https://overthewire.org/wargames/bandit/bandit4.html).

> Find the password that is stored in a hidden file in the "inhere" directory.

### My Solution
To list the hidden files with the name that start with a period, I decided to utilize `ls` with flag `-a`. After running `ls -a`, I was able to find a folder named "inhere". To check the contents inside the file,
```
ls -a inhere
```
was executed, which listed a file named "...Hiding-From-You". To access the contents inside the file, I ran the following commend in order.
```
cd inhere
cat ...Hiding-From-You
```
With the password, I was able to move on to the next level.

### Takeaways
`ls -a` will list all files in the directory. Moreover, a file with a name that starts with a period will be hidden.


These were my solutions for Bandit Level 0 to 4. Please look forward to my future posts!!

{{< comments-note >}}

