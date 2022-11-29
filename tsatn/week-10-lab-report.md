# Lab Report 5 - Grading Script

Teresa Tian  A16878664

---

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

## Part 2: reported grade loaded in the browser 

Getting the link to the local browser:

<img width="703" alt="Screen Shot 2022-11-29 at 1 28 29 PM" src="https://user-images.githubusercontent.com/114328188/204652703-837dba03-63ed-46b2-95cf-418994970dd5.png">


#### student submission 1 ([3rd link](https://github.com/ucsd-cse15l-f22/list-methods-compile-error))

<img width="820" alt="Screen Shot 2022-11-28 at 11 44 37 AM" src="https://user-images.githubusercontent.com/114328188/204366892-f11aff34-e59a-441a-ac16-43bfbe91332a.png">

#### student submission 2 ([2nd link](https://github.com/ucsd-cse15l-f22/list-methods-corrected))

<img width="860" alt="Screen Shot 2022-11-28 at 11 40 58 AM" src="https://user-images.githubusercontent.com/114328188/204366577-f3398778-07cf-443e-80c6-0e3f28d89701.png">

#### student submission 3 ([4th link](https://github.com/ucsd-cse15l-f22/list-methods-signature))
<img width="794" alt="Screen Shot 2022-11-28 at 11 46 07 AM" src="https://user-images.githubusercontent.com/114328188/204367114-88999d03-4fc9-449e-90c5-be617e4c3fc1.png">

## Part 3: tracing the script

For each line with a command, what its standard output and standard error are for this run, and whether its return code was zero or nonzero

For each line with an if statement, whether the condition was true or false, and why

Indicate each line that does not run (maybe because it is in an if branch that doesn’t evaluate, or after an early exit)
