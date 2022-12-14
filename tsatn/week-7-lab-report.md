# Lab Report 4 (Week 7) - Vim 

Teresa Tian, A16878664


## Part One 

> The purpose of this part of the lab is based on using the Vim commands involved in Lab 6 and finding the shortest sequence of Vim commands that would complete the task.

***Set up:***
1. Open a New Terminal in VS Code 
2. Type git clone https://github.com/ucsd-cse15l-f22/skill-demo1 week6-skill-demo1
3. ls and type cd week6-skill-demo1
4. vim DocSearchServer.java

These steps allow you to clone the repository and use vim to edit the file on the terminal

<img width="470" alt="Screen Shot 2022-11-17 at 1 53 45 PM" src="https://user-images.githubusercontent.com/114328188/202567980-237436fc-c510-444d-b60f-291a73629964.png">

***Chosen Task:*** Changing the name of the start parameter and its uses to base

***Overall Step:***
```
/start<enter>cebase<esc>n.n.:w<enter> 
```

**Step 1:** /start<Enter> 
>This command searches for the word start and cursor jumps to the front of the word start

<img width="800" alt="Screen Shot 2022-11-17 at 5 50 06 PM" src="https://user-images.githubusercontent.com/114328188/202599164-6d578ca8-2d4e-4800-bfd9-f5bd3f98838c.png">
  
**Step 2:** ce
>This command enters insert mode and delete the word start

<img width="695" alt="Screen Shot 2022-11-17 at 6 23 33 PM" src="https://user-images.githubusercontent.com/114328188/202602279-d0718f85-bad8-46ac-9ddb-5c45860ef683.png">
  
**Step 3:** base<Esc>
>Changes the word start to base and quits the insert mode
  
<img width="767" alt="Screen Shot 2022-11-17 at 6 39 23 PM" src="https://user-images.githubusercontent.com/114328188/202604316-a00f67c4-b159-4bac-83ec-ef91be761fdd.png">

**Step 4:** n 
>Goes back to the previous command and execute it, which is re-doing step 1: /start<Enter> 
  
<img width="772" alt="Screen Shot 2022-11-17 at 6 42 16 PM" src="https://user-images.githubusercontent.com/114328188/202604680-b4afc86a-ed1a-43b9-9575-d67f2ef066d1.png">

**Step 5:**
Since there are only 2 more occurrences of the word start, we repeat steps 2 to 4 twice until all of the places where start appears are changes to base

**Step 6:** :wq
>Saves all of the changes 
<img width="771" alt="Screen Shot 2022-11-17 at 6 58 11 PM" src="https://user-images.githubusercontent.com/114328188/202606726-2f485490-f212-4e22-8733-bfc93aa82faf.png">
  
---
## Part Two 
  
a. Report how long it took you to make the edit in seconds in both styles, and any difficulties or details that came up in doing so.
  
  1. using scp: editing the file from the local computer and putting it to the remote server using scp took me 10 minutes.
  
  2. using ssh: logging into the remote using ssh and editing the file took me 8 minutes.
  
b. Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

> I prefer method 2 which is logging into the remote using ssh and editing the file. I think this method is better since you would be able to save more time from not having to always updating the remote and re-typing the passcodes.
  
c. What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

> I believe that the complexity or the amount of the changes that I have to make in the file is crucial to which method I am going to use. If I only have to make some minor changes, I would choose to ssh log in into remote and edit from there directly. If I have to make lots of edits, I would choose to finish making all of the changes on my local computer and scp the changes to the remote.

  
  
  
