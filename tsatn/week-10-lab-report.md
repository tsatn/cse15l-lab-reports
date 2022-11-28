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

#### student submission 1 

#### student submission 2 

#### student submission 3


## Part 3: tracing the script

For each line with a command, what its standard output and standard error are for this run, and whether its return code was zero or nonzero

For each line with an if statement, whether the condition was true or false, and why

Indicate each line that does not run (maybe because it is in an if branch that doesn’t evaluate, or after an early exit)
