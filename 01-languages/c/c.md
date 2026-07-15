TO know about which library includes which function, go to bash do `man 3 function_name`, ull get details.

But another way to think about it is that a variable is a human-readable name that refers to some data in memory.

char * - strings

uninitialized variables have indeterminate values not always zero.

format string and value to print.

### ternary op

```c
y += x > 10? 17: 37
```
is

```c
if(x>10)
    y += 17;
else
    y += 37;

```

---

**switch** statement is useful for equality cases, whlie if-else can be used for various cases like comparision, ranges etc.

# Functions

### passing by value

```c
#include <stdio.h>

void increment(int a)
{
    a++;
}

int main(void)
{
    int i = 10;

    increment(i);

    printf("i == %d\n", i);  // What does this print?
}
```

as in the increment function above it just increases the value for that part of function only because it only copies the argument from main to its function and converts that copied value only, not the value from main.

To get data back we have to pass by reference, but data is still getting passed(copied).

# pointers

Said to be the only part challenging about this language.
a variable that holds the address number

```c
#include<stdio.h>

int main(void){

    int i = 10;

    printf("value of i is -> %d\n", i);
    printf("and address is = %p\n", (void *)&i);
}
```

the hexadecimal value is is trillions, but computer has much less ram, then? The concept of virtual memory, lets computer processes think

```c
int *p;
```
p's type is "pointer to an int" or int-pointer.

so it holds address of other int.

so ont he right hand side of this has to be an address and convienient way is

```c
int i;
int* p;

p = &i;

## Dereferencing

accessing the variable directly through its address via pointer. we use the same `*` sign to the pointer to access variable, like opposite type shi

```c
#include <stdio.h>

int main(void)
{
    int i;
    int *p;  // this is NOT a dereference--this is a type "int*"

    p = &i;  // p now points to i, p holds address of i

    i = 10;  // i is now 10
    *p = 20; // the thing p points to (namely i!) is now 20!!

    printf("i is %d\n", i);   // prints "20"
    printf("i is %d\n", *p);  // "20"! dereference-p is the same as i!
}
```

## passing pointers as arrgument

the main use of pointer comes when passing them in function.

NOw its always true that when parameter of function is a variable or even a pointer, it always gets copied so its like saying we have copy of the same address in the function and if we do any changes from the pointer we see that its also changes the original one.

SO if we want function to actually modify the original one we use pointer.

## Null pointer

```c
int* p;
p = NULL;
```
if we try to add a value to this it will point to nothing so deferencing it causes it to crash

# Arrays

Out Of bounds case

```c
#include <stdio.h>

int main(void)
{
    int i;
    int a[5] = {22, 37, 3490, 18, 95};

    for (i = 0; i < 10; i++) {  // BAD NEWS: printing too many elements!
        printf("%d\n", a[i]);
    }
}
```
 IT will print out garbage values and not say array out of bounds.

## Multidimensional

```c
#include <stdio.h>

int main(void)
{
    int row, col;

    int a[2][5] = {      // Initialize a 2D array
        {0, 1, 2, 3, 4},
        {5, 6, 7, 8, 9}
    };

    for (row = 0; row < 2; row++) {
        for (col = 0; col < 5; col++) {
            printf("(%d,%d) = %d\n", row, col, a[row][col]);
        }
    }
}
```

```c
#include <stdio.h>

int main(void)
{
    int row, col;

    int a[2][5] = {      // Initialize a 2D array
        {0, 1, 2, 3, 4},
        {5, 6, 7, 8, 9}
    };

    for (row = 0; row < 2; row++) {
        for (col = 0; col < 5; col++) {
            printf("(%d,%d) = %d\n", row, col, a[row][col]);
        }
    }
}
```

# Arrays and pointers

A pointer to the array means they are talking about a pointer to first element of array.

```c
#include<stdio.h>

int main(void)
{
    int a[5] = {11, 22, 33, 44, 55};
    int *p;
    
    p = &a[0];
    printf("%d\n", *p);
}
```

we can also do p = a. directly rather than doing &a[0], all the time.

## Passing single dimensional arrays to functions
```c
#include <stdio.h>

// Passing as a pointer to the first element
void times2(int *a, int len)
{
    for (int i = 0; i < len; i++)
        printf("%d\n", a[i] * 2);
}

