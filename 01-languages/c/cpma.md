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

Horner's Rule = factoring with products taking x common.

# Formatting Input/Output

Formatting string + values/variables

Format string has ordinary characters as well as conversion specifications(%) acts as a placeholder(empty space ) that gets filled by the values, so this specifes how the value will be converted from(binary) to int or float etc.

#### ERR

```c
printf("%d %d\n",
i);
```

this will print out first the original value then any random meaningless value.

C compilers doesn't check for no. of conversion specs so it will run without any errors.

```c
printf("%d\n",
i, j);
```

prints the value of i but doesn't show j.

Also compilers doesn't check  if its the appropriate type which is being printed.

### Conversion Specs

```c
%m.pX or %-m.pX
```

**minimum field width** , m, tells us how much minimum no. of characters to print. 

So if we have to print 123 and if we use %4d it will print *123.  * - space. If we want to print 12345 it will adjust accordingly if we add minus to it.

%-4d this will make it left justified so starts from left rather than right 123*.

**Precision**, p, depends on X, conversion specifier, 

* d - displays an integer in decimal, the p then acts as the minimum number to display. so %d == %.1d.

* e - displays floating point in exponential form, p shows how many digits to appear after decimal, default is 6, so if p == 0, then decimal point not displayed.

* f - Display floating in fixed decimal same work as e.

* g - shows in either exponential or fixed point, depends on number's size.


g specifier is helpful where size can't be predicted...


printf to formal nos.

```c
#include<stdio.h>

int main(void){
	int i;
	float x;

	i = 40;
	x = 839.21f

	printf("|%d|%5d|%-5d|%5.3d|\n", i, i, i, i);
	printf("|%10.3f|%10.3e|%-10g|\n", x, x, x);

	return 0;

}
```

this `|` will show the gap between each formatting.

```
|40|   40|40   |  040|
|   839.210| 8.392e+02|839.21    |

```

* **%5d** = here i has 2 chars so 3 spaces were added.

* **%-5d** = Displays i from left to right so 3 spaces on the right.

* **%5.3d** = so since i has 2 digit so it must have minimum 3 digits so extra zero added on right, so precisely 3 digits and minimum characters 5 so 2 spaces added on left.

* **%10.3f** = so it says 3 digits after decimal so it adds a zero on the right.

### Escape sequences

`\n` or others used this is called the above topic. 


This shows the compiler what to perform upon printing.

* Alert = `\a`
* backspace = `\b`
* New line = `\n`
* horizontal tab = `\t`

Now since we use ` " " ` this in the printf formatting string so if we want to use this, we use `\"` to include it in the printf statement.

```c
printf("\"Hello\"");
```

to print this char `\` u have to use this `\\` to print a single `\` .

other wise the compiler will think its an escape sequence.

## scanf function

this has usually the "tight packed" function rather than printf.

```c
int i, j;
float x, y;

scanf("%d%d%f%f", &i, &j, &x, &y);
```

Some traps are that programmer must enter the exact conversion specs as the input and `&` is usually required so remember to use it.

#### ERRR

If `&` is not put in the program, a program crash is emminent

### How scanf works

scanf starts at the format strings, start from the left, first see the conversion specs then the input data, if the input entered matches the type, then it continues on the rest of string. if item entered doesn't matches, it returns without looking at the rest of the string.

scanf ignores white-spaces(tab, space, newline etc), so we can input the number however we want.

Some rules followed by scanf to recognize integers and else.

eg. = 1-20.3-4.0e3\n

```c
scanf("%d%d%f%f", &i, &j, &x, &y);
```

first %d = reads 1, then after that integer cannot have `-` sign, so the characer is put back to be read again(starting point will now be `-`). 

then %d = scanf now reads -,2,0 and .(period). so integer cannot have a decimal, but reads -20 and stores in j.

%f = reads . , 3 and -. so minus cannot come after a digit so puts it back and stores 0.3 in the x.

%f = reads -,4,.,0,e,3 and \n. so it stores -4.0 X 10^3 in y and puts back new line character.

### Ordinary characters in format strings.

* white-spaces = scanf continuosly reads white-space consecutive till it reaches a non-white space. A white-space character in a format-string matches any number of white-space characters.

* Other chars = when it reads non-white space cahrs, if the input matches the format string it is discarded, and if not then it puts the char back into the input and aborts the process.

`"%d/%d"` = if input is `*5/*96`, skips the whitespace, reads 5 stores it, then reads `/` then matches it with the format string, then next skips the space, reads 96 and stores, but if the input was `*5*/*96` = stores 5, now next there must be `/` but it has a blank space, so it puts the space back in the input, and aborts or wait for next call, if we want to match the desired output use `"%d /%d"`.

#### some things to keep in mind

for `printf("%d %d\n", &i, &j);`

this will just print out odd looking nos. or the addresses.

in scanf one thing to keep in mind that in the format string, it must resemble the input.

```c
scanf("%d, %d", &i, &j);
```

so if it reads the integer, next it will try to match the comma, and if there is space then it can terminate the process.

So understand this, scanf treats every whitespace the same, ' ', '\t' etc so, if it hits a \n it will keep on consuming a newline or spaces, till a non-whitespace char appears.

This is designed specifically for people like us, who enter messy inputs, so that exact matching the newline character is kinda tough, so it discards or consumes the white-space all together.

Eg. adding fractions


```c

#include<stdio.h>

int main(void){
	int num1, denom1, num2, denom2, result_num, result_denom;

	printf("Enter first fraction: ");
	scanf("%d/%d", &num1, &denom1);

	printf("Enter second fraction: ");
	scanf("%d/%d", &num2, &denom2);

	result_num = num1 * denom2 + num2 * denom1;

	result_denom = denom1 * denom2;
	printf("The sum is %d/%d\n", result_num, result_denom);

	return 0;
}
```

##### is %i conversion same as %d

in printf there is no difference, but in scanf %d means it can match the integer written in base 10 decimal, while %i mathces octal, decimal or hexadecimal(base 16). If input number has prefix `0`, then treated as octal, if prefix has `0x` or `0X` then treated hexadecimal.

##### How to print `%` character.

if you enter two consecutive % %, then it prints the single character.

##### how far \t escape goes to?

you can't know, it depends upon the OS as to what happens when u print tab character, usually it is 8	chars	apart.