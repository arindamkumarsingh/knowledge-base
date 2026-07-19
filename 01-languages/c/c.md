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
destination pointer is the first pointer.

# Structs

`struct` is a user defined type that can hold multiple pieces of data. kinda bundles them together, just like the concept of classes and objects.

## TO declare a struct

```c
struct car{
    char* name;
    float price;
    int speed;
}
```
done in global scope(outside any function)

so we are  making a new type here, which is `struct car` 

by the use of dot we access the multiple fields.

```c
struct car saturn;

saturn.name = "BLAH::K"
saturn.price = 15999.99
saturn.speed = 175;
```

## Struct intializers

a better way to intialize is writting in together

```c
struct car {
    char *name;
    float price;
    int speed;
};

// Now with an initializer! Same field order as in the struct declaration:
struct car saturn = {"Saturn SL/2", 16000.99, 175};
```

this cannot happen to variable which is defined.

to make this code safer, we see that the initializer has to be in order, to be more precise.

`struct car saturn = {.speed=175, .name ="Saturn"};`

## Passing structs as a function

1. pass a struct
2. pass the pointer to struct

2 cases where we want the pointer of struct to pass in function

1. the function has to make changes in the original function

2. struct  is large or expensive to copy that into it, so just copy the pointer.

```c
//-snip-

struct car saturn

set_price(&saturn, 700.1);
```

so here we need to make a function which changes the price of thecar.

```c
void set_price(struct car *c, float new_price){
    c.price = new_price;
}
```
this gives error because `.` works for structs only, not for pointers.

so what about we dereference the pointer to access the struct.

```c
void set_price(struct car *c, float new_price){
    (*c).price = new_price;
}
```

workable, looks ugly tho.

**ARROW OPERATOR**

This is useful for when u have a pointer to it.

```c
c->price = new_price;
```

TO compare struct, u have to compare each fields of the structs.

# FILE I/O

**FILE* DATA TYPE** 

Streams of data or file from any source.

`stdin` = standard input by keyboard default

`stdout` = standard output, generally by screen by default

`stderr` = standard error by screen default

these above we have been using these implicitly.

```c
printf("HELLO");
fprintf(stdout, "HELLO");
```

Typical OS allows to redirect output or errors either to terminal screen or to files.

So in a POSIX shell, and run the program in such way that print the non-error into one file

## Reading text files

Streams are characterized in 2 ways :- text and binary

```c
#include <stdio.h>

int main(void)
{
    FILE *fp;                      // Variable to represent open file

    fp = fopen("hello.txt", "r");  // Open file for reading

    int c = fgetc(fp);             // Read a single character
    printf("%c\n", c);             // Print char to stdout

    fclose(fp);                    // Close the file when done
}
```

`r` was passed as string as many strings are passed like different options which means open a text stream for reading.

we use fgetc() function to get a character from the stream, but why did we write c as int than char.

FILE* keeps track of position in file, so subsequent cals will get next character.

## END OF FILE

EOF is a macro. Its not a character but a special integer(-1) which signals, u tired to read but no more data.

#### HOW fgetc() works

```c
int c;

while ((c = fgetc(fp)) != EOF)
    putchar(c);
```

EOF is return only after reading past the last character.

now if char could store every possible byte there would be not extra space for EOF. int can represent far movre values than char.

```c
#include<stdio.h>

int main(void){
    FILE *fp;
    int c;

    fp = fopen("hello.txt","r");

    while((c = fgetc(fp)) != EOF)
        printf("%c", c);

    fclose(fp);

}
```

### Reading a line at a time

A Code for reading a file

```c
#include <stdio.h>

int main(void)
{
    FILE *fp;
    char s[1024];  // Big enough for any line this program will encounter
    int linecount = 0;

    fp = fopen("quote.txt", "r");

    while (fgets(s, sizeof s, fp) != NULL) 
        printf("%d: %s", ++linecount, s);

    fclose(fp);
}
```

## Formatted input

```c
#include<stdio.h>

int main(void)
{
    FILE *fp;
    char name[1024];
    float length;
    int mass;

    fp = fopen("quote.txt","r");

        while(fscanf(fp, "%s %f %d", name, &length, &mass) != EOF)
            printf("%s whale, %d tonnes, %.1f meters\n", name, mass, length);

        fclose(fp);
}
```

here no `&` at name because array and pointer significance.

# typedef

We can use this to make an alias for an existing type


```c
typedef int blah;

blah x = 10;
```

we can make a number of types for the same type

```c
typedef int blah, blahblah, blahblahblah
```

## Application

### typedef and struct

we can use typedef to shorten the whole thing which we have to write

```c
struct animal {
    char *name;
    int leg_count, speed;
};

//  original name      new name
//            |         |
//            v         v
//      |-----------| |----|
typedef struct animal animal;

struct animal y;  // This works
animal z;         // This also works because "animal" is an alias
```

A more common way of doing this is

```c

typedef struct animal{
    char *name;
    int leg_count, speed;
} animal;

animal z;
```

Another shortcut is *anonymous structures* which is not naming the struct but only alias

```c
//  Anonymous struct! It has no name!
//         |
//         v
//      |----|
typedef struct {
    char *name;
    int leg_count, speed;
} animal;                         // <-- new name

//struct animal y;  // ERROR: this no longer works--no such struct!
animal z;           // This works because "animal" is an alias
```

```c
typedef struct {
    int x, y;
} point;

point p = {.x=20, .y=40};

printf("%d, %d\n", p.x, p.y);  // 20, 40
```

at point p we have done .x and .y this is done so that order can be removed and specification to be done.

### typedef and her types

