# Introduction

Whenever we start a new language we often start by writting the first hello world program.

```c
#include<stdio.h>

int main(){
    printf("Hello,World");
}

```

A C program usually has functions and variables. Functions consists of some statements which performs some task, we can name a function as we want but the **main** function is unique. main function will call other functions to perform the tasks.

The starting `#include<stdio.h>` is a standard input-output library. this library consists some in-built function which is called afterwards in the main function.'

`printf` is a library function which has some arguments "Hello, World". This argument is called **Character strings**. 


<mark>Fun fact: printf is actually not a part of c language.</mark>

Its just a function in the standard library, as this printf function can work in any other compiler if they follow the ANSI standard.
### Comments
Comments are a very useful part in any language, used for explaining the code block.

### Symbolic  constants

It's considered a bad practices to define variables in the main code with numbers. So by using `#define` and writing a replacement text and then assigning the number next to it.
So whenever we want to use that number we can just write the *replacement text* instead.


### Widths of characters

`%d` is used to show that the number printed is integer decimal, similiarly `%f` is used to  show that the number printed is float.

then we can add some modification for it to skip those spaces like:

`%6d` = shows that the number printed is integer and must leave 6 characters blank

`%6.1f` = shows that number printed is float and must leave 6 characters blank and only one digit is to be printed after the decimal point.

### Some examples


#### File copying 

In C file copying is done through `getchar()` and `putchar()`. A basic program is taking input of character and printing it one at a time.

```c
#include<stdio.h>
int main(){

        int c;

        c = getchar();
        while (c != EOF){
                putchar(c);
                c = getchar();
}
}
```
here `char` is used but we can input numbers also as its a character too.

<mark>Funfact : c = getchar() != EOF and c = (getchar() != EOF)</mark>

because `!=` gets higher preference than assignment operator.


#### Character counting

```c
#include<stdio.h>
int main(){

        double nc;

        for(nc = 0; getchar() != EOF; nc++)
                ;
                printf("%.0f\n", nc);

}
```

here we have taken `double` nc(number count) so huge number of inputs can be done, the expression `getchar` will take value till EOF( CTRL + D) in linux OS and nc++ increments the count.

<mark>Extra : this is like the ` wc -c` command of bash.</mark>

#### Line counting

Logic for this is quite simple, since new line in c is added by `\n`, we put a loop with a condition <mark>c == '\n'</mark>








#### Word counting

```c
#include<stdio.h>

#define IN 1
#define OUT 0

{
        int c, nl, nw, nc, state;

        state = OUT;
        nl = nw = nc = 0;
        while ((c = getchar()) != EOF){
                ++nc;
                if (c == '\n')
                ++nl;
        if (c == ' ' || c == '\n' || c == '\t')
        state = OUT;

        else if (state == OUT){
                state = IN;
                ++nw;
        }
        }
        printf("%d %d %d\n", nl, nw, nc);

}
```

This is the bare minimum of the command `wc` in linux based systems.

if we come at the end of the code, else if(state == OUT) , this says if you start at the word for example `hello` the first letter starting at h , the state will be OUT which means a new word has started here, so `++nw`.

<mark> As seen in the code, we have taken the cases of blank, tab, and new line character, so if still the state is out that means that we are at the first letter of the word.</mark>