// Same thing, but using array notation
void times3(int a[], int len)
{
    for (int i = 0; i < len; i++)
        printf("%d\n", a[i] * 3);
}

// Same thing, but using array notation with size
void times4(int a[5], int len)
{
    for (int i = 0; i < len; i++)
        printf("%d\n", a[i] * 4);
}

int main(void)
{
    int x[5] = {11, 22, 33, 44, 55};

    times2(x, 5);
    times3(x, 5);
    times4(x, 5);
}
```
ALl three methods are identical to use but first is the most common used on daily basis.

As array is like pointers in disguise, it can be passed to another function and all the changes done in the function will be reflected  in main.

```c
#include <stdio.h>

void double_array(int *a, int len)
{
    // Multiply each element by 2
    //
    // This doubles the values in x in main() since x and a both point
    // to the same array in memory!

    for (int i = 0; i < len; i++)
        a[i] *= 2; //imp
}

int main(void)
{
    int x[5] = {1, 2, 3, 4, 5};

    double_array(x, 5);

    for (int i = 0; i < 5; i++)
        printf("%d\n", x[i]);  // 2, 4, 6, 8, 10!
}
```
# Strings

Strings are also like pointers, as strings also barely exist in c.

### String variables as pointers

```c
char *s = "hello world";
```

pointer to a char. print using %s.

### string variables as arrays

```c
char s[] = "hello world";
```

```c


#include <stdio.h>

int main(void)
{
    char s[] = "Hello, world!";

    for (int i = 0; i < 13; i++)
        printf("%c", s[i]);
    printf("\n");
}
```

or instead we can change the definition of s to char* type.

```c
#include<stdio.h>

int main(void){
    char* s = "Hello, World!";

    for(int i=0;i <13; i++)
        printf("%c", s[i]);
    printf("\n");
}
```

we use format specifier `%c` to print a single character.

it shows deep down that array and pointers are same thing.

#### THE difference in initializers

```c
char *s = "Hello, world!";
char t[] = "Hello, again!";
```

a subtle difference is the 1st one the string is tossed into a huge chunk of memory and we are given the pointer to it, so its far away from my programs memory so if we try to mutate(change) the string it will give error or crash, but thats not the case with array.

Their memory address is right there with us, continuous so we can change it at our own will.

### TO find string length

import a lib called `string.h` and through strlen(s).

the value returned is type size_t, so its int type, but C doesnt track the length of the string anywhere.

### String termination

when we make a new lang 2 things to keep in mind while storing string:-

1. storing the bytes along with a number indicating length of string.

2. store bytes of string, and mark end of string with special byte- terminator.

If we want to store a string longer than 255 characters, option 1 requires atleast 2 bytes, where option 2 requires one byte to terminate string, these savings were useful earlier times than now.

THe real advantage of this is no need to track strings, just point a pointer and teh function like strlen will scan until it hits `\0`.

So a string like `hello` is stores as `h`, `e` , `l`, `l`, `o`, `\0`.

The downside is O(n) calculation worst case for etire string. And easy to break ->

```c
char arr[5] = "hello"; // ❌ no space for '\0'
```

"hello" in c `\0` is implicitly included.

Our own strlen

```c

int my_strlen(char* s){
    int count = 0;

    while(s[count] != '\0')
        count++;

    return count;
}
```

### Copying a string

one way is we make a copy of pointer, but we end up doing changes to the same string

```c
#include <stdio.h>

int main(void)
{
    char s[] = "Hello, world!";
    char *t;

    // This makes a copy of the pointer, not a copy of the string!
    t = s;

    // We modify t
    t[0] = 'z';

    // But printing s shows the modification!
    // Because t and s point to the same string!

    printf("%s\n", s);  // "zello, world!"
}
```

What we want is a function called, which copies the whole string into another empty array.

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    char s[] = "Hello, world!";
    char t[100];  // Each char is one byte, so plenty of room

    // This makes a copy of the string!
    strcpy(t, s);

    // We modify t
    t[0] = 'z';

    // And s remains unaffected because it's a different string
    printf("%s\n", s);  // "Hello, world!"

    // But t has been changed
    printf("%s\n", t);  // "zello, world!"
}
```
destinatin pointer is the first pointer.