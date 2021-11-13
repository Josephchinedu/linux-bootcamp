# linux-bootcamp
Linux Cloud Engineer Bootcamp

## Devjoseph Section
### Week 1 ~~ Bash Scripting and Shell Programming
Bash (AKA Bourne Again Shell) is a type of interpreter that processes shell commands.
A shell interpreter takes commands in plain text format and calls Operating System services to do something. For example, ls command lists the files and folders in a directory. Bash is the improved version of Sh (Bourne Shell). A shell scripting is writing a program for the shell to execute and a shell script is a file or program that shell will execute.

To create directory/folder using bash, use "mkdir"
we'll be creating a directory call josephjunck. It'll be a folder that'll contain all the file we don't want to push to github.

this's gitbash for windows
```bash
DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud
$ mkdir josephjunck

```
To change directory use "cd"
we'll be change directory into the newly created folder
```bash
DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud
$ cd josephjunck

```

```bash
DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud/josephjunck
$ touch mike.txt


DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud/josephjunck
$ touch segun.txt devjoseph.txt

DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud/josephjunck
$ ls
devjoseph.txt  mike.txt  segun.txt

DELL@DESKTOP-710D44U MINGW64 ~/Desktop/2021/November/cloud/josephjunck
$ ls -al
total 0
drwxr-xr-x 1 DELL 197121 0 Nov 13 01:51 ./
drwxr-xr-x 1 DELL 197121 0 Nov 13 01:43 ../
-rw-r--r-- 1 DELL 197121 0 Nov 13 01:51 devjoseph.txt
-rw-r--r-- 1 DELL 197121 0 Nov 13 01:51 mike.txt
-rw-r--r-- 1 DELL 197121 0 Nov 13 01:51 segun.txt

```

By typing Bash code directly in your terminal, it will get executed on Bash interpreter. In the above example, we have created ```mike.txt``` file using touch command and later ```segun.txt``` and ```devjoseph.txt``` at once.