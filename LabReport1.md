# Lab Report 1 - Kaustubh Paliwal
Welcome to my Lab Report for **week 1** of **CSE 15L**.  

In the first lab session, we focused on achieving three major tasks:-

**1. [Installing Visual Studio Code](#vscode)**  
**2. [Remotely Connecting to a Computer](#remoteaccess)**  
**3. [Running Some Commands (Remotely!)](#commands)**

Let's see how to do these using a step by step tutorial!

## Installing VSCode <a name="vscode"></a>

The first step was to download an integrated development environment (**IDE**) using which we can try to remotely access the computer.
**Visual Studio Code**, also known as **VSCode** is a popular IDE developed by Microsoft, which is used by millions of aspiring coders around the world. 

You can download VS Code using this [link](https://code.visualstudio.com/download).  This should take you to this page:-
<img width="1266" alt="image" src="https://user-images.githubusercontent.com/122563165/212525545-78f55d99-34f8-4f21-96d8-03602b3118eb.png">  

Select the operating system on your device and follow the steps given by the installer to correctly download VSCode on your system. Upon opening VSCode, you should see a similar page:-
<img width="1280" alt="image" src="https://user-images.githubusercontent.com/122563165/212525766-13beb60e-29a7-4af4-8264-83023c0484a0.png">

## Remotely Connecting to a Computer<a name="remoteaccess"></a>

This step is made possible using a tool called git. 
>Git is installed by default on MacOS, but Windows users can download it [here](https://gitforwindows.org/).  
><img width="365" alt="image" src="https://user-images.githubusercontent.com/122563165/212526080-c100339f-a898-45ca-877b-04f66211b3a4.png">  
Follow the steps listed in the installer and you should be good to go!

Now we need to set up the terminal in VSCode to use GitBash. Follow the steps given below:-

* Open VSCode on your computer.   
* Press *Ctrl+'* to open the terminal. 
* Press *Ctrl+Shift+P* to bring up the command pallete.
* Type *Select Default Profile* in the search bar and choose the option.   
  <img width="457" alt="image" src="https://user-images.githubusercontent.com/122563165/212526379-a28c9b7f-4f84-4b72-9f52-f3c9885f7cc7.png">
* Select GitBash from the options.
* Click on the *+* icon in the terminal window. The terminal is now a GitBash terminal.  
  <img width="146" alt="image" src="https://user-images.githubusercontent.com/122563165/212526482-41c1dcde-8611-4d10-9fad-1dc5d3c42a07.png">

Now to access the computer in the CSE building remotely, you'll need to know the course specific account using which you are allowed access. You can find the account details on [this page](https://sdacs.ucsd.edu/~icc/index.php).
>NOTE:- As this is the first time you'll be accessing the account, you will have to reset the password.

After you are done setting up your account, return to VSCode and open a new bash terminal using the shortcut *Ctrl+`*  
Now follow the steps listed below to access the computer :-

* Type in the command `$ ssh cs15lwi23zz@ieng6.ucsd.edu`
>Replace `zz` with the letters in your course specific account.  
>NOTE :- When we write the $, that’s not for you to type in! It’s just a convention for how we write commands.
* Since this is the first time you are accessing the computer, you will receive a message like this :-   
```
  ssh cs15lwi23zz@ieng6.ucsd.edu
  The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.    
  RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.      
  Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```
  Type `yes` and press enter
  *  This should result in a prompt `Password:` asking for your password. Go ahead and type in your password.
> While typing in your password, you cannot see any digits being entered on your screen, so be very careful as to not make any errors while typing in your password.
* After typing in the correct password, you should be successfully connected to a computer in the basement of the CSE Building!
<img width="257" alt="image" src="https://user-images.githubusercontent.com/122563165/212527590-6aeafcb5-1cf4-48c0-853e-97a7c782a7b0.png">

## Running Some Commands (Remotely!)<a name="commands"></a>

Now that we are successfully logged into the computer, we can run some commands using ssh. Some commands to try out would be :- 
* `cd ~`
* `cd`
* `pwd`
* `ls -a`
* `ls <directory>` where `<directory>` is `/home/linux/ieng6/cs15lwi23/cs15lwi23abc`, where the `abc` is one of the other group members’ username
* `cp /home/linux/ieng6/cs15lwi23/public/hello.txt ~/`
* `cat /home/linux/ieng6/cs15lwi23/public/hello.txt`

Let's try using some of the commands!

1. The `ls` command is used to list files. `ls -a` will list all files including hidden files (files with names beginning with a dot).
<img width="954" alt="image" src="https://user-images.githubusercontent.com/122563165/212527834-9f0c623d-2916-4b85-a978-22702a6d141c.png">

2.  `cat` command is used to print the content of a file onto the standard output stream. `cat /home/linux/ieng6/cs15lwi23/public/hello.txt` results in the following output :-
<img width="434" alt="image" src="https://user-images.githubusercontent.com/122563165/212527982-5ce092a3-1845-4b5f-b71b-1a62927d58f0.png">

3. `pwd` stands for 'print working directory' and is used to write to the output stream the full path name of your current directory. A sample output for this command is as follows :- 
<img width="206" alt="image" src="https://user-images.githubusercontent.com/122563165/212528186-898f036d-2d56-4705-9a63-e25f5fc8402f.png">

There are other basic commands you can try on the terminal. A list of them can be found [here](https://www.hostinger.com/tutorials/linux-commands).

Lastly, to log out of the remote computer, either press *Ctrl+D* on your keyboard or run the command `exit` in the terminal.

Hopefully after reading this tutorial, you were able to achieve the simple but exciting task of remote accessing a computer in the CSE Building. 
---









 





