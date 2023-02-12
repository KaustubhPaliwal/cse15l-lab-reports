# Lab Report 3 - Kaustubh Paliwal
Welcome to my Lab Report for **Week 5** of **CSE 15L**.

This week we will focus on the command `grep`. 
The `grep` command in UNIX-like operating systems is a powerful utility for searching for patterns in text files. 

`grep` has various alternative ways of being used, which can give multiple different results. We can find an extensive list of many `grep` commands on the website [geeksforgeeks.com](https://www.geeksforgeeks.org/grep-command-in-unixlinux/).
<img width="945" alt="image" src="https://user-images.githubusercontent.com/122563165/218299688-6755aa2c-d595-44c4-ad01-810d1eec5752.png">

You can also ask **ChatGPT** for the options of `grep` using the following query :- 
<img width="594" alt="image" src="https://user-images.githubusercontent.com/122563165/218305307-2c0b04fc-4914-47a2-9394-ed323c7f8a5a.png">


Some different options for using the `grep` commands that we will focus on are as follows:-

**1. [`grep -h`](#count)**  
**2. [`grep -l`](#filename)**  
**3. [`grep -n`](#linenum)**   
**4. [`grep -r`](#recursive)**

Let's see how the different options behave using multiple examples and outputs! We will carryout all the commands on the directories given in the respository `skill-demo1-data` which was provided for Skill Demonstration 1. 
> All commands preceeded by $ in the code blocks are inputs

## `grep -h` <a name="count"></a>

`grep -h` is used to print only the lines that match the given pattern. It has the syntax `grep -h "<Pattern>" <Path of Directory>`. This is useful when we want to search a large directory and only want to know the information which contains the keyword that we are searching for. Examples of this being used are as follows:-
* In this example, we will use the `grep -h` command to find the count of all lines in written_2/ which contain the word "Lucayans". The command to use will be `grep -h "Lucayans" written_2/ */*/*/*`. This gives the exact lines in all the .txt files in written_2 that contain the word **Lucayans** in them without giving the name of the file. 
  ```
  $ grep -h "Lucayans" written_2/ */*/*/*
  grep: written_2/: Is a directory
  grep: written_2/non-fiction/OUP/Abernathy: Is a directory
  grep: written_2/non-fiction/OUP/Berk: Is a directory
  grep: written_2/non-fiction/OUP/Castro: Is a directory
  grep: written_2/non-fiction/OUP/Fletcher: Is a directory
  grep: written_2/non-fiction/OUP/Kauffman: Is a directory
  grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
  Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
  The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
  ```
  As we can see, the command prints the two occurances of the word without telling us which file they occured in.
  
* In this example, we will use the `grep -h` command to find the count of all lines in written_2/ which contain the phrase "Dance Biennale". The command to use will be `grep -h "Dance Biennale" written_2/ */*/*/*`. This gives the exact lines in all the .txt files in written_2 that contain the word **Dance Biennale** in them without giving the name of the file. 
   ```
   $ grep -h "Dance Biennale" written_2/ */*/*/*
   grep: written_2/: Is a directory
   grep: written_2/non-fiction/OUP/Abernathy: Is a directory
   grep: written_2/non-fiction/OUP/Berk: Is a directory
   grep: written_2/non-fiction/OUP/Castro: Is a directory
   grep: written_2/non-fiction/OUP/Fletcher: Is a directory
   grep: written_2/non-fiction/OUP/Kauffman: Is a directory
   grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
           September: Lyon, Dance Biennale; Deauville, American film
   ```         
   As we can see, the command prints the two occurances of the word "Dance Biennale" without telling us which file they occured in.   

## `grep -l` <a name="filename"></a>

`grep -l` is used to print only the names of all the files that match the given pattern. It has the syntax `grep -l "<Pattern>" <Path of Directory>`. This is useful when you want to search for a particular text file using a keyword. Examples of this being used are as follows:-
* In this example, we will use the `grep -l` command to find the list of all lines in written_2/ which contain the word **Refreshing**. The command to use will be `grep -l "Refreshing" written_2/ */*/*/*`. 
  ```
  $ grep -l "Refreshing" written_2/ */*/*/*
  grep: written_2/: Is a directory
  grep: written_2/non-fiction/OUP/Abernathy: Is a directory
  grep: written_2/non-fiction/OUP/Berk: Is a directory
  grep: written_2/non-fiction/OUP/Castro: Is a directory
  grep: written_2/non-fiction/OUP/Fletcher: Is a directory
  grep: written_2/non-fiction/OUP/Kauffman: Is a directory
  grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
  written_2/travel_guides/berlitz2/China-WhereToGo.txt
  ```
  The output shows the list of all file names in the directory which contain the word Refreshing. 
 
* In this example, we will use the `grep -l` command to find the list of all lines in written_2/ which contain the word **Exhaust**. The command to use will be `grep -l "Exhaust" written_2/ */*/*/*`. 
  ```
  $ grep -l "Exhaust" written_2/ */*/*/*
  grep: written_2/: Is a directory
  grep: written_2/non-fiction/OUP/Abernathy: Is a directory
  grep: written_2/non-fiction/OUP/Berk: Is a directory
  grep: written_2/non-fiction/OUP/Castro: Is a directory
  grep: written_2/non-fiction/OUP/Fletcher: Is a directory
  grep: written_2/non-fiction/OUP/Kauffman: Is a directory
  grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
  written_2/travel_guides/berlitz1/HistoryMallorca.txt
  ```
  The output shows that only one file, `HistoryMallorca.txt` has the word **Exhaust** in them. 
  
## `grep -n` <a name="linenum"></a>

`grep -n` is used to print the names of all the text files which contain the given pattern and the line number where the pattern matches. This is useful when you want to search for a particular keyword in a large directory and know which file contains the information you are looking for and where exactly is that information located.   

Examples of `grep -n` being used are as follows :- 
* In this example we will use `grep -n` to find the list of all the text files which contain the word "Panathanaikos" and the line number where the text files contain it. The command we will use is `grep -n "Panathanaikos" written_2/ */*/*/*`.
  ```
  $ grep -n "Panathanaikos" written_2/ */*/*/*
  grep: written_2/: Is a directory
  grep: written_2/non-fiction/OUP/Abernathy: Is a directory
  grep: written_2/non-fiction/OUP/Berk: Is a directory
  grep: written_2/non-fiction/OUP/Castro: Is a directory
  grep: written_2/non-fiction/OUP/Fletcher: Is a directory
  grep: written_2/non-fiction/OUP/Kauffman: Is a directory
  grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
  written_2/travel_guides/berlitz2/Athens-WhatToDo.txt:30:Football (soccer): Football is a national obsession for the Greeks and Athens’ teams (Panathanaikos and AEK Athens) feature prominently in domestic and European competitions. The season runs from September to May. Panathanaikos Football Stadium is located at Kifissia, a northern suburb — this will be the major stadium for the 2004 Olympic Games, which will be held in the city. Ask your hotel if it is possible to get tickets as these are difficult to come by.
  ```
  As we can see, `Athens-WhatToDo.txt:30` indicates that the file Athens-WhatToDo.txt contains the word **Panathanaikos** at line 30.
  
* In this example we will use `grep -n` to find the list of all the text files which contain the word "Juhu" and the line number where the text files contain it. The command we will use is `grep -n "Juhu" written_2/ */*/*/*`.
  ```
  $ grep -n "Juhu" written_2/ */*/*/*
  grep: written_2/: Is a directory
  grep: written_2/non-fiction/OUP/Abernathy: Is a directory
  grep: written_2/non-fiction/OUP/Berk: Is a directory
  grep: written_2/non-fiction/OUP/Castro: Is a directory
  grep: written_2/non-fiction/OUP/Fletcher: Is a directory
  grep: written_2/non-fiction/OUP/Kauffman: Is a directory
  grep: written_2/non-fiction/OUP/Rybczynski: Is a directory
  written_2/travel_guides/berlitz1/WhatToIndia.txt:26:        at the major port cities. In Mumbai, both Juhu and Chowpatty beaches
  ```
  As we can see `WhatToIndia.txt:26` indicates that the text file WhatToIndia contains the word **Juhu** at line 26.
  
## `grep -r` <a name="recursive"></a>
 
 Notice how so far in all the commands we have been using `*/*/*/*`. This is used to recursively enter each folder in the directory and look for the pattern in each file. For that to work, you need to know the total number of folders and subfolders
 which is not always possible. Also it causes the output to print `Is a directory` every time it enters a new directory. Therefore a good solution to this problem is the `grep -r` command. This allows
 grep to recursively enter all the folders and files and look for the pattern and print out the line and the file name very it matches the pattern.  
 
 Some Examples are as follows :- 
 
 * In this example, we will use the command `grep -r` to find the words **Gateway of India** in the directory `written_2/`. We will use the command `grep -r "Gateway of India" written_2/` to print all the lines and files which contain that phrase.
   ```
   $ grep -r "Gateway of India" written_2/
   written_2/travel_guides/berlitz1/WhereToIndia.txt:        “ Gateway of India” still describes the main function of
   written_2/travel_guides/berlitz1/WhereToIndia.txt:        This site is marked today by the world famous Gateway of India — a
   ```
   As we can see, there are no lines in the output containing the sentence `is a directory` and lists out all instances of **Gateway of India** appearing the text files.
 
 * In this example, we will use the command `grep -r` to find the words **Lakers** in the directory `written_2/`. We will use the command `grep -r "Lakers" written_2/` to print all the lines and files which contain that phrase.
   ```
   $ grep -r "Lakers" written_2/
   written_2/travel_guides/berlitz1/WhatToLosAngeles.txt:        Lakers and the Clippers run the court at the new downtown Staples
   written_2/travel_guides/berlitz2/California-WhatToDo.txt:Basketball. Basketball is as popular in California as in the rest of the United States — the season lasts from October to April. Probably the best-known team in California is the Los Angeles Lakers.
   ```
   As we can see, there are no lines in the output containing the sentence `is a directory` and lists out all instances of **Lakers** appearing the text files.
   
In Week 4 and 5 we learned many new commands like `find`, `grep` and `less` using which we can manipulate and access data stored in text files. Using the Lab Report    3, we further increased out knowledge by practicing 8 new examples of different variations of `grep`. 
---

  

