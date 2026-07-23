Using make to build c files.

```bash
make filename
```

then execute.

Break program by removing parts on random and output be pasted here.


got this after removing the `%d` for this.

```
ex1.c:7:12: warning: too many arguments for format [-Wformat-extra-args]
    7 |     printf("You are  miles away.\n", distance);

```

After removing the distance variable but putting the format variable.

```
ex1.c:7:22: warning: format ‘%d’ expects a matching ‘int’ argument [-Wformat=]
    7 |     printf("You are %d miles away.\n");
      |                     ~^
      |                      |
      |                      int
```

after removing the comma i get.

```
ex1.c:7:38: error: expected ‘)’ before ‘distance’
    7 |     printf("You are %d miles away.\n" distance);
      |           ~                          ^~~~~~~~~
      |                                      )
ex1.c:7:22: warning: format ‘%d’ expects a matching ‘int’ argument [-Wformat=]
    7 |     printf("You are %d miles away.\n" distance);
      |                     ~^
      |                      |
      |                      int
make: *** [<builtin>: ex1] Error 1
```

i changed int into char, but still we got 100 printed but we had '%d' there isnt it for integer values, how????

There is something called integer promotion. Distance is of type char, so if passed to printf, its automatically promoted to int.

printf is variadic function(can take no. of arguments.) 

```c
int printf(const char *format, ...)
```

`...` means compiler doesnt know the remaining argument. So all the remaining data type like:-

* char - int

* signed char - int

* short - int

* float - double.


AN example of why using %c can give diff results

```c
char c = 65;

printf("%c\n", c);
```

This prints out A, rather than 65, because %c prints out the character which has the value corresponding to it.

## Using Make

We rely on internal knowledge of program to build most common software.

```bash
make ex1

# or this

CFLAGS="-Wall" make ex1
```

The make program then looks

1. Does ex1 exists already.

2. If not then if another file that starts with ex1.

3. yes, ex1.c, then its checks if it knows how to build .c files.

4. so it knows the command `cc ex1.c -o ex1`

5. than it makes ex1 by using cc.

The CFLAGS command gvies a command line option `-Wall` meaning it reports all possible warnings.

How do u make a Makefile.

just create a file name `Makefile` in the same directory as ur program and write down some automation

```
CFLAGS=-Wall    -g
clean:
    rm  -f  ex1
```

use only TAB and not tab and spaces, the program assumes makefile and executres it.

so we can run
`make clean` to clean out any existing ex1 file.
then run `make ex1`

#### TO break this

remove the identation after clean in the makefile and see that u are using tab.

Q. To create an `all: ex1` which will make the default `all:` to be on ex1 files. And then we clarify ex1 as ex1.c then do cc compile.

<mark>U can add clean in it, so add clean and do make clean before directly putting `make`</mark>

do `man make` and `man cc`.

## Formating printing



