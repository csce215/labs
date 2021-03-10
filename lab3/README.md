# Required Lab 3 Notes

## VIM
Basic functionality:  

Use ```vi <filename>``` or ```vim <filename>``` to open a file.

This will open your file that you passed in 'normal mode'.

Create a new file:
Use ```vi <newfilename>``` to open a new file. The file can exist or not exist.

Navigation:  
You can use the arrow keys and the pageup and page down keys to move your cursor around in the file.  

Inserting:  
To insert or modify press the 'i' key on your keyboard. You can then 'insert' or modify the file based on where your cursor is.

Saving your work:  
To save you work press the escape key 'esc' and then type ```:w``` amd press enter. This stands for write.  

To exit the file:  
Be sure you are in normal mode (use the esc key) and type ```:q``` to quit vim.

To save and quit at the same time:  
Use ```:wq``` to write and then quit.

## Bash Scripting
Bash scripting is like writing a program using the bash commands we have already learned in class. The only difference is the commands are in a single file and can all be run at once.

To create a bash script you can just open a newfile using vim ```vi <scriptname>.sh```. Typically, shell scripts end with the '.sh' extention to indicate that they are shell scripts.

From here you can just put commands in the file using vim and the save them.

Two ways to run: using ```bash <scriptname>.sh``` or ```./<scriptname.sh>```  

The difference between the two is that one can be run without execute permissions and the other must have execute permissions granted.

## File Permissions
To change permissions you use the ```chmod``` command with the permissions you want to grant and the filename.

For example: ```chmod +x hello.sh``` gives execute permissions to hello.sh shell script.

You can also use a 3 digit number with each digit being 0-7 (i.e. 777). 7 in binary is 111.
The permissions are in order of read(r), write(w), execute(x). You will notice there are 10 spots in the permissions area when you do ```ls -l```. The first one is a placeholder to identifiy if something is a directory or not using a 'd'. The remaining 9 are the different permission groups user, group, other. User only gives the user (you) certain permissions. Group gives a group of people permission (almost never used). Other gives anyone permissions(be careful with this)! So if you use ```chmod 777 hello.sh``` then it will give read, write, and execute permssions to everyone! ```chmod 700 hello.sh``` give only you read, write, and execute permissions (use this one).

## sed
The ```sed``` (stream editor) command involves searching and replacing.

```sed -i 's/<search_patter>/<replacement>/g' <filename>```

## tr
Translate or delete characters (from man page).
These accomplish the same thing (converting all uppercase to lowercase):  
- ```tr '[:upper:]' '[:lower:]'```
- ```tr '[A-Z]' '[a-z]'```


## diff
Shows the differences between to files.

```diff <file1> <file2>```

## More on Bash Scripting!
There is a lot more you can do with bash. You can write functions/methods, create for-loops and while-loops, and use if-statements just like Java or your favorite programming language.
