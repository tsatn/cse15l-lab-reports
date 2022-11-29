# Lab Report 5 - Grading Script

Teresa Tian  
A16878664

## Part 1: grade.sh in a code block

```
rm -rf student-submission

#clone to local
git clone $1 student-submission
echo 'finished cloning'

#check file exist
if [ ! -e 'student-submission/ListExamples.java' ]
then
	echo 'ListExamples.java missing from submission'
	exit
fi

#copy test to submission folder
cp TestListExamples.java student-submission 
echo "setup test cases"

#compile
set -e
javac -classpath "lib/*" -d student-submission student-submission/*.java
echo "Succesfully Compiled, congrats!"
echo "Your grade: 100%"

#run junit

echo "Running tests..."
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > error.txt

cat error.txt
faliure =$(grep -i "Failures:" error.txt)

if[[$faliure == ""]]
then 
echo "You are Good, all test passd"
echo "Your grade: 100%"
fi

```

---

## Part 2: reported grade loaded in the browser 

Using Terminal to compile files to get the link to the local browser: 

<img width="703" alt="Screen Shot 2022-11-29 at 1 28 29 PM" src="https://user-images.githubusercontent.com/114328188/204652703-837dba03-63ed-46b2-95cf-418994970dd5.png">

After the brower is opened following the terminal link, type **/grade?repo=** in the web browser address: 

<img width="616" alt="Screen Shot 2022-11-29 at 1 38 44 PM" src="https://user-images.githubusercontent.com/114328188/204653940-0dd46072-9804-4ff9-a9ce-63619c8f9367.png">

Next, after the equal sign, add the link to the student submission and hit return. 

#### Student submission 1 ([2nd link]([https://github.com/ucsd-cse15l-f22/list-methods-compile-error](https://github.com/ucsd-cse15l-f22/list-methods-corrected)))
<img width="893" alt="Screen Shot 2022-11-29 at 1 43 52 PM" src="https://user-images.githubusercontent.com/114328188/204654500-9b95827f-7356-4367-bbfb-913d9962c82b.png">

#### Student submission 2 ([3rd link](https://github.com/ucsd-cse15l-f22/list-methods-compile-error))
<img width="811" alt="Screen Shot 2022-11-29 at 1 48 55 PM" src="https://user-images.githubusercontent.com/114328188/204655387-b703f09b-4f0a-442e-9203-0fad46d6ebbe.png">

#### Student submission 3 ([5th link](https://github.com/ucsd-cse15l-f22/list-methods-filename)))
<img width="780" alt="Screen Shot 2022-11-29 at 1 51 32 PM" src="https://user-images.githubusercontent.com/114328188/204656037-0b057a51-9a68-47fc-bbf6-ed7fac0ad856.png">

---

## Part 3: tracing the script

For each line with a command, what its standard output and standard error are for this run, and whether its return code was zero or nonzero

For each line with an if statement, whether the condition was true or false, and why

Indicate each line that does not run (maybe because it is in an if branch that doesn’t evaluate, or after an early exit)
