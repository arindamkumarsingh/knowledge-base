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


#### digit counting and others


```c
#include<stdio.h>

int main(){

	int i, c, nwhite, nother;
	int ndigit[10];

	for(i = 0; i < 10; i++){
		ndigit[i] = 0;
	}

	while ((c = getchar()) != EOF){
		if ( c >= '0' && c <= '9'){
			++ndigit[c - '0'];
		}
		else if (c == ' ' || c == '\t' || c == '\n')
		{
			++nwhite;
		}
		else
		++nother;
	
	}
	printf("digits = ");
	for(i = 0; i < 10; ++i){
		printf("%d", ndigit[i]);
	}
	printf(", white space = %d, other = %d\n", nwhite, nother);
	
}
```

`++ndigit[c - '0']` = this is the main brain child, so whenever we put '' this symbol, it stores into the computer as ascii values, so this i called mapping function, which helps us to jump right into its memory location.

### Functions

**can encapsulate a function without worrying the implementation.**.

printf, getchar, putchar were inbuilt functions, we can make our own functions. 


```c

#include <stdio.h>

int power(int m, int n);   // function prototype

int main()
{
    int i;

    for (i = 0; i < 10; ++i)
        printf("%d %d %d\n", i, power(2,i), power(-3,i));

    return 0;
}

/* power: raise base to n-th power; n >= 0 */

int power(int base, int n)
{
    int i, p;

    p = 1;

    for (i = 1; i <= n; ++i)
        p = p * base;

    return p;
}
```

Functions exist for **abstraction**, you dont have to worry about how something works, if you know what it does.

Here the most important thing to note is *function prototype*, where in above we defined `int power(int m, int n)` this shows that somewhere in this program there exists a function of this kind and the compiler will take this as the reference of sort.

The parameters used or the variables inside a function is local to it and wouldnt come in way in other functions.

the advantage of using function prototype is to tell the compiler to check the input if its correct or not, as we have defined it to be `int` u cannot put double or string value in it and will give an error.

#### OLD C

here the power functions parameters will be mentioned first then the data type of them, so compiler can take in all kinds of crazy things than creating massive bugs.

```c

power(base, n);
int base, n;

```

Q. Temperature conversion program to use a function for conversion.

```c
#include <stdio.h>

int temperature(int fahr);

int main()
{
    int fahr;

    for (fahr = 0; fahr <= 200; fahr += 20)
    {
        printf("%d\t%d\n", fahr, temperature(fahr));
    }

    return 0;
}

int temperature(int fahr)
{
    return 5 * (fahr - 32) / 9;
}
```

practise.

## Arguments- call by value

unlike old langs like fortran and pascal, it copies the arguments into temporary variables.

eg.

```c

void change(int x){
        x = 100;
}

int main(){
        a = 10;

        change(a);

        printf("%d\n", a);
}
```

the output is still a = 10;

so when the value of a is assigned to `change` function, it is stored in temp variable and that is changed accordingly.

Designers of C wanted each functions to behave independently.

Another version of power function :-

```c

int power(int base, int n){
        int p;

        for (p = 1; n > 0; n--)
                p = p * base;
        
        return p;
        
}
```

 Here the for loop is directly changing the parameter n , as its a copy.

 Early version had to use another variable then manipulate that variable.

 If you actually want to change the caller variable, we can use **pointers**.

 But there is an exception which is array, they are not passed by their values, but rather than their address, so it can be modified directly.

 This led to many bugs lke, buffer overflow, memory corruption etc.

## Character array

