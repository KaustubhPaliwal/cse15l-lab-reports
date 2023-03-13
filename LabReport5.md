# Lab Report 5 - Kaustubh Paliwal
Welcome to my Lab Report for **Week 10** of **CSE 15L**.  

We are at the end of the quarter, Winter 2023. We learned and practiced multiple new things throughout this course like accessing remote servers, creating new servers, 
bash commands and scripts, and much more. One of the things I most enjoyed doing this was creating a Grading Script, which works like Autograder on Gradescope. 

While creating a Grading Script, I had to follow the given below workflow:- 

1. Clone the repository of the student submission to a well-known directory name.
2. Check that the student code has the correct file submitted. If they didn’t, detect and give helpful feedback about it. 
3. Somehow get the student code and your test .java file into the same directory
4. Compile your tests and the student’s code from the appropriate directory with the appropriate classpath commands. If the compilation fails, detect and give helpful feedback about it.
5. Run the tests and report the grade based on the JUnit output.

While keeping in mind these specifications, I created the following Grading Script :- 
```
CPATH='.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar'

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

cd student-submission 

if [[ -f ListExamples.java ]]
then
    echo "ListExamples found"
else
    echo "need file ListExamples.java"
    exit 1
fi 

cp ../TestListExamples.java ./ 
cp -rf ../lib .

javac -cp $CPATH *.java

if [[ $? -eq 0 ]]
then
    echo ""
else    
    echo "Failed Compilation, Grade : F"
    exit 1
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples >java-tester.txt 2>&1

if [[ $? -eq 0 ]]
then
    echo "Passes all Test Cases, Grade : A"
elif [[ $? -eq 1 ]]  
then 
    echo "Failed to Pass All Cases, Grade : B"
else 
    echo "Failed All Test Cases, Grade : F"
    exit
fi
```

This script fulfils all the requirements and provides the grades :- 
* A, if all test cases pass
* B, if One test case fails
* F, if all test case fails

Here are some of examples of the Grading Script running on different type of files :-   
**1. [Lab 3 Implementation](#lab3)**    
**2. [Lab 3 Corrected Methods](#lab3corrected)**    
**3. [Compiler Error](#compiler)**  
**4. [Wrong FileName](#filename)**  

Let's see the grading script run on these and the results it produces!

## Lab 3 Implementation <a name="lab3"></a>

We are running the Grading Script on the files present in this [directory.](https://github.com/ucsd-cse15l-f22/list-methods-lab3)

To run the script on this repository, we run the following command in the terminal :- 
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3
```
<img width="307" alt="image" src="https://user-images.githubusercontent.com/122563165/224598367-c5f7d266-2534-46b6-a2a9-df8634fde425.png">

As we can see, it fails to pass all the test cases as we saw in Lab3, and therefore sucessfully produces the Grade B.

## Lab 3 Corrected Methods <a name="lab3corrected"></a>

We are running the Grading Script on the files present in this [directory.](https://github.com/ucsd-cse15l-f22/list-methods-corrected)

To run the script on this repository, we run the following command in the terminal :- 
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected
```
<img width="303" alt="image" src="https://user-images.githubusercontent.com/122563165/224598680-8b728011-7531-43e1-989c-d7f5f851aaa3.png">

This file contains correctly working methods, and therefore sucessfully passes all the test cases and produces the Grade A.

## Compiler Error <a name="compiler"></a>

We are running the Grading Script on the files present in this [directory.](https://github.com/ucsd-cse15l-f22/list-methods-compile-error)

To run the script on this repository, we run the following command in the terminal :- 
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error
```
<img width="305" alt="image" src="https://user-images.githubusercontent.com/122563165/224599063-26d9de52-8021-4f29-a2eb-ff97d1b5f847.png">

This file contains a compiler error as it is missing a semicolon in one of the lines, and therefore fails to compile and produces a grade F due to a compiler error.

## Wrong FileName <a name="filename"></a>

We are running the Grading Script on the files present in this [directory.](https://github.com/ucsd-cse15l-f22/list-methods-filename)

To run the script on this repository, we run the following command in the terminal :- 
```
bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-filename
```
<img width="306" alt="image" src="https://user-images.githubusercontent.com/122563165/224599380-de58750c-e36a-4eaf-bb5f-ccc2e703eefa.png">

This file contains a wrong FileName, therefore the grading script does not find the required file, and thus produces `need file ListExamples.java` with no Grade.

---

**As we can see the Grading Script successfully performs the required tasks on several implementations of the file `ListExamples.java`.** 

At the end of the quarter, I am grateful to the Professor and the Instructional Assistants for such an informational and engaging course throughout the Ten Weeks and I am looking forward to having a CSE Lab Class again in the future!
---

