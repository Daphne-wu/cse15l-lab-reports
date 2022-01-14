# Lab Report 1 Week 2
---
## *Tutorial for remote access*
## **Part 1**: Installing VScode
> Go to the [Visual Studio Code website](https://code.visualstudio.com/) and read the instructions to install it onto your computer. *Make sure its the correct version!* 
<br />
Here is what it should look like after installations (may have different color, menu bar, etc. depending on systems/settings):
<!-- ![Image](photos/vsCode.png) -->
<img src="photos/vsCode.png" width="200" height="140" />

##**Part 2**: Remotely Connecting
> If you are on a windows computer you must install [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) in order to remotely connect.
<br />
Next, look up your course-specific account for CSE15L here:
https://sdacs.ucsd.edu/~icc/index.php
<br /> For example, mine is: *cs15lwi22axn*
<br /> Now, open a terminal on VSCode and it should look like this:
<br /> 
 
<span style="color:blue">$ ssh cs15lwi22zz@ieng6.ucsd.edu </span>
<br /> 
> The **zz** are replaced by letters in course specific account (ex: mine are axn).
<img src="/Users/daphnewu/Desktop/remoteconnect.png" width="200" height="140" />
INSERT IMAGE
<br />
YAY! Now your terminal is connected to a computer in the CSE basement. **SO COOL.** The commands you  run on your terminal will run on that computer! Your computer is called the client and the computer in the basement is called the server based on your connection.

## **Part 3**: Trying Some Commands
> Let's start off by trying some simple commands.
* **cd** (this command "changes directory" to a specified one)
* **ls** (this command lists the files/folders in the current directory)
* **pwd** (this command "prints working directory")
* **mkdir** (this command makes a new directory of a specified name)
* **cp** (this command is used to make a copy of a specified file)
<br />
> Here is an example of running some commands:
 <br />
INSET IMAE

## **Part 4**: Moving Files with **scp**
>A key part of working remotely is being able to copy files between the computers back and forth. 
 <br />
To copy files from your computer to a remote computer, use the command **scp**. We will always run this from the *client* meaning from your own computer, not logged into ieng6.

Here is an example of using this command:
(I copied the WhereAmI.java file to the ieng6 server)

INSERT IMAGE

## **Part 5**: Setting an SSH key
> We're going set an SSH key to avoid having to enter our password everytimg we log in or run **scp**. 
(We are going to use a program called **ssh-keygen**, which creates a pair of files called *public key* and *private key*. We are going to copy the public key to a particular location on the serve and the private key to a partiuclar location on the client. Then, the **ssh** command uses the pair of files in place of your passowrd. 

To do so type the following in terminal on client (your computer):
 <br />
 <span style="color:blue">$ ssh-keygen</span>
 <br />
> This created two new files on your system...The private key (in a file id_rsa) and the public key (in a file id_rsa.pub), stored in the .ssh directory on your computer.

> Sidenote: (If using Windows, follow the extra ssh-add steps here: https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)

INSERT IMAGE

> Now we have to copy the public key to the **.ssh** directory of your user account on the server.
?$ ssh cs15lwi22zz@ieng6.ucsd.edu
Enter Password
# now on server
$ mkdir .ssh
$ logout
# back on client
$ scp /Users/joe/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above


















