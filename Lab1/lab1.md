# CSCE215 - Required lab 1

The following points will be discussed in the first required lab.

## SSH Linux Machines

[ssh](https://linux.die.net/man/1/ssh) will allow students to log in into a remote computer and execute commands in the remote machine. In our case, executing the commands in the [Linux Machines in the Swearingen Labs](https://cse.sc.edu/resources/workstations).

For connecting we need the following information:
- Authorized user id (your USCID). Example: *fvilchez*
- Remote computer hostname or IP address. Example: *L<span>-1D43-01.cs</span>e.s<span>c.edu</span>*
- Connection port. In our case, port *222*.

Example:

`ssh -p 222 fvilchez@L-1D43-01.cse.sc.edu`

*Pause for questions.*

## Review some commands

- `echo`: Print a message
- `pwd`: Current directory
- `ls`: List files
- `touch`: Create empty file
- `mkdir`: Create directory
- `mv`: Move or rename a file or directory

*Pause for questions.*

- `cd`: Change directory
- `ls -a`: List files, include hidden files
- `.` and `..`: Current and previous directory
- `~`: Reference to your HOME directory

*Pause for questions.*

**WARNING: `rm` PERMANENTLY DELETES! You CANNOT recover anything when you use `rm`. I recommend to `mkdir OLD` to make a trash directory OLD and `mv` older/uneeded files/directories there. You can always delete them later.**
- `rm`: Delete
- `rm -r`: Delete recursively (used for deleting directories)
- `man`: Open the manual page for a command

*Pause for questions.*

## Redirection with `>` and `>>`

Commands executed show the result in our screen by default (also known as **standard output**). However, we can redirect that result to be displayed somewhere else. Some possible locations where we can redirect the output illustrated bellow (*Taken from DAS page 168*):

![](./stdoutput.png)

`>` and `>>` are used for redirecting the output to a specific file. For example:

`echo "Hello world" > hello.txt`

*Ask what command can be used to view file content. Pause for answers.*

What is the difference?

- `>`: Re-creates the file before writing the output.
- `>>`: Appends the output to the bottom of the file. If file doesn't exist, it will create it.

*Pause for questions.*

## More about `cat` command

[cat](https://www.man7.org/linux/man-pages/man1/cat.1.html) command allows you to concatenate files and print the concatenation in the standard output. You can `cat` at least one file.

`cat file1.txt file2.txt file3.txt` (and many more files)

*Pause for questions.*

## SCP for transferring files

The [scp](https://linux.die.net/man/1/scp) command will allow students to send or pull files from a remote machine, in our case, the [Linux Machines in the Swearingen Labs](https://cse.sc.edu/resources/workstations).

### Pulling files from a remote machine

Additionally to the already required for the `ssh`, we also need the following information for pulling a file:

- *Absolute path* of the file **in the remote machine** that we want to pull. Example: */acct/fvilchez/test.txt*
- *Absolute or Relative path* of the directory **in the local machine** where we want to store the file. Example: *.* (*dot* which refers to the *current directory*)

Since we are pulling a file, the `scp` command needs to be executed from a local terminal, i.e. a terminal without the `ssh` connection.

`scp -P 222 fvilchez@L-1D43-01.cse.sc.edu:/acct/fvilchez/test.txt .`

*Pause for questions.*

<!-- ### Sending a file to a remote machine

Same logic applies but we need to switch the order of the arguments. First we specify the location of the file in the local machine, and after it the location of the file in the remote machine. In the following example, the file *./test.txt* is sent to the home directory of the remote machine.

`scp -P 222 ./test.txt fvilchez@L-1D43-01.cse.sc.edu:~`

*Pause for questions.* -->


## Show Google Form

Complete form for attendance.

<!-- https://docs.google.com/forms/d/e/1FAIpQLSeW5WzcUTO6u-GEYsBwlhnme-6PUTmijWv85Ziu2ZhCVAJepg/viewform -->

## Commands executed during the lab

*Content may be different from the commands executed during the lab*.

### Review some commands

```
fvilchez@cocsce-l3d22-16 ~ $ echo "Hello World!"
Hello World!
fvilchez@cocsce-l3d22-16 ~ $ pwd
/acct/fvilchez
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp  Pictures   public_html  test_environment
Desktop    extractdata  Music     polls.csv  Templates    Videos
Documents  lab1.txt     osx       Public     test
fvilchez@cocsce-l3d22-16 ~ $ touch myfirstfile.txt
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp         osx        Public       test
Desktop    extractdata  Music            Pictures   public_html  test_environment
Documents  lab1.txt     myfirstfile.txt  polls.csv  Templates    Videos
fvilchez@cocsce-l3d22-16 ~ $ mkdir myfirstdirectory
fvilchez@cocsce-l3d22-16 ~ $ ls
215        extractdata  myfirstdirectory  polls.csv    test
Desktop    lab1.txt     myfirstfile.txt   Public       test_environment
Documents  Main.cpp     osx               public_html  Videos
Downloads  Music        Pictures          Templates
fvilchez@cocsce-l3d22-16 ~ $ mv myfirstfile.txt mysecondfile.txt
fvilchez@cocsce-l3d22-16 ~ $ ls
215        extractdata  myfirstdirectory  polls.csv    test
Desktop    lab1.txt     mysecondfile.txt  Public       test_environment
Documents  Main.cpp     osx               public_html  Videos
Downloads  Music        Pictures          Templates
fvilchez@cocsce-l3d22-16 ~ $ mv myfirstdirectory myseconddirectory
fvilchez@cocsce-l3d22-16 ~ $ ls
215        extractdata  myseconddirectory  polls.csv    test
Desktop    lab1.txt     mysecondfile.txt   Public       test_environment
Documents  Main.cpp     osx                public_html  Videos
Downloads  Music        Pictures           Templates
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $ pwd
/acct/fvilchez
fvilchez@cocsce-l3d22-16 ~ $ ls
215        extractdata  myseconddirectory  polls.csv    test
Desktop    lab1.txt     mysecondfile.txt   Public       test_environment
Documents  Main.cpp     osx                public_html  Videos
Downloads  Music        Pictures           Templates
fvilchez@cocsce-l3d22-16 ~ $ cd myseconddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ pwd
/acct/fvilchez/myseconddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ touch mynewfile.txt
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ ls
mynewfile.txt
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ ls -a
.  ..  mynewfile.txt
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ cd ..
fvilchez@cocsce-l3d22-16 ~ $ pwd
/acct/fvilchez
fvilchez@cocsce-l3d22-16 ~ $ cd myseconddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ cd ~
fvilchez@cocsce-l3d22-16 ~ $ pwd
/acct/fvilchez
fvilchez@cocsce-l3d22-16 ~ $ cd myseconddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ mkdir mythirddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory $ cd mythirddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory/mythirddirectory $ pwd
/acct/fvilchez/myseconddirectory/mythirddirectory
fvilchez@cocsce-l3d22-16 ~/myseconddirectory/mythirddirectory $ cd ~
fvilchez@cocsce-l3d22-16 ~ $ pwd
/acct/fvilchez
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $ ls
215        extractdata  myseconddirectory  polls.csv    test
Desktop    lab1.txt     mysecondfile.txt   Public       test_environment
Documents  Main.cpp     osx                public_html  Videos
Downloads  Music        Pictures           Templates
fvilchez@cocsce-l3d22-16 ~ $ rm mysecondfile.txt
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp           osx        Public       test
Desktop    extractdata  Music              Pictures   public_html  test_environment
Documents  lab1.txt     myseconddirectory  polls.csv  Templates    Videos
fvilchez@cocsce-l3d22-16 ~ $ rm myseconddirectory
rm: cannot remove 'myseconddirectory': Is a directory
fvilchez@cocsce-l3d22-16 ~ $ rm -r myseconddirectory
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp  Pictures   public_html  test_environment
Desktop    extractdata  Music     polls.csv  Templates    Videos
Documents  lab1.txt     osx       Public     test
fvilchez@cocsce-l3d22-16 ~ $ man rm
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $
```

### Redirection

```
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp  Pictures   public_html  test_environment
Desktop    extractdata  Music     polls.csv  Templates    Videos
Documents  lab1.txt     osx       Public     test
fvilchez@cocsce-l3d22-16 ~ $ echo "my first question"
my first question
fvilchez@cocsce-l3d22-16 ~ $ echo "my first question" > questions.txt
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp  Pictures   public_html    test
Desktop    extractdata  Music     polls.csv  questions.txt  test_environment
Documents  lab1.txt     osx       Public     Templates      Videos
fvilchez@cocsce-l3d22-16 ~ $ cat questions.txt
my first question
fvilchez@cocsce-l3d22-16 ~ $ echo "my second question"
my second question
fvilchez@cocsce-l3d22-16 ~ $ echo "my second question" >> questions.txt
fvilchez@cocsce-l3d22-16 ~ $ cat questions.txt
my first question
my second question
fvilchez@cocsce-l3d22-16 ~ $ echo "my third questions" > questions.txt
fvilchez@cocsce-l3d22-16 ~ $ cat questions.txt
my third questions
fvilchez@cocsce-l3d22-16 ~ $ ls
215        Downloads    Main.cpp  Pictures   public_html    test
Desktop    extractdata  Music     polls.csv  questions.txt  test_environment
Documents  lab1.txt     osx       Public     Templates      Videos
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $
```

### More on `cat`

```
fvilchez@cocsce-l3d22-16 ~ $ echo "first message" > first.txt
fvilchez@cocsce-l3d22-16 ~ $ echo "second message" > second.txt
fvilchez@cocsce-l3d22-16 ~ $ echo "third message" > third.txt
fvilchez@cocsce-l3d22-16 ~ $ cat first.txt
first message
fvilchez@cocsce-l3d22-16 ~ $ cat second.txt
second message
fvilchez@cocsce-l3d22-16 ~ $ cat third.txt
third message
fvilchez@cocsce-l3d22-16 ~ $ cat first.txt second.txt third.txt
first message
second message
third message
fvilchez@cocsce-l3d22-16 ~ $ cat first.txt second.txt third.txt > concatenation.txt
fvilchez@cocsce-l3d22-16 ~ $ cat concatenation.txt
first message
second message
third message
fvilchez@cocsce-l3d22-16 ~ $ ls
215                Downloads    Main.cpp  polls.csv      second.txt        third.txt
concatenation.txt  extractdata  Music     Public         Templates         Videos
Desktop            first.txt    osx       public_html    test
Documents          lab1.txt     Pictures  questions.txt  test_environment
fvilchez@cocsce-l3d22-16 ~ $
fvilchez@cocsce-l3d22-16 ~ $
```