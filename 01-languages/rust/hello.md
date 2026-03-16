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

> use std::io;

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