---
layout: default
---

## Command-Line Course

During the 7 weeks of this course I learned how to use the command line and gained a much better understanding of how to interact with my own computer. I have learned a whole lot of things for a very short period and am eager to start applying them for my actual work. And most importantly - I learned that it's okay not have the solution for everything immediately available in your head - the answer is at the tip of your fingers with a quick google search!

### Content
1. Introduction
2. Navigating a UNIX System
3. Basic Corpus Processing
4. Advanced Corpus Processing
5. Scripting and Configuration Files
6. Installing and Running Programs
7. Version Control

#### Week 1: Introduction
 The first week was a gentle introduction into the command-line environment. We learned simple commands such as:  `ls, cd, wget, less, mkdir, cp, mv, and rm`  


 We also learned how to open and edit a file in a text editor. I personally find emacs a little confusing to work with, hence I prefer using nano.


#### Week 2: Navigating a UNIX System
 The second week provided a deeper dive into navigation within the command line and introduced us to changing permissions for files, running commands in the background, and connecting to remote servers. Here are some of the commands that were covered:

`cp -R` - copy directory  
`rmdir` - remove empty directory  
`rm -R` - remove directory with content


#### Week 3: Introduction to Corpus Processing
 Week 3 was about different character encoding systems, conversion, and basic corpus processing. We also got to play around with regular expressions and learn how to use them in a fun and easy way [here](https://regexcrossword.com/). Here's a useful cheatsheet:

| RegEx   | Represents                    |
| --------|:------------------------------|
|.        | any character except newline  |
|\w \d \s | word, digit, whitespace       |
|\W \D \S | not word, digit, whitespace   |
|[abc]    | any of a, b, or c             |
|[^abc]   | not a, b, or c                |
|[a-g]    | character between a-g         |
|^abc$    | start / end of string         |
|\b \B    | word, not-word boundary       |
|\t \n \r | tab, linefeed, carriage return|
|a* a+ a? | 0 or more, 1 or more, 0 or 1  |

#### Week 4: Advanced Corpus Processing
 Things started getting serious! We were introduced to the sed command and used it to make a frequency list, sentence-per-line file and lists of n-grams from text files. We did lots of fun things such as finding which is the most common sentence-final word in the book *The Life of the Bee* by Maurice Maeterlinck:

```
cat life_of_bee.sent | sed -E 's/.* //' | tr -cd "A-Za-z0-9\n'" | sort | uniq -c | sort -nr | head -1
```

Turns out the answer is... **hive**!




#### Week 5: Scripting and UNIX Configuration Files
 Week 5 had us writing simple scripts and defining values of variables with `export`. We also modified the prompt and learned how to make shortcuts for commands that we most often use.

 I couldn't figure out how to make the script that takes an English adjective and prints out its comparative form, but it all became clear when I saw Miikka's solution:

```
FINAL_LETTER=`echo $1 | sed -E 's/.*(.)/\1/'`
STEM=`echo $1 | sed -E 's/(.*)./\1/'

if [ $FINAL_LETTER == "y" ]
then
 echo $STEM ier | tr -d ' '
else
 if [ $FINAL_LETTER == "e" ]
  then
    echo $STEM er | tr -d ' '
  else
    echo $STEM $FINAL_LETTER er | tr -d ' '
  fi
fi
```


#### Week 6: Installing and Running Programs
 During this week we learned how to give commands as the root user with `sudo`, we installed software with `apt-get` and python packages with `pip`. We created python virtual environments and played around with Makefile.


#### Week 7: Version Control
 Week 7 taught us how to use version control. I have had some experience with GitHub using TortoiseGit, but it was interesting for me to learn how to manage my repository from the command line. I'm still more comfortable using the Windows Shell extension, but perhaps in the future I will gain more confidence writing `git` commands directly in my command line.

---
And there it is! The course is finished! I hope to be able to apply the newly acquired knowledge in my research projects and to continue learning new cool things.
