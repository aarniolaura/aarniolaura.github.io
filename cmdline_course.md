---
layout: default
---

## Command-line Course
You should write a short overall introduction to the course and
one section for every week (for the final week, you can talk about 
Jekyll and Github Pages). Please use appropriate headers for each 
section. You should briefly describe the main content of each week 
and also briefly reflect on what you learned during the week 
(maybe 1-3 sentences for reflection). You need to include at least one 
list, image and table on the cmdline-course page. 

### Week 1. Introduction to Command-line Environments
The first task was to download Ubuntu for Windows and create a UNIX account. We learned how to run basic commands on the command-line, like creating directories and files, and copying files between Windows and Linux.  
We also covered some differences between file formats, and learned to use nano text editor to create and edit text files. 
Some basic commands learned in the first week:
* cp, rm, mv 
* ls, cd, mkdir
* pwd, whoami, wget
* cat, less, nano

### Week 2. Navigating a UNIX System
In this part, we learned about users and permissions. The first lesson was about switching to the root user and setting up a password for it, and how to switch between different users using su and sudo su.  We also learned how to execute commands with sudo as a temporary root user.  After having grasped this, the next task was to change read, write and execute permissions of a file and change the owner of a file.  
Commands learned:
* su, sudo su (switch user)
* chmod (change access permissions)
* chown (change the owner of a file)

We also worked with a remote server, taito, and learned how to transfer and copy files securely from and to a secure server.
Commands learned:
* ssh (connect to a remote server)
* sftp (secure file transfer protocol)
* scp (secure copy)

Finally, there was also some information about how to view currently running processes and how to end them.  
* `ps aux` (view currently running processes)
* `top` (view processes that are taking the most resources)

### Week 3. Corpus Processing
This week’s focus was on text processing. Lots of new commands to process text files where introduced, such as 
* head, tail
* sort
* wc (word count)
* uniq
* tr
* sed (stream editor, makes changes in a file without opening it)  

We also covered regular expressions and how to use them and `grep` (Global Regular Expressions Print) for searching tasks.  

The third week included two text processing tasks:
1. Creating a frequency list for the Gutenberg text file Life of Bee  
`cat life_of_bee.txt  | dos2unix | sed 's/^$/#/' | tr '\n' ' ' | sed -E 's/([.?!]) ([A-Z])/\1# \2/g' | sed -E 's/([IVX][.])#/\1/g' | tr '#' '\n' | sed 's/^ *//' | sed 's/ *$//' | grep -v "^$" | > life_of_bee.sent`

One more important point in this task: commands can be chained together using pipes (`|`).

2. Creating a sentence per line file for Life of Bee  
`cat life_of_bee.txt  | dos2unix | sed 's/^$/#/' | tr '\n' ' ' | sed -E 's/([.?!]) ([A-Z])/\1# \2/g' | sed -E 's/([IVX][.])#/\1/g' | tr '#' '\n' | sed 's/^ *//' | sed 's/ *$//' | grep -v "^$" | > life_of_bee.sent`


### Week 4. Scripting and UNIX Configuration Files

### Week 5. Installing and Running Programs

### Week 6. Version Control

### Week 7. Building Webpages Using GitHub Pages

