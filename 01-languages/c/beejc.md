Many C-versions exists, to apply the specific version you use c.

```bash
gcc -std=c11 -pedantic example.c
```

Variable is basically a humanreadable name for some data in the memory. Consider it an array of bytes, an index to this memeory is pointer. So instead of writting down the address of the data, we make a name for it instead. 

Whenever we have an uninitialised variable, it stores some indeterministic value, not 0 always.

Two arguments are passed on to printf() function. A string which describes what to print and how to print called format string. Second is the value to print, the variable is put in this argument.

```c
printf("%s i = %d and f = %f!\n", s, i, f);
```

the `%` sign shows that the variable which will correspond sequentially prints what values, i.e int, float, string etc.

q