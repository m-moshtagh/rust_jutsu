# Structs Functions Methods

## Struct

Structs are concept like object oriented programming classes. We can define a custom structure with special fields.

```Rust
struct Object {
    width  : u32,
    height : u32,
}
```

## Function

We can also define functions with fn keyword, define parameters it gets and a return type for what it returns. In rust
We don't need to explicitly use return keyword we just need to type the expression without semicolon.

```Rust
fn area(obj : &Object) -> u32 {
    obj.width * obj.height
}
```

Now in order to create an instance from struct and call the area function:

```Rust
fn main() {
    let o = Object {
        width = 10,
        height = 5,
    };

    prtinln!("area equals to {} x {} = {}", o.width, o.height, area(&o));
}
```

## Methods

In order to define methods specifically for the struct type we use `impl` keyword and write the functions inside it.

### Self keyword

This keyword refers to the Struct type we used in front of impl keyword. After this we can access the method via instance
name.

```Rust
impl Object {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}
```

now we can use o.area() and it will automatically pass the self object as argument.

## Related functions

If we define a new method inside impl that creates a new object

```Rust
impl Object {
    fn area(&self) -> u32 {
        self.width * self.height
    }

    fn new(width: u32, height: u32) -> Object {
        Object {
            width: width,
            height: height,
        }
    }
}
```

now if we try to access it via o.new() it will fail. impl actually creates a namespace called object for the object type
which it is tighting into. To access this new function we need the namespace.

```Rust
let obj = Object::new(10, 5);
```

> Rust can automatically detect if argumetnt passed has the same name.

```Rust
fn new(width: u32, height: u32) -> Object {
        Object {
            width,
            height,
        }
    }
```

We usually as a conventions put methods above the relational functions. We can also define another impl and put relational functions there.

# Derive traits

If we try to print the object instance with the debug trait, it will fail because we haven't derived it yet. We can do it
by adding `#[derive(Debug)]`
What if we want to print it the normal way using the display trait. It will error so that we can't derive it. We just need to use it manually. we import this, where display trait resides: `use std::fmt` then we create an impl to implement
the fmt display.

```Rust
impl fmt::Display for Object {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "({}, {})", self.width, self.height)
    }
}
```
