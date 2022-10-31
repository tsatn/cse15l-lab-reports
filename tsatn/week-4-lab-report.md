# CSE 15L Week 5 Lab Report  

## Find Linux command

Teresa Tian,  A16878664

### 1. find -name option

_Example 1.1_

    $ find ./technical -name "chapter-1.txt"
    
Output: 

    ./technical/911report/chapter-1.txt
    
The command above searches a file called "chapter-1.txt" within the folder ./technical. It will be useful for user who try to find a file within a nested directory system. 


_Example 1.2_

    $ find ./technical -name "chapter-13.*.txt"
    
Output: 

    ./technical/911report/chapter-13.4.txt
    ./technical/911report/chapter-13.5.txt
    ./technical/911report/chapter-13.1.txt
    ./technical/911report/chapter-13.2.txt
    ./technical/911report/chapter-13.3.txt
    
The command above searches files within the "technical" folder with the filename containing "chapter-13.?.txt", where ? can be replaced by any number if the file exists in the nested directory system within technical repository.  


_Example 1.3_

    $ find . -name "bill.txt"
    
Output: 

    ./technical/government/Env_Prot_Agen/bill.txt
    
The command above searches a file called "bill.txt" under the current working directory, the command will search through the all the folders within the current repository and find the relative path to that file. 
   

### 2. find -type option

The find -type option specifies the file type that the command wants to search for.

Possible type:

    d - directory
    f - file
    l - symbolic link
    s - socket
    p - named pipe (used for FIFO)
    b - block special (usually a hard drive designation)

_Example 2.1_

    $ find . -type d -name "About_LSC"
    
Output: 

    ./technical/government/About_LSC
    
    
This command above searches for a directory with name "About_LSC" within the current directory, and it will return the relative path to the directory under the current directory.


_Example 2.2_

    $ find . -type f -name "ai*"
    
Output: 

    ./technical/government/Gen_Account_Office/ai00134.txt
    ./technical/government/Gen_Account_Office/ai9868.txt
    ./technical/government/Gen_Account_Office/ai2132.txt
    
The command above searches for all the files under the current directory that starts with "ai". 


_Example 2.3_

    $ find ./technical -type d
    
Output: 

    ./technical
    ./technical/government
    ./technical/government/About_LSC
    ./technical/government/Env_Prot_Agen
    ./technical/government/Alcohol_Problems
    ./technical/government/Gen_Account_Office
    ./technical/government/Post_Rate_Comm
    ./technical/government/Media
    ./technical/plos
    ./technical/biomed
    ./technical/911report
    
The command above searches for all the directories under the directory "./technical" and return the relative path for each of the directories. 


### 3. find -size option

This command finds all the files with size specified by the -size option command

    `b'    for 512-byte blocks (this is the default if no
                     suffix is used)

    `c'    for bytes

    `w'    for two-byte words

    `k'    for kilobytes (KiB, units of 1024 bytes)

    `M'    for megabytes (MiB, units of 1024 * 1024 = 1048576
           bytes)

    `G'    for gigabytes (GiB, units of 1024 * 1024 * 1024 =
           1073741824 bytes)

_Example 3.1_

    $ find . -size +200k
    
Output: 

    ./lib/junit-4.13.2.jar
    ./.git/objects/pack/pack-32b7da9b0ed4fea250c5980741abee3e122c9e8c.pack
    ./technical/government/About_LSC/commission_report.txt
    ./technical/government/Env_Prot_Agen/bill.txt
    ./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
    ./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
    ./technical/government/Gen_Account_Office/d01591sp.txt
    ./technical/911report/chapter-13.4.txt
    ./technical/911report/chapter-13.5.txt
    ./technical/911report/chapter-3.txt
    
    
This command above searches for all the files with filesize greater than 200 kilobyte. It will be useful when we want to filter out files with large filesize or filter out all the files under a threshold filesize. 


_Example 3.2_

    $ find . -size +200k -size -220k
    
Output: 

    ./technical/government/About_LSC/commission_report.txt
    
The command above searches for all the files under the current directory that have the filesize under the range between 200 kilobytes and 220 kilobytes.


_Example 3.3_

    $ find . -type d -size +1k -size -5k
    
Output: 

    ./technical/government/Gen_Account_Office
    ./technical/government/Media
    
The command above searches for all the directories under the current directory with the directory size under the range between 1 kilobytes and 5 kilobytes.
