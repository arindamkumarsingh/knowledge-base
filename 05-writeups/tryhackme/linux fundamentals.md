# PART 1

Linux is one of the many OSs which can be intimidating at first but have their own adv and disadv. Linux is considered very lightweight and is used at many things we use today like Iots etc.

As linux is **Open Source**, many variants of this are available in the web. 

I use Ubuntu(Debian-based) OS. We can use ubuntu as a server.

<mark> Fun fact: Ubuntu can even run on systems with 512 mbs of ram.</mark>

### Using some basic commands

* `echo` = use this whenever want to print something in command line. use double quotes when printing a string, else if its a single word no need to.

* `whoami` = this can be used to know which user is currently accessing it.

* `ls` = listing, used to show all contents in a directory(many more flags can be used with this).

* `cd` = change directory, first writing `cd` then writing the name of the directory you want to go can be used, it is preferred to write the whole destination unless you want to access a directory of the directory u are currently in.

* `cat` = concatenate, can be used to see whats written in the file, with the use of angular bracket can be used to write into a blank while, append the file etc.

* `pwd` = print working directory, used to know the current directory u are present in.

<mark>It's considered efficient that without navigating to a directory we can use commands like cat, ls just by writing the full destination after the commands</mark>

Now there is a way where we cannot always use cd and ls, instead we can use `find` command.

* `find` = if u remember the name of the file:-

```bash
find -name passwords.txt
```

this will print out the location of the file.

now if we dont remember the name of the file, we can use wildcard(*) which means all file with a certain catchpoint, like `.txt`

```bash
find -name *.txt
```

* `grep` = another tool is this command, this allos to search some specific keyword which we want to search withing a file.

```bash
grep "ip_address" access.log
```

**Recursive searching with `grep`**

We may like to search the specific keyword accross all files present in that directory when we dont know in which file it can be.

```bash
grep -R "Some_name" /etc/
```

#### some shel operators

* `&` = This allows commands to run in background, for example if we copy a big file, it is obvious it will take a longer time so instead of wasting time we use  `&` operator so that we can use the terminal rather than waiting for it.

* `&&` = This allows two commands to run together, note that only both command will run only when command 1 is possible.



