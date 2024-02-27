# Lab Report 4

## STEPS 4-9:

### 4: Log into ieng6
* `ssh prs009@ieng6.ucsd.edu<enter>`
* entered password
![Image](loginIeng6.png)

### 5: Clone your fork of the repository from your Github account (using the SSH URL)
* My terminal didn't save for this part, so I couldn't take a screenshot but I have the block code. Also, for reference, I copied my ssh url from GitHub.
```
git clone<Command-V><enter>
```

### 6: Run the tests, demonstrating that they fail
* `bash test.sh<enter>`

![Image](preFixTest.png)

### 7: Edit the code file to fix the failing test
* `vim ListExamples.java<enter>`
* `44Gexi2<esc>:wq<enter>`

![Image](fixTest.png)

### 8: Run the tests, demonstrating that they now succeed
* `<up><up><enter>`

![Image](testRun.png)

### 9: Commit and push the resulting change to your Github account (you can pick any commit message!)
* `git add List<tab><enter>`
* `git commit -m "lab 4 report commit"<enter>`
* `git push origin main<enter>`

![Image](gitPushCommit.png)
