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

## part 2: reported grade loaded in the browser 

#### student submission 1 
#### student submission 2 
#### student submission 3


## part 3: tracing the script