Lets take an example that if we have int in my code over so many places, it will be painful if we have to convert them all to double, so here `typedef` comes   to  save    us.

```c
typedef float app_float;

app_float f1,f2,f3;
```

```c
typedef long double app_float;

app_float f1, f2, f3;
```

### typedef and pointers

```c
typedef int *intptr;

int a = 10;
intptr x = &a;
```

not good in practice.


# Pointers-II

we can do math, addition or subtraction to pointers.

SO if we add one to a pointer, it moves to the the next item of that type directly.

```c
int a[5] = {1, 2, 3, 4, 5};
int *p = &a[0];
```

```c
#include<stdio.h>

int main(void)
{
    int a[5] = {1, 2, 3, 4, 5};

    int *p = &a[0];

    for(int i = 0; i < 5; i++){
        printf("%d\n", *(p + i));
    }
}
```

works the same for array notation.

if we add 1 to pointer of int, then it jumps ahead of sizeof(int).

## changing pointers

we can do that while knowing the value and doing while loop and incrementing pointers till it reaches that certain value.

```c
while(*p != 999){
    printf("%d", *p);
    p++;
}
```

## Subtracting pointers

Can subtract two pointers to find the difference between them, and calculate how many ints there are between two `int*` and happens within the single array.

```c
#include <stdio.h>

int my_strlen(char *s)
{
    // Start scanning from the beginning of the string
    char *p = s;

    // Scan until we find the NUL character
    while (*p != '\0')
        p++;

    // Return the difference in pointers
    return p - s;
}

int main(void)
{
    printf("%d\n", my_strlen("Hello, world!"));  // Prints "13"
}
```

Above code is how strlen works.

## Array/Pointer Equivalence

Formula

`a[b] == *(a+b)`

a and b can be expressions.

we cant move an array variable gives error but can move pointers.

If we have a functino whcih takes a pointer argument we can either pass an array or a pointer to function and it can work

```c
char s[] = "antelopes";
char *t = "wombates";
```
jsut pass s or t in the function

## Void pointers

a `void*` enables us to write code type-agnostic which gives us some flexibility.

Some function are :-

1. `memcpy()` copies bytes of memory from one pointer to another, but those pointers can point to any type, so memcpy takes advantage of this fact
and ensures bytes are iterated over other.

built-in memcpy function

```c
void *memcpy(void *s1, void *s2, size_t n)

```
this function copies from s2 to memory starting of s1 but both are voids.

So we can copy a string with memcpy

```c
#include<stdio.h>
#include<string.h>

int main(void){
    char s[] = "Goat";
    char t[100];

    memcpy(t, s, 7);

    printf("%s\n", t);
}
```

```c
#include<stdio.h>
#include<string.h>

int main(void){
    int a[] = {11, 22, 33};
    int b[3];

    memcpy(b, a, 3 * sizeof(int));

    printf("%d\n", b[1]);
}
```

if its a float, or strucct or else u should have a pointer to it, and above is array so there was 
    no need for a pointer or anything.

in the string example there was no need to do size of char because its 1 only so we would have been doig 7 * 1.

so if we didnt had `void*` with us then we would have had to define seperate functions for each data type

```c
memcpy_int(int *a, int *b, int count);
memcpy_float(float *a, float *b, int count);
memcpy_double(double *a, double *b, int count);
memcpy_char(char *a, char *b, int count);
memcpy_unsigned_char(unsigned char *a, unsigned char *b, int count);

```

Here are some limitations of void*

1. we cannot do pointer arthmetic on void*
2. cannot dereference a void*
3. cannot use arrow operator on void* as it means dereference.
4. cannot use array notation on void* also means dereference.

We can do dereferencing by assigning another variable of desired type and then assigning the void* to it.

```c
char a = 'x';

void* p = &a;
char* q = p;

printf("%c", *p);
```

with this we can write our own memcpy

```c
void *my_memcpy(void *dest, void *src, int byte_count){

    char *s = src, *d = dest;

    while(byte_count--){
        *d++ = *s++;
    }

    return  dest;
}
```

in the while statement, we see that *d = *s, so from source bytes gets transfered to dest, but alse
after assignment, it gets post incremented so that it moves on to the next available memory.

<mark>review the qsort and compar functions afterwards.</mark>

# Manual Memory Allocation

We can tell c as to how much block of memory we need to keep to ourself and the most important is to tell
it when we want to free it, if we dont then a **memory leak** can occur and the process will continue to reserve the memory 
untill it exits.

Its as simple(:-

*If u manually allocated it, u have to manually free it when u are done with it*.

The automatic local variables(ones who gets out of scope when outside a function) are allocated "on the stack" while
manually allocated one stay on the heap.

Some new functions which can be found with `stdlib.h` library.

## Allocating and deallocating

`malloc()` function accepts no. of bytes to allocate and returns void pointer to that block and that void pointer can then be assigned
to any pointer we want, so how do we allocate the amt of bytes...

We use the `sizeof()` function , if we want room for a single int, we do `sizeof(int)`.

after using we can call free() to call and be used for something else.

```c
int *p = malloc(sizeof(int));

*p = 12;

printf("%d\n", *p);

free(p);
```

This is useful for complex tab.

## Error checking

The allocation functions like malloc() returns a pointer to the newly allocated stretch of memory or NULL.
Buut some OSes like linux can be made in such way that it never returns null even out of memory.

error handling:-

```c
int *x;

x = malloc(sizeof(int) * 10);

if(x == NULL){
    printf("error allocating 10");
}
```

OR

```c
int *x;

if ((x = malloc(sizeof(int) * 10)) == NULL) {
    printf("Error allocating 10 ints\n");
    // do something here to handle it
}
```

assingment and condition on same line


