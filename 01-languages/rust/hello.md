# Hello, world 

```rust
fn main() {
    println!("Hello, World");
}
```

```bash
rustc main.rs
./main
```

the fn main function, here main is the first code that runs in a program, it has no parameters inside it currently.

> println! calls a rust macro, if there was a function inside the println then it would be written without this `!` sign.

## Cargo

rust's build system and package manager. This can handle rust projects and do some tasks for us like building code, downloading the packages needed.

Whenver we create a complex project, we need to use cargo to add more and new dependencies as it gets much easier with it.

Lets create a new project using cargo.

```bash
$ cargo new hello_cargo
$ cd hello_cargo
```

after this cargo has generated some files and a directory, Cargo.toml file and a src directory with main.rs inside and a .gitignore file too.

TOML(tom's obvious, minimal language) format is cargo's config format.

When you cat the cargo.toml file.

```bash

[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2024"

[dependencies]

```

the statements after package is config a package.

dependencies will vary according to the projects dependencies.

Cargo helps to organise various projects.

Cargo expects that the main source code is to be stored in the `src` directory and the top level directory to be just README files, licenses etc.


> IF you didnt use cargo to create the file, you can just move the file into `src` directory and after that run `cargo init` to generate cargo.toml file.

### Building and running a cargo project.

in the project main directory run

`cargo build`

this creates an exec file in target/debug/hello_cargo rather than in current directory.
The default build is called debug build thats why cargo puts binary in dir called debug.

can run the exec through

`./target/debug/hello_world`

Now instead of using `cargo build` and create an executable file everytime we can use `cargo check` to see if the program is compiling or not. for big projects we use this to know if its still compiling or not. use cargo build when its completed and ready to use an executable.

U can use `cargo run` directly to run rather than pinpointing location and running it. 

### Building for release

`cargo build --release` 
this compiles it with optimisations which makes the code much faster to run but takes more time to compile, so there are two phases, one in development so no need to use this command when continous compiling and all is required, and other when users use it so no need to rebuilt it repeatedly and to run as fast as  possible.

# Guessing game

First part of the game is to ask user input, process input and check the input is in expected form, will be done main.rs

```rust
use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}
```

we will go line by line
```rust
 use std::io;
```
means input output library comes into scope from the standard library `std`.

Some predefined set of items brings into scope in every program, this is called *prelude* in https://doc.rust-lang.org/stable/std/prelude/index.html.

so here if you explicitly wants to bring a type into the scope you use `use` statement.

#### Storing values into variables

```rust
let mut guess = String::new();
```

another eg.

```rust
let apples = 5
```
so in Rust, variables are immutable by default, meaning once a value given to a variable it wont change, so to make a variable mutable we use `mut`.

```rust
let mut guess = String::new();
```

the String::new creates a new instance from the type String. new is the associated function, creates a new empty string.

### Recieving user input

`io::stdin()` = this instanciates std::io::Stdin which handles standard input in your terminal.

now in this stdin has a method called `read_line` and we pass `&mut guess` so that it know in which variable it must store the user input.

& => references, they are immutable by default.

the next line
`.expect("failed to read code");` this the part of same logical single line of code.

now after the users enter string it stores, but also returns a `Result` value. This is a enum and can exist in multiple states called variants. Their variants are `Ok` and `Err`.

Result has a method called `expect`, so if the instance of result gives Err, expect will cause program to crash and display the msg u passes as an argument

We can also ignore this but its safe practice to do error handling in code.

### printing the values

`println!("You guessed: {guess}");`. {} acts a as a placeholders for the value of variable that gets printed when the variable is put inside curl bbraces. When evaluating the result of some ops, put empty curly braces and followed by the variables operation.

```rust
let x = 5;
let y = 10;

println!("x = {x} and y + 2 = {}", y + 2);
```

## Generating a secret number

random number between 1 to 100, we will use `rand` crate.

A crate is ocllection of rust source code files. this collection of codes to be used in other programs not to be used on its own. So we have to modify in the dependencies to inlcude rand with the version number

**Semantic Versioning** and crates.io is where people post in the rust ecosystem about their projects.

After doing cargo build, when including the rand dependencies, it sees the .toml file and downloads any dependencies and related to it, then after we do cargo build it will just reuse and compile.

### reproducible builds

cargo has an mechnaism to make sure for example, if rand releases a new version, it fixes a bug but also breaks ur programs, to fix this when we do cargo build the first time, it creates a cargo.lock file. So it figures out all the dependencies that fits the criteria, so when we build the project in future, cargo will use the dependencies listed in the cargo lock file, so it doesnt automatically update unless explicitly saide so.

### updating crate

we can update crate through update command which makes cargo ignore lock file and figure out the latest versions. So in the specific case, rand has been choosen as atlease 0.8.5 but less than 0.9.9.

## Generating random number
```rust
use std::io;

use rand::Rng;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    println!("The secret number is: {secret_number}");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}
```

we first added rand::Rng, rng defines the methods random number generators implement.

`rand::thread_rng` is the function which gives a particular random no. generator.

then next is `gen_range` method on random no. generator. this take range expression as an argument and generates acc to that range. the form is `start..=end` so `1..=100`. To know more functionality of each cargo crates use the documentation to know.

## Comparing the guess to a random number

we add another `use` and add `std::cmp::Ordering`, its an enum and has variants like `Less`, `Greater`, and `Equal`. `cmp` method compares two values and can be called on anything that need to be compared.

`match` expression is used to decide what to do based on which variant ordering has returned.

Now after compiling we see that, the number stored in guess is string while secret_number is stored by default as i32, 32-bit number so the compilation fails.

So we may want the string to be converted into number.

So we add

`let guess: u32 = guess.trim().parse().expect("Please type a number!");` = just below `.expect`, if Result shows Err then the msg gets printed.

```rust
use std::io;

use rand::Rng;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    println!("The secret number is: {secret_number}");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    let guess: u32 = guess.trim().parse().expect("Please type a number!");

    println!("You guessed: {guess}");

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => println!("You win!"),
    }
}
```

So we created another variable guess, but doesnt it have another guess, rust has a feature of shadowing which lets us reuse the `guess` variable without forcing us to create more names.

expression - `guess.trim().parse()`= trim method deletes any whitespace at begining or end, must be dont to convert string to u32. So whenever we press enter after entering lets say `5`, so after enter it add newline character = `5\n`, so `trim` eliminates this \n.

Parse method converts string to another type. we want to convert to number so we tell rust `let guess: u32`, u - unsigned. If a string contains `A%`, then no way ot convert that logicaly. Parse method returns a `Result` same as readline, same treatment using expect method as always.

## Allowing multiple guesses with looping

`loop` keyword creates infinite loop.

```rust
    // --snip--

    println!("The secret number is: {secret_number}");

    loop {
        println!("Please input your guess.");

        // --snip--

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Great;er => println!("Too big!"),
            Ordering::Equal => println!("You win!"),
        }
    }
}
```

but this creates another problem it wont ever quit.

one way to take adv is writing the string instead of number so it may quit.

### Quit after correct guess

```rust
        // --snip--

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```

just added break in the equal section.

### error handling 

instead of crashing the program, lets handle the problem

```rust
        // --snip--

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        // --snip--
```

So instead of expect, we use match here as Result has different variants, if string->number(OK), if not then Err(_), `_` means catch-all, so whateevrt the info is isnide, the program tells to continue on to the next iteration and ask for another gues..