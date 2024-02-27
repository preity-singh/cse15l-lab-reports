For the lab report this week, reproduce the task from above on your own. For each numbered step starting right after the timer (so steps 4-9), take a screenshot, and write down exactly **which keys you pressed to get to that step.** For special characters like <enter> or <tab>, write them in angle brackets with code formatting. Then, summarize the commands you ran and what the **effect of those keypresses were.**

For example, when you run the tests, you might want to use the **up arrow or Ctrl-R** to access your bash history rather than typing in the full command with classpath, etc. You might say something like this accompanying the screenshot for running the tests:

Keys pressed: <up><up><up><up><enter>, <up><up><up><up><enter> The javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java command was 4 up in the search history, so I used up arrow to access it. Then the java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ... command was 4 up in the history, so I accessed and ran it in the same way.

STEPS 4-9:
### 4: Log into ieng6
* `ssh prs009@ieng6.ucsd.edu`
* entered password
*add picture*

### 5: Clone your fork of the repository from your Github account (using the SSH URL)
* My terminal didn't save for this part, so I couldn't take a screenshot but I have the block code.
```
git clone git@github.com:preity-singh/lab7.git
```

### 6: Run the tests, demonstrating that they fail
* `bash test.sh`
*add picture*

### 7: Edit the code file to fix the failing test
* (started at the end of the file) 6`k`-11`l`-`x`-`i`-(insert 2)-<escape>(returns to normal mode)-`:wq` (to save the quit)-<enter>
*add picture*

### 8: Run the tests, demonstrating that they now succeed
**NOT WORKING**

### 9: Commit and push the resulting change to your Github account (you can pick any commit message!)
