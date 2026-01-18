---
author: Enoch Yu
title: "OverTheWire Bandit: Level 5-9"
date: 2026-01-08
categories: ["Computer Science"]
tags: ["OverTheWire Bandit"]
---

Below are my solutions to Bandit level 5 to 9 continuing from [Level 0-4](https://enochyu-blog.pages.dev/posts/post06/). Let's get started~!!

## Level 5
### Task
Below is the task for [Level 5](https://overthewire.org/wargames/bandit/bandit5.html).

    Find the password that is stored in the only file in the "inhere" directory that is human-readable.

### My Solution
First, I ran the following commands to list all the files in the "inhere" directory.
```bash
ls
cd inhere
ls -a
```
In the "inhere" directory, there were ten files named "-file00" to "-file09". To find the human-readable file, the type of each file must be known.
```bash
file ./*
```
The command above allowed me to identify the ASCII text file. With the password, I was able to move on to the next level.

### Takeaways
The key command that I learned in this level is "file". Running `file myfile` will identify the file type of "myfile".


## Level 6
### Task
Below is the task for [Level 6](https://overthewire.org/wargames/bandit/bandit6.html).

    Find the password that is stored in a file in "inhere" directory that is human-readable, 1033 bytes in size, and not executable. 

### My Solution
First, I decided to list all files in "inhere" directory.
```bash
cd inhere
ls -a
```
Here, I was thrown into 20 directories. Inside each directory, multiple files existed. In other words, the level is not intended to be solved with manual inspection of each file. Therefore, I ran the following command to narrow down the choices.
```bash
file -size 1033c
```
where `c` is for bytes. The command provided me exactly one file with the password.

### Takeaways
Without manually inspecting each file, it is possible to find multiple properties of files with `file` command. Moreover, it is significant to optimize all the information provided by the prompt to make our lives easier.


## Level 7
### Task
Below is the task for [Level 7](https://overthewire.org/wargames/bandit/bandit7.html).

    Find the password that is stored in the server, owned by user bandit7, owned by group bandit6, and 33 bytes in size.

### My Solution
After running `ls -a` in the directory, `.`, `..`, `.bash_logout`, `.bashrc`, and `.profile` were listed. Therefore, `du -b .*` was used to list the following information.
```bash
220      .bash_logout
3851     .bashrc
807      .profile
```
None of the files were 33 bytes in size. In other words no comments in the files are likely to contain the password. In order to utilize the word "server", I travelled to the higher directory with `cd ..`.


### Takeaways


## Level 8
### Task
Below is the task for [Level 8](https://overthewire.org/wargames/bandit/bandit8.html).


### My Solution


### Takeaways


## Level 9
### Task
Below is the task for [Level 9](https://overthewire.org/wargames/bandit/bandit9.html).


### My Solution


### Takeaways


