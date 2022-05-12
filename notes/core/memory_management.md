# Memory management

## How memory management works

Stack and Heap are parts of memory that are available for us to aid us in Runtime coding. Stack stores values to get them and removes them in opposite order. Stack is fast beacuse CPU doesn't need to process any searches for getting data. In memory all these data are fixed size.

In rust, all literals are stored on stack. For complicated data we use Heap. Heap is a kind of parallel memory with bunch of pointers that point to memory various locations. Heap is slower beacuse CPU needs to process where pointers follow to the complicated data and, this data can get larger and complicated.

Languages like C and C++ can directly manipulate parts of memory using pointers and this may be harmful. Languages like Java, C#, Ruby and Python have garbage collectors that release free memories refrences.

> If we use two pointers to point to one location derefrencing them will harm the memory.

Rust is something in the middle. Rust uses Ownership which has three rules:

- Each variable has a value and the variable itself is called owner. for example:<br/> `let x = 1;` <br/> Means `x` owns `1` because `1` is a literal which is stored on the stack not the heap. Each piece of data can only have one owner at the time and when the owner goes out of the scope the value is gonna be dropped.

* If we define a variable and instantiate the second one with the first varaible and then we try to do something with the first variable we encounter a problem. Here We use something called `borrowint(&)` What this does asks the first variable to borrow the value for moment.

```rust
let s = String::from("RUST");
let y = &s;
println!(s); // if we don't borrow, doesn't compile.
```

- We can also transfer the ownership from a function to another function which is called moving.

```Rust
fn take(v: Vec<i32>){
    println!("we took v: {}", v[10] + v[100]);
}
fn main(){
    let mut v = Vec::new();

    for i in 1..1000 {
        v.push(i);
    }
    take(v);
    println!("finished");
}
```

- We also have something called copying Which is applicable for literals because they are stored on the stack.

```Rust
fn cop(a: i32, b:i32){
    println!("{}", a + b);
}
fn main(){
    let a = 32;
    let b = 45;
    cop(a, b);
    println!("we still have a: {} and b:{}", a, b);
}
```

> We can use the actual value of the referenced itme using an `*`.
