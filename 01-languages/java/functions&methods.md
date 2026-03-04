# Functions

### syntax

```java
returnType functionName(type arg1, type arg2, ...){
    //operations

}
```

returnType means its a data type, and the functions return that type of data type.

void --> no return

public static = written in primary classes.

function name can be any except the keyword and keep the function name such that upon reading the name we can understand what these functions will do.

Eg

**print a name** 

```java
import java.util.*;

public class functions{

    public static void printMyName(String name){

        System.out.println(name);
        return;
    }

    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        String name = sc.next();

        printMyName(name);

    }
}

```

### what happens in memory

these functions are stored in stacks, stack frame where its given to the function

like main function is stored in a stack frame, uske contents uss me hi save hoga.

a new function also made above the main function stackframe, so when the work of that function over, that is removed from stack then after the main function is also removed from it.

```java
import java.util.*;

public class functions{

    public static void factorial(int n){
        if(n < 0){
            System.out.println("Invalid input");
            return;
        }
        int num = 1;
        for(int i = n; i >=1; i--){
            num = num*i;
        }
        System.out.println(num);
    }
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        
        int n = sc.nextInt();

        factorial(n);
        sc.close();
    }
}
```

methods are objects of classes.

# OOPs

