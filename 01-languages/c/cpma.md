## Effective use of c

Avoid C pitfalls - after cpma, read Andrew Koenig's C Traps and Pitfalls. Modern compilers can detect some pitfalls and issue warnings but no compiler can spot them all.

## Compiling and linking

3 Steps:-

* **Preprocessing** = The program is given to a preprocessor and obeys the command given by `#` symbol, its like an editor which can add things.

* **Compiling** = now the modified program goes to the compiler and translated into machine code(object code). 

* **Linking** = combines the object code with additional code which yields an executable program.

#### GCC compiler

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
