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

# Lab 2: Manage Linux VMs with the Azure CLI
1. Create resource group
![resource group](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2_resource_group.PNG?raw=true)

2. Create virtual machine
![virtual machine](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-vm.PNG?raw=true)

3. Connect to VM
![Connect to VM](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/connect_to_vm.PNG?raw=true)

4. Understand VM images
![Understand VM images](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-image-tables.PNG?raw=true)
![Understand VM images](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/all_centos_table.PNG?raw=true)
![Understand VM images](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2_vm_centos.PNG?raw=true)

5. Understand VM sizes
A virtual machine size determines the amount of compute resources such as CPU, GPU, and memory that are made available to the virtual machine. Virtual machines need to be sized appropriately for the expected work load. If workload increases, an existing virtual machine can be resized.
##### Find available VM sizes
![VM sizes](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-sizes.PNG?raw=true)

##### Create VM with specific size
![specific size](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-specific-size.PNG?raw=true)

##### view the current of size of a VM
![view](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-size-vm.PNG?raw=true)

##### az vm list-vm-resize-options
![vm-resize-options](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-resize-options.PNG?raw=true)

##### az vm resize
![vm resize](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-resize.PNG?raw=true)

##### VM start
![vm start](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/start-vm.PNG?raw=true)



# VM power states
##### Find the power state
To retrieve the state of a particular VM, use the ```az vm get-instance-view``` command. Be sure to specify a valid name for a virtual machine and resource group.
![power state](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-power-state.PNG?raw=true)



# Management tasks
##### Get IP address
![IP address](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-ap-address.PNG?raw=true)

##### Stop virtual machine
![stop vm](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab-stop-vm.PNG?raw=true)

##### Start virtual machine
![start vm](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-start.PNG?raw=true)

##### Delete resource group
![Delete resource group](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab2-delete-resource-group.PNG?raw=true)


# Lab 3: Manage Azure disks with the Azure CLI
Azure virtual machines (VMs) use disks to store the operating system, applications, and data. When you create a VM, it is important to choose a disk size and configuration appropriate to the expected workload

##### Default Azure disks
When an Azure virtual machine is created, two disks are automatically attached to the virtual machine.
```Operating system disk```
```Temporary disk```

##### Azure data disks
To install applications and store data, additional data disks can be added. Data disks should be used in any situation where durable and responsive data storage is desired. The size of the virtual machine determines how many data disks can be attached to a VM.

##### VM disk types
Azure provides two types of disks.
```Standard disks```
```Premium disks```

### Attach disk at VM creation
Create a resource group with the az group create command.
![resource group](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3_group.PNG?raw=true)

In the following example, a VM is created with two data disks, both 128 GB. Because the disk sizes are 128 GB, these disks are both configured as P10s, which provide maximum 500 IOPS per disk.
![data disks](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3_vm_data_disks.PNG?raw=true)

### Attach disk to existing VM
The following example creates a premium disk, 128 gigabytes in size, and attaches it to the VM created in the last step.
![Attach disk](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/vm-disk-attach.PNG?raw=true)

### Prepare data disks
Once a disk has been attached to the virtual machine, the operating system needs to be configured to use the disk.

Create an SSH connection with the virtual machine.
![SSH connection](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3-ssh-connect.PNG?raw=true) 

Partition the disk with parted.
![Partition](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3-partion.PNG?raw=true) 
Write a file system to the partition by using the ```mkfs``` command. Use ```partprobe``` to make the OS aware of the change.
![os partion](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/os-partion.PNG?raw=true)
Mount the new disk so that it is accessible in the operating system.
![os partion](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/mount-disk.PNG?raw=true)
The disk can now be accessed through the ```/datadrive``` mountpoint, which can be verified by running the ```df -h``` command.
![mount point](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/mount-point.PNG?raw=true)
To ensure that the drive is remounted after a reboot, it must be added to the /etc/fstab file. To do so, get the UUID of the disk with the ```blkid``` utility.
![blkid](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/blkid.PNG?raw=true)
Open the ```/etc/fstab``` file in a text editor as follows:
![nanoedit](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/nanoedit.PNG?raw=true)

### Create snapshot
![snap shot](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/snapshot.PNG?raw=true)
![snap shot](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/create-snap.PNG?raw=true)

### Create disk from snapshot
![snap shot](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/disk-snapshot.PNG?raw=true)

### Restore virtual machine from snapshot
To demonstrate virtual machine recovery, delete the existing virtual machine using az vm delete.
![snap shot](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/delete-snap-shot.PNG?raw=true)
Create a new virtual machine from the snapshot disk.
![snap shot](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3-new-virtual-m.PNG?raw=true)

### Reattach data disk
All data disks need to be reattached to the virtual machine.

Find the data disk name using the az disk list command. 
![data list](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab3_datalist.PNG?raw=true)
Use the az vm disk attach command to attach the disk.


# Lab 4: Create and use an SSH public-private key pair for Linux VMs in Azure
With a secure shell (SSH) key pair, you can create virtual machines (VMs) in Azure that use SSH keys for authentication.

##### Supported SSH key formats
Azure supports SSH protocol 2 (SSH-2) RSA public-private key pairs with a minimum length of 2048 bits. Other key formats such as ED25519 and ECDSA are not supported.

### Create an SSH key pair
Use the ```ssh-keygen``` command to generate SSH public and private key files.
The following command creates an SSH key pair using RSA encryption and a bit length of 4096:
![ssh key](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/create-ssh-key.PNG?raw=true)
![vm](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab4-create-vm.PNG?raw=true)

display your public key with the following ```cat``` command
![cat-ssh](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/cat-ssh.PNG?raw=true)
to create your VM with an existing public key, specify the value and optionally the location of this public key using the az vm create command with the ```--ssh-key-values``` option.
![ssh](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/create-re-shh.PNG?raw=true)

### SSH into your VM
![SSH into your VM](https://github.com/Josephchinedu/linux-bootcamp/blob/devjoseph/devjoseph_images/lab4-ssh-vm.PNG?raw=true)

