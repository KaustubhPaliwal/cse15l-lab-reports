# Lab Report 4 - Kaustubh Paliwal
Welcome to my Lab Report for **Week 7** of **CSE 15L**.  

In the lab session this week, we focused on learning the skill of manipulating code and working with Git through the command line. To put our newfound learnings into 
test, Professor Joe Politz designed a Coding race called **Speed Up** which took place in Lab 7. We had to complete 9 difficult tasks and the quickest one to do so 
earned a certificate!! 

The nine steps needed to complete the challenge were as follows:-

**1. [Delete Existing Forks](#delete)**  
**2. [Forking the Lab 7 Repository](#fork)**  
**3. [Starting the timer!!](#timer)**  
**4. [Logging into ieng6](#remote)**  
**5. [Cloning the Lab 7 Repository](#clone)**  
**6. [Running JUnit Tests](#tests)**  
**7. [Fixing the Code](#fix)**  
**8. [Checking the Fixed code](#check)**  
**9. [Commit and Push](#candp)**

Let's see how to do these using a step by step tutorial!
>NOTE :- For the steps, we assume that you have the SSH Keys for GitHub and ieng6 setup as taught in Lab7.     
>For more information visit the course information page for [week 7](https://ucsd-cse15l-w23.github.io/week/week7/)

## Delete Existing Forks <a name="delete"></a>

The first step will be checking your GitHub account and making sure that there are no repositories called Lab7. 
> This step is probably only applicable only after you have completed the entire Race once

To delete a repository, click on the Settings tab of the repository and go to the General Settings tab. 

<img width="617" alt="image" src="https://user-images.githubusercontent.com/122563165/221133744-6eecf521-5e5f-4fc0-9447-7947fcbcea71.png">  
Here, scroll down to the absolute bottom of the page and click on the red button named Delete Repository   
<img width="584" alt="image" src="https://user-images.githubusercontent.com/122563165/221134042-0c500402-9001-4c97-96ea-f4443c77425c.png">
Go ahead and type the path of the repository and press enter. That should delete the repository from your GitHub account.

If this is the second time you are trying this race, you need to also delete the repository from the ieng6 server. To do this follow the code given below:-
```
cd <enter>
rm -rf lab7 <enter>
```
`rm-rf` ensures that the lab7 repository is deleted from the server.

## Forking the Lab 7 Repository <a name="fork"></a>

This is probably the first step if this is the first time you are going through the steps.   
Now click on the link for the [Lab7 repository](https://github.com/ucsd-cse15l-w23/lab7) 
and fork it using the <img width="113" alt="image" src="https://user-images.githubusercontent.com/122563165/221135262-80b0de7b-f0dd-46cf-bddb-acbb9a0f56d9.png">
sign at the top right corner.

You are done! You should have the Repository now forked into your own GitHub account.

## Starting the timer!! <a name="timer"></a>

Open a clock app on your Laptop or Mobile Phone, or use this [link](https://www.timeanddate.com/stopwatch/) and start the stopwatch. 
<img width="571" alt="image" src="https://user-images.githubusercontent.com/122563165/221136059-d9fd57fa-e3c3-49a2-9fd9-17aba49dd20b.png">  
**3, 2, 1, off you go. Good Luck!!**

## Logging into ieng6 <a name="remote"></a>

Now open Visual Studio Code on your system and open the GitBash terminal. 
> You don't neccesarily need to use VSCode, the main objective is opening a GitBash Terminal

Now go ahead and type:-
```
ssh cs15lwi23___@ieng6.ucsd.edu <enter>
```
> NOTE :- Replace `___` with the three letter code of your course specific account 

You should be logged in after `<enter>` as setting up the SSH Key for ieng6 ensures that you do not need to type out the password
on every login.

## Cloning the Lab 7 Repository <a name="clone"></a>

After logging in, open the fork of the Lab7 repository in a browser. Next, click on the button <img width="80" alt="image" src="https://user-images.githubusercontent.com/122563165/221139423-b7128c7d-bd0a-4b82-9796-9702ff65489f.png">
and select the option `SSH`. Now copy the path of the `SSH` and return to the ieng6 terminal.  
<img width="276" alt="image" src="https://user-images.githubusercontent.com/122563165/221139784-2b11620f-7d71-4c95-b93c-641b177bd3b3.png">  
Now, in the terminal, type the following code :- 
```
git clone (ssh key from GitHub) <enter>
```
> Replace `ssh key from GitHub` with the link-like text we just copied from GitHub.

You should be greeted with a success message like this :-   
<img width="565" alt="image" src="https://user-images.githubusercontent.com/122563165/221140379-fe942f8b-808d-463c-89f3-40749f657a3f.png">

## Running JUnit Tests <a name="tests"></a>

Now it is time to test our code and check for the error in the file `ListExamples.java` that is present in the folder lab7. To run JUnit Tests, follow the 
instructions given below :- 
```
cd lab7 <enter>
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>
local $ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>
```

This should run the JUnit tests on the files given in lab7. 

<img width="469" alt="image" src="https://user-images.githubusercontent.com/122563165/221143277-a01ee6bd-0559-484b-8eaa-59f176e32962.png">

You will notice that the file `ListExamples.java` has an error, your task in the next step is to 
identify this error and rectify it to make the tests pass.

## Fixing the Code <a name="fix"></a>

To fix the code, you will have to use the command `nano` to view the contents of the file and make a change. To enter the file and view the code, use the command :-   
```
nano ListExamples.java <enter>
```

This should open the code layout in the terminal as follows.   
<img width="1029" alt="image" src="https://user-images.githubusercontent.com/122563165/221142445-e873bb1b-ba66-48b1-b513-ac116af04c46.png">

Now you should use the `<up>` and `<down>` arrow keys to navigate through this interface. The error according to the error message is at line 42, so use the command `<down>` 42 times!!
You should be at the line that caused the error, you will notice that the loop will have the increment `index1 += 1` instead of `index2 += 2`

To fix this, follow the steps mentioned below :- 
``` 
<right><right><right><right><right><right><right><right><right><right><right><right> <backspace> <Type 2>
CTRL + O <enter>
<enter>
CTRL + X <enter>
```
> The `<right>` key helps you navigate to index1 and make the change in the code
  
You should be back to the normal terminal and exited from the nano terminal. You `CTRL + O` is the shortcut for Saving the changes, and `CTRL + X` is the shortcut
for exiting the `nano` terminal. Your file's changes should be saved now.

## Checking the Fixed code <a name="check"></a>

Now we need to rerun the tests to check whether our fix worked or not. To do this we will use the following commands :- 
```
<up><up><up> <enter>
<up><up><up> <enter>
```

The first line of the code block pertains to the running of the `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` command. We use `<up>` three times are it is the third latest command in the terminal history.

The second line of the code block pertains to the running of the `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` command. It is also the third latest command in terminal history, therefore we use the `<up>` key thrice and then press `<enter>`.

> We need to compile the files before running the tests again, else the changes will not reflect in the test

After running the test, we get the output that the test passes all cases and run without any failures.  
<img width="115" alt="image" src="https://user-images.githubusercontent.com/122563165/221146988-230627f4-cffb-4a7e-ab86-d423d2478b5d.png">

Therefore, we now know that the code is fixed and the only remaining step is pushing and committing it to the GitHub repository.

## Commit and Push <a name="candp"></a>

To update the recent changes in the GitHub repository, we need to follow the commands given below :- 
```
git add ListExamples.java <enter>
git commit -m "Updated" <enter>
git push origin main <enter>
```
> Do not forget the `-m` in the commit command, as the absence of it will lead you to vim which will slow you down a lot!
After the `commit` and `push` commands, you should see success messages such as follows :-   
<img width="387" alt="image" src="https://user-images.githubusercontent.com/122563165/221148045-b1c60a4a-437a-4dbf-94c1-761b397e852e.png">

**And you are done!!** Congratulations on reaching the end of the tutorial for the **Speed Up** Challenge for CSE 15L. 

***

Hopefully after reading the guide, you now are better prepared for the competition and now have a better understanding of commands like `nano` and tricks like `SSH Keys` and terminal shortcuts!
---











