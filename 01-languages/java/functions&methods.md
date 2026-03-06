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


```java
class Pen{
    String color;
    String type;

    public void write(){
        System.out.println("writing ")
    }
}
```

now in the main public class 
uspe main function likhenge.

now in the main function we create the object.

```java
public class OOPS{
    public static void main(String args[]){
        Pen pen1 = new Pen();

        pen1.color = "blue";
        pen1.type = "gel";

        pen1.write();
    }
}
```

type of object will be the class ka name before pen1, baaki jitne bhi properties likhe h, uspe dot lagake do this.

`pen1.write();` = this prints out the function write and prints writing something.

to print out the color and type we have to ake another function.

now when we create another object pen2 and fill details like color and type. we owuld make functions in the Pen class, to print colors.

```java
public void write printColor(){
    System.out.println(this.color);
}
```

here `this` keyword plays a major role, specifying the object in role. 

convention se class should have capital.

```java
class Student{
    String name;
    int age;

    public void printInfo(){
        System.out.println(this.name);
        System.out.println(this.age);
    }
}
```
now we can make objects accordingly in the main function.
`Student s1 = new Student()`= new creats a new memory in the heap and stores. Student() is a constructor which is responsible for creating objects.

#### some rules

constructor and class name must be same.

constructor doesnt return anything and na koi data type.

constructor is called only once when an object is created.

#### Non parametrised constructor

now in above we have not made any Student() constructor above, but still our code was able to execute, that is because java can by default create the constructor if we have not made exclusively.

```java
Student() {
    System.out.println("constructor called");
}
```

now we have made our exclusive constructor inside the Student class code block, now whenever that constructor will be called, the code inside the constructor will be executed accordingly. 

#### parametrised constructor

```java
Student(String name, int age){
    this.name = name; 
    this.age = age;
}
```

here `this.name` and `this.age` is of object, and name and age is the parameter name.

```java
Student s1 = new Student("aman", 24);
s1.printInfo();
```

parametrised constructor me parameters paaas krdiye and boom.

#### copy constructor

copy contents from one object to another object.

```java
Student(Student s2){
    this.name = s2.name;
    this.name = s2.age;
}

Student(){

}

public class OOPS{

    public static void main(String args[]){
        
        Student s2 = new Student();
        s1.name = "aman";
        s1.age = 24;

        Student s2 = new Student(s1);
        s2.printInfo
    }
}
```

so without putting nfo of s2 , we got the same info.

So we have defined the copy constructor, so before that the above constructor must also be defined. 

### Destructors also exists

but we dont have to write destructors as garabage collectors exists, so automatically collects the objects and disposes of them.

# Polymorphism

### Function overloading

Name same but work different different.

```java
class Student{
    String name;
    int age;

    public void printInfo(String name){
        System.out.println(name);
    }

    public void printInfo(int age){
        System.out.println(age);
    }

    public void printInfo(String name, int age){
        System.out.println(name + " " + age);
    }
}
```

this is **polymorphism**

```java

Student s1 = new Student();

s1.name = "aman";
s1.age = 24;

s1.printInfo(s1.age);
```

```java
s1.printInfo(s1.name, s1.age)
``` 

first example me, it will take the second printInfo and in the second example code, it will take the third printInfo.

#### some rules

if the parameters u put need to be same, then the function return type must be different and true vice versa, if both same karna h, then another argument must be put in the parameter of function.

this is done in compile time polymorphism, so in compilation it detects all the problem in it.

# Inheritance

Ek class ke properties if dosri class lena chahti h, so its called inheritance.

now lets make a class and we will mae another class to link.

```java
class Shape {
    String color;
}

class Triangle extends Shape{

}

public class OOPS {

    public static void main(String args[]){

        Triangle t1 = new Triangle();
        t1.color = "red";
    }
}
```

so here we have not written, anything in triangle class but still we can get he output, so ek class ke methods and properties doosri class inherit krle.

### Uses of inheritance

reusability increases, for eg in a website, if we want a specific type of button, we will create only one class of that and rest all buttons will be inherited from it.

Base class --> child class

Four types of inheritance.

#### single level inheritance

```java

class Shape{
    public void area(){
        System.out.println("displays area"
        );

    }

    class Triangle extends Shape{
        public void area(int l, int h){
            System.out.println(1/2*l*h)
        }
    }

    class EquiTriangle extends Triangle{
        public void area(int l, int h){
            System.out.println(blahblah)
        }
    }

    class Circle extends Shape{
        public void area(int r){
            System.out.println(blahblha)
        }
    }


}
```
this was single level, multi level, hiearchial, and hybird level inheritance.


# Encapsulation

#### package

In a package, relative codes are written in collectively and a application can be divided into packages so that similiar functionalities are grouped together into packages.

**Built-in class** = java.util = this is a package in java which is built-in.

