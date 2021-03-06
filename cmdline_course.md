---
layout: default
---

## Command-line Course
The aim of this course was to get the hang of a UNIX system and learn basic skills that could be useful in further courses on language technology. The main focus was to execute UNIX commands on a command-line and to learn to process text in useful ways. We were also taught how to use regular expressions for various text processing tasks, as well as how to write scripts and a simple program using `makefile`.
In addition, quite a few other things were worked with, such as installing and running programs, and using version control to facilitate working with projects.  
All in all, it has been a course with quite a lot of content that will surely come in handy later. The emphasis has been on gaining practical knowledge, while also learning more about how computers and programs work. 

### Week 1. Introduction to Command-line Environments
The first task was to download Ubuntu for Windows and create a UNIX account. We learned how to run basic commands on the command-line, like creating directories and files, and copying files between Windows and Linux.  
We also covered some differences between file formats, and learned to use nano text editor to create and edit text files.  
Some basic commands learned in the first week:
* `cp, rm, mv` (copying, deleting and renaming files)
* `mkdir` (creating a directory)
* `cd, ls` (changing directory and listing the contents of a directory)
* `pwd, whoami` (showing the current directory and showing the username)
* `wget` (downloading content from the web)
* `cat, less` (reading and viewing text files on screen)
* `nano` (creating and editing a file in the editor)

### Week 2. Navigating a UNIX System
In this part, we learned about users and permissions. The first lesson was about switching to the root user and setting up a password for it, and how to switch between different users using `su` and `sudo su`.  We also learned how to execute commands with `sudo` as a temporary root user.  After having grasped this, the next task was to change read, write and execute permissions of a file and change the owner of a file. Commands learned:
* `su, sudo su` (switch user)
* `chmod` (change access permissions)
* `chown` (change the owner of a file)

We also worked with a remote server, **taito**, and learned how to transfer and copy files securely from and to a secure server.
Commands learned:
* `ssh` (connect to a remote server)
* `sftp` (secure file transfer protocol)
* `scp` (secure copy)

Finally, there was also some information about how to view currently running processes and how to end them.  
* `ps aux` (view currently running processes)
* `top` (view processes that are taking the most resources)

### Week 3. Corpus Processing
This week’s focus was on text processing. Lots of new commands to process text files where introduced, such as 
* `head, tail` (show the beginning or the end of a file)
* `sort` (sort alphabetically)
* `wc` (word count)
* `uniq` (omit repeated lines)
* `tr` (translate = replace or remove characters)
* `sed` (stream editor, makes changes in a file without opening it)  

We also covered regular expressions and how to use them and `grep` (Global Regular Expressions Print) for searching tasks.  
Some useful Regex special characters that can be used with `grep –E`:  

| Metacharacter | Meaning                  |  
| :------------:| -------------------------|   
| .             | any character            |  
| *             | 0 or more occurrences    |  
| +             | 1 or more occurrences    |  
| ?             | optional                 |  
| ^             | beginning of a line      |  
| $             | end of a line            |  
| \s            | any whitespace character |  
| \b            | word boundary            |  


The third week included two text processing tasks. One of them was to create a frequency list for the Gutenberg text file _Life of Bee_.
One more important point in this task: commands can be chained together using pipes (`|`).
1. One word per line (replacing newlines, carriage return, newline, tab and space with a newline, so every word will begin a new line) and getting rid of empty lines (`-s`):  
  `cat life_of_bee.txt | tr -s '\n\r\t ' '\n'| `
2. Getting rid of punctuation marks (delete the complement of alphanumerics):  
   `tr -dc "A-Za-z0-9\n"" | `
3. Sorting it in alphabetical order and counting consecutive lines that have identical words in them:  
   `sort | uniq -c | `
4. Sorting it in reverse numerical order and redirecting it to a frequency list file:  
  `sort -nr > life_of_bee.freq`

### Week 4. Scripting and UNIX Configuration Files
In this week’s lessons we learned about Unix **environment variables**, which are variables that are set up in the shell when logging in. Each variable has a value assigned to it. We learned how to make an environment variable and how to add it to the **.bashrc** file, so it will be a permanent setting. We also looked at other things in the .bashrc file, such as how to add aliases, how to set up a nice command line prompt, and how to make changes in the PATH variable.  
This week we also did two text processing tasks, but instead of writing the commands straight to the command-line, we wrote a script in a text file with a .sh (shell script) extension. One of them was the frequency list task from the previous week, and the another was about creating a concordance list for a particular word, in this case, _queen_:  

![Corcordance for word queen](https://raw.githubusercontent.com/aarniolaura/aarniolaura.github.io/master/assets/img/concordance.jpg) 

Before writing the commands, there has to be `#! /bin/bash` written in the first line of the script, so it will be run by the bash shell.  
An example from the script where we are using `sed –E` to substitute everything before the center word (`$WF`) with the center word and 30 characters before it ( in other words everything before the 30 characters will be deleted):  
`sed -E "s/.*(.{$CONTEXT}$WF)/\1/" | `  
and then doing the same thing to every character after the center word + 30 characters:  
`sed -E "s/($WF.{$CONTEXT}).*/\1/" `  

### Week 5. Installing and Running Programs
This week we learned about running and installing software.
Before installing a program you need to also install libraries or other software that it depends on for it to function properly. **Package managers** take care of installing all these dependencies. We tried this in practice by installing ImageMagick with `apt-get`. We also used Python’s package manager pip to install python packages such as torchvision.  
We also used `make` to compile a C program manually. For this we first downloaded the program file, then prepared the compilation with `./configure`. When the makefile was ready, we used `make` to do the required connections, and finally `make install` to finish the installation of the program.

### Week 6. Version Control
Sixth week consisted mostly of **Git** and **GitHub** tutorials. It is useful to use version control so we can keep track of all the modifications made. That way it is also possible to return to an earlier version of the code that is still working properly. 
We learned to use some fundamental git commands in the command line, such as:
* `git init` (create a local repository)
* `git status` (check if the changes have been added from the working directory to the staging area, and if there are any changes to be committed to the git repository)
* `git add –A` (add all the changes to the staging area)
* `git commit –m “message”` (commit all changes to the repository)
* `git pull origin master` (get the newest version of the code)
* `git push origin master` (to push the committed changes to the remote repository) 

In addition, we learned how to make separate branches to the project, which can later be merged with the master branch.

### Week 7. Building Webpages Using GitHub Pages
The task of the last week was to build a homepage in GitHub pages using **Jekyll** – which generates the webpage – and **Markdown** – which converts the plain text to HTML.  
At first this seemed like a very challenging task, maybe a bit too much for a basic course. There were a lot of difficulties with installing Jekyll, because there were some libraries or gems missing, but luckily it was nothing a bit a googling couldn’t fix.  
However, as it turns out, Jekyll is quite easy to use. You don’t really need to know much to get started, since Jekyll does all the work in getting the site working. Despite all the difficulties it has been a rewarding project.
