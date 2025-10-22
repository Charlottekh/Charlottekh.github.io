---
layout: default
---

# <font color="pink"> Command-line Tools for Linguists Fall 2025</font>


This course teaches the basics of command-line tools, like moving through directories, editing files, sorting content of files and making scripts. 
It is tailored towards linguists, which means that it focuses on commands relevant for computational linguistics and language technology. 
It is taught at the university of Helsinki.

## <font color="pink"> Module 1: Introduction to Command Line Environments </font>
In this module linguists are introduced to Ubuntu. They are taught how to move through directories, display content of text files and edit those files.
A glimpse of the commands used in this week:

commands | what it does
---|---
`ls` | show a list of all (hidden) files in this directory
`pwd` | prints working directory 
`whoami` | prints current user
`wget` | can be used to download a file, for example: `wget https://www.gutenberg.org/files/215/215-0.txt` download a file from Project Gutenberg
`mv` | moves a file from one directory to another
`cat` | prints the text of a file 
`less` | shows the text of a file in a more readable format
`cp` | copies a file 
`rm` | removes a file (or directory)
`mkdir` | makes a directory
`cd` | changes directory
`head` | print the beginning of a file
`wc` | tells you the wordcount

For all these commands, there are optional parameters to use when you want it to behave just a little different. Try using `command --help` and see what the options are!

Personally, I have saved a cd to my windows directory with my masters folder and my most used folder in the unix system. I can mv and cp files from my Windowsstation to my Linux filestation in Ubuntu easily that way

## <font color="pink"> Module 2: Text Processing in UNIX </font>

In module one we learned how to open a file (with nano, cat, or less) and in module 2 we learned how to process these texts.
This can be useful to make wordlists, for example.

Some useful combinations:

commands | what it does
---|---
`uniq -i` | Returns a list of all unique words, case insensitive
`sort -f` | Returns a list of all words in alphabetical order, ignoring capital letters
`tr -s "[:space:][:punct:]" "\n"` | Puts every word on a new line by removing punctuation and spaces, and squeezes double spaces with -s 

> `cat myfile.txt | tr -s "[:space:][:punct:]" "\n" | sort -f | uniq -i` 

Combines the above and gives you a wordlist! However, whenever making wordlists it is always important to look at the file you're working on, as it is never a one size fits all solution

Another combination of commands is this:

> `cat life_of_bee.txt | tr -s "\n\r\t "  "\n" | tr -dc "[:aln>cat life_of_bee.txt | tr -s "\n\r\t "  "\n" | tr -dc "[:alnum:]\n'" | sort | uniq -c | sort -nr  > life_of_bee.freq``

sorted word freq list

> `| tr -dc "A-Za-z0-9\n'" ` en `tr -dc "[:alnum:]\n'"`

Sometimes it is necessary to check the filetype of a file and to convert it.

file ..txt
iconv -f ISO-8859-1 -t UTF-8 katinka_rabe.txt > katinka_rabe.utf-8.txt
dos2unix katinka_rabe.utf-8.txt


## <font color="pink"> Module 3: Scripting, Configuration Files and Installing Programs </font>

When you need to process a lot of text files, it is easier to combine the commands into *scripts*. That is what this module is all about.

A script can look as simple as this:

```bash
# !/bin/bash

# This script prints the word script

echo script
```


But what makes them powerful is that you can use variables and give them conditional clauses, like here:

```bash
# !/bin/bash

# This program makes the comparative form
# of an English adjective ending in a consonant

while read -r line;

do
       if [ "${line: -1}" = "y" ]; then
               echo $line | sed "s/y$/ier/"
       else
               echo "${line}er"
       fi

done < "$1"
```

This functions used the first argument ($1) and uses it throughout the function. 

Another powerful tool learned during this module is installing software and packages.
Using `sudo`, which gives you the power of the rootuser to install software. This can look like:

>`sudo apt install python3`

Which installs Python 3 for you.
When you continue to work with Python, you will come across Python packages. These can be installed with `pip`, such as:

>`pip install pandas`

This command installs the pandas library for you.
## <font color="pink"> Module 4: Using ssh, scp and Version Control </font>

This module focused on process, remote servers and version control.


Version control was introduced using github. It teaches you how to clone a rep, push and pull. revrt changes and other important tools when working on a project.
There exist numerous cheatsheets for this online, here is just one of them:

<img src="assets/images/cheatsheet.png" alt="Photo" hspace="20" width="30%" align="right"/>
