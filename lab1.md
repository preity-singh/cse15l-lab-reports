# For each of the commands `cd`, `ls`, and `cat`, and using the workspace you created in this lab:

## **Share an example of using the command with no arguments.**
* `cd` with no argument goes to the `home` directory since that is the default. The output is not an error. This examples shows that the working directory was `/home`.

![Image](NoArgumentCD.png)
---

* `ls` command with no argument will default to showing the names of the files of the current working directory. This working directory in this example was the `home` directory, so the terminal listed out the only file in that directory: `lecture1`. The output didn't have an error.

![Image](NoArgumentLS.png)
---

* `cat` command with no argument prints a blank line. Since the `cat` command displays the contens of a specified file and I passed no file name in the argument, the terminal will print nothing. The `cat` command can also take input directly from the terminal, so passing the command without any arguments is like passing that `cat` command with an empty string. (the output is would be an empty string). The working directory is the `home` directory

![Image](noArgumentCAT.png)
---

## **Share an example of using the command with a path to a directory as an argument.**
* `cd` command with a path to a directory as an argument will change the working directory to the specific directory. This command doesn't produce any errors. By using "/" adds another step in the navigation. The working directory is `/home/lecture1/messages`.
  
![Image](DirectoryCD.png)
![Image](PathCD.png)
---

* `ls`command with a path to a specific directory as an argument will list out all the files of the specified directory. The example below didn't produce an error and the argument `lecture1` displayed all the files under the `lecture1` in the directory. The working directory is `home`.

![Image](DirectoryLS.png)
---

* when using the `cat` command, the terminal expects a file name as the argument in order to print the contents of the argument. When the argument is instead a path to a directory, the terminal is unable to print anything, so the output is an error. This is why the output prints "...is a directory" indicating that the argument type was incorrect. The working directory is `/home`.

![Image](DirectoryCAT.png)
---

## **Share an example of using the command with a path to a file as an argument.**
* `cd` command with a path to a file as an argument prints an error message, part of the message including "...not a directory." Since the `cd` command lets you change directories, the terminal expects a directory name as the argument, not a file name. When the command was run, the initial directory was the `home` directory. 
  
![Image](FileCD.png)
---

* `ls` command with a file name as an argument prints the path to the file. The working directory is the `home` directory. The terminal outputs what is accessible from the given path.

![Image](FileLS.png)
---

* The `cat` command expects a file name as an argument, so the command line successfully printed the contents of the specified file name. In this example below, the working directory is the `home` directory and I wanted to see contents of the `en-us.txt` file under the messages directory. The terminal printed "Hello World!" 

![Image](FileCAT.png)
