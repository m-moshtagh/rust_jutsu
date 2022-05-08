# Concepts

---

## Rust

Rust is a fresh low level system language which is quite familiar for being fast, good concurrency and greate performance.

Rust doesn't have a GC but uses a concept "Ownership".

## Cargo

Cargo is the build tool we use in rust projects.

We can create a binary project using cargo by:

`cargo new project_name --bin`

We have a cargo.tml file which is our package file. It has metadata of our project and also we can specify the dependencies of proejcts here.

We'll get a main.rs file which contains hello world.
`fn` is the macro respobsible to create a function in rust language. `main()` function is the entry point of our rust program.

> Library projects don't have main() function, only binary projects contain main function.

## Basics

### Variables

We can create variables in rust with `let`. variables are immutable by default in rust. We can make them mutable by `mut` keyword.

`let mut x = 5;`

Rust can infer variables or we can specify them explicitly in code.

`let x: u32 = 5;`

> This is important for rust managing the memory.

### Data types

#### Integers

- i8
- u8
- i16
- u16
- i32
- u32
- i64
- u64

Rust has two kind of integers signed & unsigned. The number shows the amount of bits the number is taking in the memory.

We also have isize & usize The actual memory these two take is based on the computer we are running the code on. For x64 takes 64 bit and similar on x86 which is 32 bits.

#### Floats

- f32
- f64

#### Boolean

- bool

This is either true or false.

#### Characters

- char

#### Tuples

Collections of data which necessaily doesn't need to be the same type.

`let t: (i32, f64, char) = (46, 2.5, 'j');`

> These are useful for something like destructing.

We can also use pattern matching with this tupple and have some variabels:

`let (z, _, x) = t;`

This will match the z with 46 in `t`, ignores the second and matches j to `x` variable.

We can also access the tuple elements by indices.

`t.0` gives us 46.

#### Arrays

Collections of elements with one type.

`let a = [1,2,3,4];`

We can access them using indices.

`a[0]`

> Arrays are useful when we want the data to be allocated on the stack rather than the heap and, when we want to make sure to have fixed amount of elements.

> We have Vector for dynamic arrays.

### Operators

- Mathematics [+ - * / %]
