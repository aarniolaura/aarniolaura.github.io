---
layout: default
---

## Command-line Course
The aim of this course was to get the hang of a UNIX system and learn basic skills that could be useful in further courses on language technology. The main focus was to execute UNIX commands on a command-line and to learn to process text in useful ways (for building a corpus for example). We were also taught how to use regular expressions for various text processing tasks, as well as how to write scripts and a simple program using `makefile`.
In addition, quite a few other things were worked with, such as installing and running programs, and using version control to facilitate working with projects.  
All in all, it has been a course with quite a lot of content that will surely come in handy later. The emphasis has been on gaining practical knowledge, while also learning more about how computers and programs work. 

### Week 1. Introduction to Command-line Environments
The first task was to download Ubuntu for Windows and create a UNIX account. We learned how to run basic commands on the command-line, like creating directories and files, and copying files between Windows and Linux.  
We also covered some differences between file formats, and learned to use nano text editor to create and edit text files. 
Some basic commands learned in the first week:
* `cp, rm, mv` 
* `ls, cd, mkdir`
* `pwd, whoami, wget`
* `cat, less, nano`

### Week 2. Navigating a UNIX System
In this part, we learned about users and permissions. The first lesson was about switching to the root user and setting up a password for it, and how to switch between different users using `su` and `sudo su`.  We also learned how to execute commands with sudo as a temporary root user.  After having grasped this, the next task was to change read, write and execute permissions of a file and change the owner of a file. Commands learned:
* `su, sudo su` (switch user)
* `chmod` (change access permissions)
* `chown` (change the owner of a file)

We also worked with a remote server, taito, and learned how to transfer and copy files securely from and to a secure server.
Commands learned:
* `ssh` (connect to a remote server)
* `sftp` (secure file transfer protocol)
* `scp` (secure copy)

Finally, there was also some information about how to view currently running processes and how to end them.  
* `ps aux` (view currently running processes)
* `top` (view processes that are taking the most resources)

### Week 3. Corpus Processing
This week’s focus was on text processing. Lots of new commands to process text files where introduced, such as 
* `head, tail`(show the beginning or the end of a file)
* `sort`(sort alphabetically)
* `wc` (word count)
* `uniq` (omit repeated lines)
* `tr` (translate = replace or remove characters)
* `sed` (stream editor, makes changes in a file without opening it)  

We also covered regular expressions and how to use them and `grep` (Global Regular Expressions Print) for searching tasks.  

The third week included two text processing tasks. One of them was to create a frequency list for the Gutenberg text file Life of Bee.
One more important point in this task: commands can be chained together using pipes (`|`).
1. One word per line (replacing newlines, carriage return, newline, tab and space with a newline, so every word will begin a new line) and getting rid of empty lines (`-s`)  
  `cat life_of_bee.txt | tr -s '\n\r\t ' '\n'| `
2. Getting rid of punctuation marks (delete the complement of alphanumerics)  
   `tr -dc "A-Za-z0-9\n'" | `
3. Sorting it in alphabetical order and counting consecutive lines that have identical words in them  
   `sort | uniq -c | `
4. Sorting it in reverse numerical order and redirecting it to a frequency list file  
  `sort -nr > life_of_bee.freq`

### Week 4. Scripting and UNIX Configuration Files
In this week’s lessons we learned about Unix environment variables, which are variables that are set up in the shell when logging in. Each variable has a value assigned to it. We learned how to make an environment variable and how to add it to the .bashrc file, so it will be a permanent setting. We also looked at other things in the .bashrc file, such as how to add aliases, how to set up a nice command line prompt, and how to make changes in the PATH variable.  
Scripts

### Week 5. Installing and Running Programs
This week we learned about running and installing software.
Before installing a program you need to also install libraries or other software that it depends on for it to function properly. Package managers take care of installing all the dependencies. We tried this in practice by installing ImageMagick with `apt-get`. We also used Python’s package manager pip to install python packages such as torchvision.  
We also used `make` to compile a C program manually. For this we first downloaded the program file, then prepared the compilation with `./configure`. When the makefile was ready, we used `make` to do the required connections, and finally `make install` to finish the installation of the program.

### Week 6. Version Control
Sixth week consisted mostly of Git and GitHub tutorials. It is useful to use version control so we can keep track of all the modifications made. That way it is also possible to return to an earlier version of the code that is still working properly. 
We learned to use some fundamental git commands in the command line, such as:
* `git init` (to create a local repository)
* `git status` (to check if the changes have been added from the working directory to the staging area, and if there are any changes to be committed to the git repository)
* `git add –A` (to add all the changes to the staging area)
* `git commit –m “message”` (to commit all changes to the repository)
* `git pull origin master` (to get the newest version of the code)
* `git push origin master` (to push the committed changes to the remote repository)
In addition, we learned how to make new branches, which can later be merged with the master branch.

### Week 7. Building Webpages Using GitHub Pages
The last week of the course was to do a project using GitHub pages, Jekyll and Markdown.
