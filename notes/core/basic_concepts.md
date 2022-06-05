# Concepts

---

## Rust

Rust is a fresh low level system language which is quite familiar for being fast, good concurrency and greate performance.

Rust doesn't have a GC but uses a concept "Ownership".

## Cargo

Cargo is the build tool we use in rust projects.

We can create a binary project using cargo by:

`cargo new project_name --bin`

We have a cargo.toml file which is our package file. It has metadata of our project and also we can specify the dependencies of proejcts here.

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

We can define tuples inside tuples too.

`let f = (5, t)` OR `let f = (5, (46, 2.5, 'j'))`

If we try to print f.1, The statement will fail because of trait which we are going to learn later.

We can use `{:?}` in print macro and boom we can print it. This sign is called debug flag, since tuples have debug traits built in we can do it this way. To beautify the output we can use `{:#?}`

> This debug trait doesn't work with too long tuples.

If We declare an empty touple, This is called a unit value. For example main() returns an empty touple which means they don't return anything.

#### Arrays

Collections of elements with one type.

`let a = [1,2,3,4];`

We can access them using indices.

`a[0]`

> Arrays are useful when we want the data to be allocated on the stack rather than the heap and, when we want to make sure to have fixed amount of elements.
> We have Vector for dynamic arrays.

We can declare array datatype and capacity in signature.

`let xs: [i32; 5] = [1,5,16,6,8];`

> We can access array length by `len()` function.

The `&` is operator like pointers to refrence to something. When use arrays like this:

`let yx : &xs[2..4];`

What happens is that it populates the yx array with the xs 2 till 4 indices. The 4 is not included.

We can use debug trait to print the whole arrays.

#### Strings

We can define Strings in rust with double quots and functions but, both these will give us different types. In rust Strings are compund types like arrays. When we write

`let s = "String";`

This will return type of `&str` which we call slice of String. However if we

`let s = String::from("String!");`

This will return String type.

We can take a slice (subString) of a String like we did back in arrays.

`let ss = &s[2..4];`

We can concat our Strings using `+` operator.

### Operators

- Mathematics [+ - * / %]

### Print

We have macros to print values in terminal or console.
`println!()`

In this println we can format the string like logback or slf4j in java.

`println!("{} {}", 1, 6)`
