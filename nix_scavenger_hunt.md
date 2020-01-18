# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. 

Paste the output of the `pwd` command here:

```
/Users/drew/Desktop/projects/wats1030-intro-to-unix
```

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. 

What directories and files do you see when you run `ls`?

```
LICENSE                         challenge_files                 nix_scavenger_hunt_stretch.md
README.md                       nix_scavenger_hunt.md           super_scavengers.md
```

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. 

How are the results different when you use the `-alh` options?

```
-alh shows you all of the directories, including the directories that begin with "." It also lists out the details for each file with -l and makes the file size human readable with -h. 
```

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://man.he.net/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. 

Write down what those options do?

```
-a List all entires that begin with . (without this you'll see two less directories when writing the ls command)


-l This lists file info in "long format." 

 -h This makes the file sizes "human readable and converts them into kilobytes instead of bytes.

```


* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. 

What files and directories do you see listed?

```

Applications                    bin                             net
Library                         cores                           private
Network                         dev                             sbin
System                          etc                             tmp
Users                           home                            usr
Volumes                         installer.failurerequests       var
```

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. 

Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) Then run `pwd` and paste the output here:

```
/
```
* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. 

Use `cd` to move to `~`. Run `pwd` and paste the response here:

```
/Users/drew
```

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. How many files do you find?

```
3 files
```
 
Use the `cd` command to move "up" one directory. Where are you in the filesystem now?

```
/Users/drew/desktop/projects/wats1030-intro-to-unix
```

Press the up arrow on your keyboard. What just happened?

```
pwd appeared
```

Press the up arrow a few more times. What do you see?

```
 It shows all of my previous commands.
```
Run the `history` command. What do you see?

```
It lis```ts all of the commands that I ran.
```
### Observing the System

* Discover what account you are logged into using the `whoami` command. 

What username are you currently using?

```
drew
```
* Discover who else is on your system with the `who` command. 

Are any other users using your system? If so, list them here:

```
drew     console  Jan  1 14:49 
drew     ttys001  Jan 13 20:46 

Me twice? A little confused on this...
```
* How long has your system been running? 

Use `uptime` to see, and *paste the result here:

```
up 15 days
```

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) 

How do you interpret what you see here?

```
a = show processes for all users
u = display the process's user/owner
x = also show processes not attached to a terminal
```

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) 

How do you interpret what you see here?

```
It shows which programs are running and the statistical data for each and what it's using on my computer.
```

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. 

How many files did you find?

``
2
``
* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
```
Last updated: 01-15-2015
```
* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. 

Where is that file located?

```
./tmp/modi_laboriosam.txt
```
* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). 

How many files did you find?
```
2
```
* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. 

Paste the result showing the file and line where the word "Waldo" shows up.

```
./serial-numbers/eaque_molestiae.txt
```
### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. 

What do you see in the `files.txt` file?

```
All of the contents of the chanllenge_files folder.
```

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. 

Describe what you see when you run `ls -alh | more`.

```
It allows me to load content by hitting enter or using the arrow keys, so it doesn't appear all at once.
```
* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. 

Paste the list of processes that reference your username here:

```
drew             13253   3.8  1.6  5000368 132888   ??  S     6:11PM   2:46.80 /Applications/Google Chrome.app/Contents/Frameworks/Google Chrome Framework.framework/Versions/79.0.3945.117/Helpers/Google Chrome Helper (Renderer).app/Contents/MacOS/Google Chrome Helper (Renderer) --type=renderer --field-trial-handle=1718379636,14099911265682994555,6175297816075609402,131072 --lang=en-US --metrics-client-id=eb46d334-47e3-4f26-83c9-b817d749001c --enable-auto-reload --num-raster-threads=4 --enable-zero-copy --enable-gpu-memory-buffer-compositor-resources --enable-main-frame-before-activation --service-request-channel-token=13147143355932953280 --renderer-client-id=42 --no-v8-untrusted-code-mitigations --seatbelt-client=197
```