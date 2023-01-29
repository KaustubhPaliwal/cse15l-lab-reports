# Lab Report 2 - Kaustubh Paliwal
Welcome to my Lab Report for **week 2** of **CSE 15L**. 

In Lab Session of Week 2 and Week 3, our main focus was three things:-

**1. [Running a Server Remotely](#remoteserver)**  
**2. [Learning to Identify and Fix Bugs](#bugs)**  
**3. [The New Things We Learnt](#newthings)**

Let's see examples of how to do these things Step by Step:-

## Running a Server Remotely <a name="remoteserver"></a>

The first thing we will do is clone a respository with GitHub Desktop! 
**GitHub Desktop** is an open source tool which allows growing developers
to be more productive. 

To get started, first we have to download GitHub Desktop from [here](https://desktop.github.com/).
<img width="774" alt="image" src="https://user-images.githubusercontent.com/122563165/215316191-94e50119-b5fd-4012-9c19-b5bc413929cf.png">

Installing and logging in with your Github account should take you to the startup page. 

The next step will be
opening this [respository](https://github.com/ucsd-cse15l-f22/wavelet) and forking it. This will create your
own copy of the preexisting repository.
Then, we want our repository to be open  in the desktop app. To do this, go on the page of 
the forked repository and click on the `<>Code` button followed by `Open with GitHub Desktop`.

<img width="298" alt="image" src="https://user-images.githubusercontent.com/122563165/215316380-5f0e00fd-2c2d-4d7e-bccd-70f2bb802b19.png">

Now after opening it GitHub Desktop, we will use the open `Open in Visual Studio Code` which should open the files in 
the IDE known as **VSCode**.

<img width="450" alt="image" src="https://user-images.githubusercontent.com/122563165/215316637-090ef167-b741-4f92-b272-d7ae24a0edc7.png">

Now, create a new file named `StringServer.java` and paste the following code in it:-
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a string that will be manipulated by
    // various requests.
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return str;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    str += parameters[1] + "\n";
                    return String.format(str);
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
Now commit and push the changes using the GitHub Desktop app. Now as we did last time, log into the remote computer
in the CSE Building using your specific course account. 
> We learned about remote accessing a Computer in [Lab Report 1.](https://github.com/KaustubhPaliwal/cse15l-lab-reports/blob/main/LabReport1.md)  

After logging in run the command `git clone <your-repository-url-for-your-fork>`
This should load your repository and its contents onto the remote computer.
> Paste the URL for the forked (i.e. your own copy) repository

A successful cloning should give this message:-

<img width="464" alt="image" src="https://user-images.githubusercontent.com/122563165/215317117-8c0ff689-3bbd-41d2-9345-a78856633f63.png">

Type the following code to compile and start your server :-
```
cd wavelet
javac Server.java StringServer.java 
java StringServer 4000
```

This should have started your server! Now to access your website and add the words your like onto it, type onto
the web browser `http://ieng6-201.ucsd.edu:4000`

We will now test if the server is doing its purpose of taking in a word as a query and storing and displaying it on every call.

**1.**  For our first try we will try to add the words **Welcome to** by accessing the server using the link 
`http://ieng6-201.ucsd.edu:4000/add-message?s=Welcome to`

The result should be as follows :-
<img width="486" alt="image" src="https://user-images.githubusercontent.com/122563165/215317632-0ec13f08-9dee-4caa-8ff7-a3ae7f7f6842.png">

For this example:-
* The methods called are `public String handleRequest()` 
* When the link is entered in the browser, the argument passed into the method `handleRequest()` is `URI url` which contains the address we typed in and `String str` is created which is a String which stores the history of all the strings entered.
* Other values of parameters and fields which change after entering the link are `getPath()` which stores everything in the address after `4000`, `getQuery()` which stores everything after `?`, parameters which is a String array which divides the Query into 2 parts, one before `=`, and one after. `Parameters[0]` which contains the value of `s` `and Parameters[1]` which contains the value of `Welcome To`.

**2.**  For our second example we will add on the words **Lab Report 2** in the second line by accessing the server using the link `http://ieng6-201.ucsd.edu:4000/add-message?s=Lab Report 2` 

The result should be as follows :- 

<img width="506" alt="image" src="https://user-images.githubusercontent.com/122563165/215318279-9417f151-5a9d-46ce-895c-a6b29a7073e0.png">

For this example:-
* The methods called are `public String handleRequest()` 
* When the link is entered in the browser, the argument passed into the method `handleRequest()` is `URI url` which contains the address we typed in and `String str` is a String which stores the history of all the strings entered.
* Other values of parameters and fields which change after entering the link are, `String str` which now stores the values of both the entered Strings, `getPath()` which stores everything in the address after `4000`, `getQuery()` which stores everything after `?`, parameters which is a String array which divides the Query into 2 parts, one before `=`, and one after. `Parameters[0]` which contains the value of `s` `and Parameters[1]` which contains the value of `Lab Report 2`.

To turn off the server, press `Ctrl-C`

Here we go! We have now successfully created a server and made it store words which we entered!

## Learning to Identify and Fix Bugs<a name="bugs"></a>

Using the steps used earlier go ahead and fork and open this [repository](https://github.com/ucsd-cse15l-w23/lab3) in VSCode.

The file `ArrayExamples.java` has bugs in all of the methods. To fix this we will write a JUnit Test in the file `ArrayTests.java`

Go ahead and copy this code in the editor :-
```
import static org.junit.Assert.*;

import java.lang.reflect.Array;

import org.junit.*;

public class ArrayTests {
	@Test 
  public void testReversed() {
    int[] input1 = {1,2,3,4};
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
  
}
```
Go ahead and run this test, you will see that the test has failed. 

<img width="722" alt="image" src="https://user-images.githubusercontent.com/122563165/215319029-b9ede220-32a2-48c7-88cd-bbea4aa7903f.png">

This proves that the method `reversed()` in the file `ArrayExamples.java` isn't doing the required task of reversing the elements in the array.

After analyzing the code and results of the test, we can see some issues and observe that the function stores `0` instead of the expected `4`. One possible outcome could be that it stores 0 instead of all elements.
To test this theory, let us try checking the output value of the String with an Array of value `[0,0,0,0]`. 

We go ahead and change the code to :- 

```
import static org.junit.Assert.*;

import java.lang.reflect.Array;

import org.junit.*;

public class ArrayTests {
	@Test 
  public void testReversed() {
    int[] input1 = {0,0,0,0};
    assertArrayEquals(new int[]{0,0,0,0}, ArrayExamples.reversed(input1));
  }
  
}
```

After running the test, we see that the code successfully reverses a array containing value `[0,0,0,0]`.

<img width="494" alt="image" src="https://user-images.githubusercontent.com/122563165/215319278-c4d3bf65-48de-43ca-8ec9-38210e9cf755.png">

Let us try two more inputs of values :- 
* `[1,2]`

   <img width="768" alt="image" src="https://user-images.githubusercontent.com/122563165/215319512-e6893878-b593-478b-b077-0e5dc3c8ac66.png">
   We see that running the test with the following inputs has again failed the test with the *Symptom* being that the first element is 0. 
   
* `[2,0,0]`

   <img width="767" alt="image" src="https://user-images.githubusercontent.com/122563165/215319616-2597f6e0-d994-4ec9-b835-df40909dca47.png">
   We see that this time the element differs at index 2, where the element is still 0 instead of 2. 


We can now see that the symptom is that all the elements in the Reversed Array are 0. 

The bug might be due to the code :-
```
arr[i] = newArray[arr.length - i - 1];
```
This code instead of assigning the value of the last element of the existing array to the first element of the new array, it does the opposite which results in the value of the current array being `[0.0.0.0]`, etc. Also, it doesn't reassign the value of `arr` to `newArray`.

The solution to that bug will be assigning the value of the last element of the existing array to the first element of the new array.

The fixed code is :- 
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i=i+1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    arr = newArray;
    return arr;
  }
```

Let us rerun the JUnit test to see if it is passing now

<img width="482" alt="image" src="https://user-images.githubusercontent.com/122563165/215320116-7e712f8a-0b1e-446f-8756-764ac8134168.png">

We can now see that the original test is finally passing. Hence our code is now *Bug-Free*. 

## The New Things We Learnt)<a name="newthings"></a>

At the end of this Lab Report 2, and week 3 of the Winter Quarter 2023, I have learned a lot of new things, some which I always used in my 
day to day lives like accessing the remote server of Instagram or encountering the WebLogInService Failed on the UCSD Login page, but I never knew how these worked.


To conclude Lab Report 2, here is a list of new things I have learned from week 2 and 3 of Lab Sections which I didn't know before :- 

* Using GitHub Desktop
* Forking a repository on GitHub
* Cloning a repository onto a remote desktop
* Running a local and remote server
* Accessing and storing information stored on these server using their Queries and Paths
* Learning about Symptoms, Bugs and Solutions
* Practicing Identifying Bugs through Symptoms and creating a viable solution
* Creating and running JUnit tests

The past two weeks were a fun and exciting journey of learning and I am looking forward to learning more new and fascinating things throughout the rest of the quarter.
---