We can make our own package and import it into another java file.


```java
package bank;

class Account {
    public String name;

}
public class Bank{
    public static void main(String args[]){
        Account account1 = new Account();
        account1.name = "AKS";

    }

}
```


```java
import bank;

public class OOPS{

    public static void main(String args[]){
        bank.Account account1 = new bank.Account();
        account1.name = custormer1;
    }
}
```

Here we can call the functionality of another package, by first importing the package we created, then writing its use acc above.

### Access Modifiers

Permissions, some sensitive info to not be seen by unauthorised personnel.

4 types

1. public = if public written before any variable, this can be accessible to everyone, why main function is public, because compiler searches which function the work will start, so it must always be public rather than private. Eg = AKS will be visible public.

2. default = we don't need to write anything before, so here only the package which consists of that default type will be able to access , other package will not be able to see.

3. protected = the main package and sub-classes of other packages will only be able to access.

4. private = only the class which has the private type will only be able to access, which means we will not able to call it in the other classes.

How to access private = getters & setters

getters = info of the private info and then setting another value of the private info.


```java
//getter

public String getPassword(){
    return this.password;
}

public void String setPassword(){
    this.password = pass;
}

study about this more
```
# Encapsulation

combine data and function/methods inside a class. This process is called Encapsulation.

### Data hiding

with the use of access modifiers

### Abstraction

showing important things to user.

### Diff between data hiding and abstraction

DH is process of protecting members of class from unintended changes and abstraction is hiding the implementation details and showing only useful parts to the user.


```java

abstract class Animal{
    abstract public void walk();
}

class Horse extends Animal{
    public void walk{
        System.out.println("walks on four legs");
}

class Chicken extends Animal{
    public void walk(){
        System.out.println("Walks on 2legs");
    }
}
}

public class OOPS{

    public static void main(String args[]){
        Horse horse = new Horse();
        horse.walk;
    }
}
```

Nowwe know the properties of animal class, and all the other types of animals will have the properties of the animal class, so its not necessary that the user should go and check into the animal class to see the prop, its irrelevant.

so we can abstract the animal class, so it can make it an imagination but we cannot use the whole animal class, similiarly all animals walk so necessary hoga so we can make it abstract too.

If we walk the animal, the error will come that we cannot create the animal object as its abstract. the error which came was runtime error.

### PROp of abstract class

1. must be declared with an abstract keyword

2. can have abstract and non abstract methods in it.

3. cannot be instantiated(object nhi ban skta)

4. can have constructors and static methods also.

```java


abstract class Animal{
    Animal(){
        System.out.ln("You are creating a new animal");
    }
    abstract public void walk();
}

class Horse extends Animal{
    Horse(){
        System.out.println("created a horse");
    }
    public void walk{
        System.out.println("walks on four legs");
}

class Chicken extends Animal{
    public void walk(){
        System.out.println("Walks on 2legs");
    }
}
}

public class OOPS{

    public static void main(String args[]){
        Horse horse = new Horse();
        horse.walk;

    }
}
```
so when the constructor was created in animal class and horse class. so whenever we call a dervied class constructer, first the base class constructor is called then the derived class constructor.

This concept is called constructor chaining.

# Interface

how to have pure interfaces where only the important info is present and rest all information is hidden.
Interface cannot have constructors.

Now if we try to make a non-abstract(the method which has a body), that will also be not possible.

```java
interface Animal{
    void eat(){

    }
}
```

Now the keyword for interface is implements not extends.

```java
interface Animal{
    void walk();
}
class Horse implements Animal{
    public void walk() {
        System.out.println("walks on four legs");
    }
}

```java

interface Animal{
    void walk();
    
}
```

Interface

1. ALL the fields in interfaces are public static and final by default.

for eg in interface animal we add

`int eyes = 2` = this means that by default this remains static and cannot be changed.

2. methods are public & abstract by default.

no need to write public and abstract by default.

We can crreate more interfaces here.
like interface herbivores and we can implement both these interfaces in the class Horse.

<mark>THerefore her emultiple inheritance is possible through interfaces...</mark>

### Static

common and accessible to public.
for eg students can be differnet but students study in same school so we can make it static.

and we can call it directly as its static towards all classes

`Student.school = "KV"` rather than doing `Student student1 = new Student();` 

```java
Student.school = "KV";
Student student1 = new Student();
student1.name = "AKS";
System.out.printl(student1.school);
}
```
this will print the students name, if the school name is changed, it will be changed for every student object, so its easier, rather than not making it static and changing it for each school.

```java
public static void changeSchool(){
    school = "newschool";
}
```

we can also make static for the whole code block or for nested classes. To save memory static is used as its used for a single time of memory.

# Class in a class(nested)

``` java

class A{
    int age;

    class B{

        public void config(){
            
        }
    }
}
