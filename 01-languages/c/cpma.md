## Effective use of c

Avoid C pitfalls - after cpma, read Andrew Koenig's C Traps and Pitfalls. Modern compilers can detect some pitfalls and issue warnings but no compiler can spot them all.

## Compiling and linking

3 Steps:-

* **Preprocessing** = The program is given to a preprocessor and obeys the command given by `#` symbol, its like an editor which can add things.

* **Compiling** = now the modified program goes to the compiler and translated into machine code(object code). 

* **Linking** = combines the object code with additional code which yields an executable program.

#### GCC compiler

GCC = GNU C compilier originally, but now stands for GNU compiler collection because it also compiles programs of C, C++, Fortran, JAVA etc.

GNU = GNU's Not UNIX ( guh - NEW), GNU is a project by Free Software Foundation, a protest against licensed UNIX software, in FSF, the users must be free to run, copy distribute modify improve the software. This project has rewritten this licensed software from scratch and made it publically available at no charge.

GCC runs under many OSs, and is responsible for generating code for many CPUs. It is used extensively for commercial software development.

Some specific commands to spot errors while compiling.

1. `-Wall` = all -W options, generates warning messages when detects error.

2. `-pedantic` = issues all the warnings by C standard and causes it to reject programs which use non standard features.

3. `-ansi` = enables few features which are disables.

4. `-std=c99 = specifies the version of c for compiler to use.

When a comment is added does it replace or put black spaces in it or what,

```c
a/**/b = 0;
```
will be interpreted as a b = 0;

which becomes an illegal statement fo rmodern standards of C.





#### General form of c

Three key features- directives, functions and statements.

##### Directives

Commands intended for the preprocessor is called directives, such as #include directive.

which means `stdio.h` has to be includes before the program starts compiling, many such headers files exists, we include this because c has no inbuilt read and write functions. Java has it.

##### Functions

two parts - library functions and program functions. Series of statement grouped together and given a name. 
```c
♦include <stdio.h>
int main(void)
{
printf("To C, or not to C: that is the question.\n");
return 0;
}
```
int just before main includes that it has integer value, void in parenthesis means main has no arguments.

For return 0; causes program to terminate and return a value 0, if u dont include this return statement, some compilers will stiill allow it to be terminated while others may not so, as it wouldn't have returned an integer value.

##### Statement

as in the above code, it calls the function `printf`.


##### COmments

/* ---- */ or //

### Volume division

By default, c round downs on divising, `/` so if we want to force the integer division to round up we use the form

x/d = (x + d - 1)/d

Either u can use  variables or put expressions in the `printf` functions.

The printf and scanf has f which stands for formatting, which implies that it requires the use of format string.

```c
scanf("%d", &i);
```

reads as an integer and stores it in i.

```c
#include <stdio.h>

int main(void){
	int height, length, width, volume, weight;

	printf("Enter the height of box: ");
	scanf("%d", &height);

	printf("Enter the length of box: ");
	scanf("%d", &length);

	printf("Enter the width of box: ");
	scanf("%d", &width);



	volume = length * width * height;
	weight = (volume + 165)/166;

	printf("Weight of the box is = %d\n", weight);
	
	return 0;
}
```

#### Defining names to constants

In the above program we have the constant 166 we can provide it a name, process called macro definition.

```c
#define inches_per_pound 166
```

and replacing 166 with the new name given to it.

```c
#include <stdio.h>
#define inches_per_pound 166

int main(void){
	int height, length, width, volume, weight;

	printf("Enter the height of box: ");
	scanf("%d", &height);

	printf("Enter the length of box: ");
	scanf("%d", &length);

	printf("Enter the width of box: ");
	scanf("%d", &width);



	volume = length * width * height;
	weight = (volume + inches_per_pound - 1)/inches_per_pound;

	printf("Weight of the box is = %d\n", weight);
	
	return 0;
}
```

if the definition consists of operations like reciprocal of pi or etc, it should be enclosed within the brackets.

here any name can be given, but mostly all letters must be upper-case, just a convention.

## Layout of a C prog

think of the c program as tokens, group of characters than can't split up without changing their meaning, identifiers and keywords are token, or the operators + , - etc...

```c
printf("Height: %d\n", height);
```
This has 7 tokens.

printf, { , "Height: %d\n", `,` , height, } , ; .

1 and 5 are identifiers, 3 is a string literal, (2,4,6,7) are punctuation.

All the tokens can be lined up together and crammed with almost no space, but it can cause two tokens to merge into third one.

It can also be merged into a single program, but each preprocessing directives require a different new line.

Enough space must be used to make it more readable and understandable.

#### Some FAQs

1. Why floating point constants need to end with letter f?

because if we don't it will go and by default save in the double data type, these get stored more accurately, and can store larger value.


Some errors by me

```c

#include<stdio.h>
int main(void){
        float original, taxed;

        printf("Enter the original amount dollars and cent = ");
        scanf("%.2f", &original);

        taxed = original + (original * (5.0f/100.0f));

        printf("Total amount after taxed = %.2f", taxed);

        return 0;

}
```

In the scanf part, i may want only till 2 decimal point, but we say that the variable is the floatin gpoint and wont be decided now but in the printing format.

so we will replace `%.2f` with `%f`.

2. Whenever we write `%2f` this would mean that it takes first 2 digits of the number inputted, so in the above program if the condtion was written, if we write 10, 100, 1000, the amount taxed would be the same.

Q. 3x^5 + 2x^4 - 5x^3 - x^2 + 7x - 6

