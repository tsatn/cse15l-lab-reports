# CSE15L Week 1 Lab-Report 
Teresa Tian 
A16878664
## Step 1 - Installing VScode 

To download VScode for your own Mac, follow this link to the VScode official website: https://code.visualstudio.com/ 
Click the blue button on the web page: 

After VScode is successfully downloaded, open it on your computer and the window should look like the image below: 

## Step 2 - Remotely Connecting

When VScode is open, go to the top bar on your mac where it says “Terminal”.

Click on it, and choose “New Terminal” on the menu. 
In the terminal, type $ ssh shtian@ieng6.ucsd.edu
* shtian is the tritonlink username
* Enter the password for the ucsd student account 
* This link allows you to find your course-specific account name and reset your password: https://sdacs.ucsd.edu/~icc/index.php 

When asked “Are you sure you want to continue connecting”, type $ yes

Once you type in your correct password and log in into the remote server, you should have the output below (shown in the image): 





<img width="374" alt="calendar " src="https://user-images.githubusercontent.com/114328188/193386625-03f3cecf-4160-4087-a975-34f70833328c.png">

## Step 3 - Trying Some Commands 

Here is a list of commands to experiment on the terminal: 

* cd ~
* cd 
* ls -lat
* ls -a
* ls <directory>, for example, ls /home/linux/ieng6/cs15lfa22/shtian
* cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
* cat /home/linux/ieng6/cs15lfa22/public/hello.txt

Below is an example of commands I ran on my terminal and playing with the change of directories:

  
After this, we log out from the remote server. To do this, type $ exit on the Terminal.

  
## Step 4 - Moving Files with scp 

> The command called scp gives us another way to copy files from the client computer (your laptop/Mac) to the remote computer.

* While VScode is open, go to the top menu bar, click on “File”, select “New File”
* Type “java” into the pop-up search bar on the VScode window. 
* Name the new file WhereAmI.java

* Copy the block of code below into the new java file.

Below is a screenshot of the procedure
* Compile: $ javac WhereAmI.java
* Run: $ java WhereAmI
* Type in: $ scp WhereAmI.java shtian@ieng6.ucsd.edu:~/
* Enter password
* Then, compile and run the same java file again 

## Step 5 - Setting an SSH Key

> Here we are finding a more convenient method to log into the remote computer and perform our tasks using what’s called ssh keys. Ssh keygen allows us to save our passwords as the public for logging in, and with this method, the process will become more convenient and we will not have to type in our passwords every time.  
  
Below is the detailed procedure for how to do this: 

* (your client computer)
* Type $ ssh-keygen
* Type:  /Users/tteresattian/.ssh/id_rsa
* When asked Overwrite? Type: y (for yes)
* Enter pw twice 
* Type: $ ssh shtian@ieng6.ucsd.edu
* Enter pw 

* (server)
* Type: $ mkdir .ssh
* Type: logout
 
* (returns to your client computer)
* Type: scp /Users/tteresattian/.ssh/id_rsa.pub shtian@ieng6.ucsd.edu:~/.ssh/authorized_keys 
* Enter pw 


## Step 6 - Optimizing Remote Running

