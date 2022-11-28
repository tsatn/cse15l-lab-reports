# Lab Report 5 

Teresa Tian 

A16878664

---

## Part 1: grade.sh in a code block
```
	#clone to local
	if [ -d 'student-submission' ]
	then
		rm -rf student-submission
		echo 'old submission purged'
	fi

	if [ ! $# -eq 0 ]
	then
		git clone $1 student-submission
		echo 'finished cloning'
	else
		echo 'no repo supplied'
	fi

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
	echo "Succesfully Compiled"

	#run junit

```

## Part 2: reported grade loaded in the browser 

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
