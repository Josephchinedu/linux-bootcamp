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

```touch``` is a binary executable file located inside ```/bin``` directory of your system (use command ```which touch``` to see its location). When shell receives ```touch mike.txt```, it executes ```touch``` file with ```mike.txt``` as the command line option and ```touch``` creates ```mike.txt``` in the current directory of the terminal.

```ls``` is also a command to list files in a directory (current directory if no directory path argument is provided). We can use ```ls``` because it is a binary executable file located inside ```/bin```. We have used ```-al``` flags (or ```-a``` and ```-l```) separately, to list all files and directory with more information. This will also show ```.``` (current directory path) and ```..``` (parent directory path).

When you enter a command like ```ls``` or ```touch```, the shell interpreter first checks for an alias present in ```.bash_profile``` file in your home directory. If alias is not present, then it looks for a binary executable file in the PATH.

#### Declaring variables and introduction to ```echo``` and ```read``` commands
We can declare variables in a Bash script. Unlike other programming languages, we don’t need to declare with ```var``` keyword or data type like ```int```.
To declare a variable and assign with a value, use ```VARIABLE_NAME=VALUE``` expression (with no spaces in between).

```bash
CITY=Lagos
NAME="Joseph Chinedu"
AGE=269
EMAIL='devjoseph@coding'
GRADE=8.43
EMPLOYED=true
```

In the above example, we have declared a few variables with different data types. But Bash does not have a type system, it can only save string values. Hence internally, Bash saves them as a string.

To print a value, we use ```echo``` command. It is a binary file located inside ```/bin```. It takes arbitrary arguments which could be a string or a variable.

To print a variable declared in the script, we need to put ```$``` as the prefix for the ```VARIABLE_NAME``` like ```$VARIABLE_NAME```.

```bash
echo $NAME $AGE $EMAIL $GRADE $EMPLOYED
Joseph Chinedu 269 devjoseph@coding 8.43
```

We can read user input in the terminal using ```read``` command. When the user input the text and hit enter, that entire text will be saved in a variable.

```bash
echo -n "Enter a name:"
read NAME
echo "Your name is:" $NAME

⥤ Enter a name: ⥢ John Doe
⥤ Your name is: John Doe
```
From the above program, we used ```echo``` command with ```-n``` flag, this will prevent adding a newline to the terminal so that user can input text on the same line. Then ```read``` command has given ```NAME``` as the argument, this will create ```NAME``` variable and save user input in it.
  💡```-n``` is not supported in ```sh```. You can use ```\c``` to prevent ```echo``` command adding a new line, for example, ```echo “Enter a name:\c”```.


#### String interpolation
We can concatenate two variable by just placing them side by side.
```bash
FIRST_NAME='Joseph'
LAST_NAME='Chinedu'
echo $FIRST_NAME$LAST_NAME
FULL_NAME=$FIRST_NAME$LAST_NAME
echo $FULL_NAME
⥤ JosephChinedu
⥤ JosephChinedu
```

Bash also supports ```+=``` operator to concatenate two strings.

```bash
NUMBER=1
NUMBER+=2         # 1+2 => 12
NUMBER+=$NUMBER   # 12+12 => 1212
echo $NUMBER
⥤ 1212
```

#### Arithmetic Operations
We can perform arithmetic operations in Bash even though Bash does not support ```number``` data type. Let’s see different mechanisms through which we can perform arithmetic operations.
##### 1. Using let command
We can perform simple arithmetics calculations with ```let``` command.

```bash
let RESULT=1+1
echo $RESULT
⥤ 2

```
Since ```let``` would evaluate the expression in a string. So if you want to use interpolation to generate a string, it’s possible. Now we know that, based on the operation, Bash will convert string to appropriate data type.
We can use any arithmetic operation like ```+```, ```-```, ```*``` or ```/```. We can also calculate the modulus using ```%``` operator. We can also increment or decrement a variable using ```VAR++``` , ```++VAR```,```VAR--``` or ```--VARexpression```.

```bash
NUMBER=1
let RESULT="++NUMBER"
echo $RESULT
echo $NUMBER
⥤ 2
⥤ 2

```

##### 2. Using expr command
We can also use ```expr``` command to execute an expression which takes multiple arguments ( it concatenates them and executes it ). It does not have a problem like ```let``` to declare a variable but it will print the result by default, hence we need to use ```$(expression)``` syntax.

```bash

expr 1 + 1   # prints to the STDOUT
RESULT=$(expr 3 \* 3)
echo $RESULT
⥤ 2
⥤ 9

```

##### 3. Using double parentheses
Using ```$((expression))``` syntax, we can also perform arithmetic operations. We can put spaces between the ```expression``` which is valid.

```bash

RESULT=$((1 + 1))
echo $RESULT
⥤ 2

```
#### if/else conditions in Bash
If an ```expression``` is used, it is a job of runtime or an interpreter to evaluate the expression and return ```true``` or ```false```. In bash, ```test``` command is used to evaluate an expression. This command accepts a series of arguments which forms an expression when combined.

Let’s test a simple example. In the below example, we are checking if the value ```5``` is greater than ```9```. We use ```-gt``` argument to state a greater than operation.
```bash
test 5 -gt 9
⥤
```

In the above example, all the arguments should be in the order given else ```test``` would not understand the operation. In this case, we are not sure if the expression ```5 -gt 9``` is ```true``` or ```false``` as nothing was printed to the terminal.
In Bash, ```$?``` expression prints the status of the last command executed.

```bash
echo $?
⥤ 1
```

Our last command was test ```5 -gt 9``` and it exited with status ```1``` which means the expression ```5 -gt 9``` is false.

```test``` command also has an alias command ```[```. Don’t be surprised, it is actually a command. You can check that by ```which [``` and it should return ```/bin/[```. This works exactly like ```test``` command except it needs the last ```]``` argument. ```]``` is not a command, it is just a character which is required by ```[``` command to make the expression easier to understand.

```bash
~$ [ 5 -lt 9 ]
~$ echo $?
⥤ 0
~$ [ 5 -gt 9 ]
~$ echo $?
⥤ 1

```

##### 1. if/else block
To write if/else statement, we need to use ```if/then/else blocks```. ```[``` command is preferred to evaluate ```test``` conditions and it makes code easier to read.

```bash
if [ conditional expression ]
then
    # if code here
else
    # else code here
fi
```

# Lab 1: Create a Linux virtual machine with the Azure CLI
1. Launch Azure Cloud Shell
![Azure Cloud Shell](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/azure-power-shell.PNG?raw=true)
2. Create a resource group
![resource group](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/azure_resouce_group.PNG?raw=true)
3. Create virtual machine
![virtual machine](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm.PNG?raw=true)
4. Open port 80 for web traffic
![port 80](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/port80.PNG?raw=true)
5. Connect to virtual machine
![onnect to virtual machine](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/connect_to_vm.PNG?raw=true)
6. Install web server
![web server](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/install_web_server.PNG?raw=true)
7. View the web server in action
![View web](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/view_web_version.PNG?raw=true)



