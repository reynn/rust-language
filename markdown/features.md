# Language Features <!-- omit in toc -->

## Ownership and Borrowing

[Ownership Chapter]

Rust does not force you to manage memory directly using `alloc` and `dealloc`, it also does not use a
Garbage collection system such as Java and Go. Instead when variables go out of scope they are cleaned up.

```rust
fn main() {
    let x = 10;
    { // This is a closure and is a separate scope from the main func
        let y = 20;
        println!("x + y = {}", (x + y));
    } // This is the end of the closure, y will be unavailable after this
    println!("y is {}", y);
}
```

When attempting to run this code you will get the following error

```shell
$ cargo run
Compiling rust-basic-app-template v0.1.0 (/Users/reynn/git/github.com/reynn/rust-basic-app-template)
error[E0425]: cannot find value `y` in this scope
 --> src/main.rs:8:25
  |
8 |     println!("y is {}", y);
  |                         ^ help: a local variable with a similar name exists: `x`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0425`.
error: could not compile `rust-basic-app-template`.

To learn more, run the command again with --verbose.
```

## `Option` and `Result`

[Option Chapter]

[Result Chapter]

A typical pattern in Go is to return a type + an error like shown in the following snippet

```golang
// This function wont fail the program but still has to return an error type
func add(a, b: int) (int, error) {
    if b < 0 || a < 0 {
        return 0, fmt.Error("Not going to add a negative number")
    }
    return a + b
}

// This function could cause the app to fail if not successful which makes sense for an error
func GetClient(auth *Authenticator) (*Client, error) {
    if auth == nil {
        return nil
    }
    // newClient is a method that initializes the client and ensures successful auth
    // signature is similar to this GetClient method
    return newClient(auth)
}

func main() {
    res, err := add(1, -5)
    if err != nil {
        fmt.Printf("Failed to add the numbers together %v", err)
    } else {
        fmt.Printf("Result is %d", res)
    }

    if client, cErr := GetClient(AnonAuth{}); err != {
        executeLoop(client)
    } else {
        panic(cErr)
    }
}
```

In Rust this is made easier by the `Option` and `Result` types.

```rust
fn add(a: i32, b: i32) -> Option<i32> {
    Some(a+b)
}

fn get_client(auth: &Authenticator) -> Result<Client> {
    Ok(Client::new(auth)?) // shortcut, `?` will return out the error when the function returns a Result
}

// Result<()> is a void result, this is so you can still use the ? shortcut in main
fn main() -> Result<()> {
    if let Some(res) = add(1, 80) {
        assert_eq!(res, 81);
    };

    match get_client(auth::Anonymous()) {
        Ok(c) -> c.whoami()?,
        Err(e) -> {
            eprintln!("Error creating a new client {}", e);
            std::process::exit(2);
        }
    }
}
```

## Lazy iterators

Similar to generators in Python where the call to `.iter()` just returns the
option to retrieve next instead of actually getting the data.
This can lead to reduction in API calls since paging doesn't have to happen up front.

Some real examples from our existing responsibilities.
Lookups to GitHub for teams can be sorted and once `bh-` teams no longer show
in results we can stop calling the API since we wont care about the rest.

## Macros

Macros provide a form of code generation to reduce boilerplate code. The earliest
macro a new Rust dev will use is the `println!` macro.

```rust
// This is provided as a convenient macro
println!("Hello World");
// The compilation will expand this macro to something like
{
  $crate::io::_print(std::fmt::Arguments::new_v1(&[], &[]));
}
```

### Declarative Macros

[Declarative Macros Chapter]

Declarative macros can be defined anywhere using the `macro_rules!` macro.
This is a good candidate for basic code that must be reused in several places.

### Procedural Macros

[Procedural Macros Chapter]

Procedural macros accept some code as an input, operate on that code, and produce some code as an output rather than matching against patterns and replacing the code with other code as declarative macros do.

## Enums

Enums exist in a lot of languages but were not properly supported in Go.
Rust expands on normal enums by having Enum variants as well. The [Enum Chapter]
in the Rust book has a really good intro on enums and how to define variants
but at a high level overview.

### Basic enum example

```rust
/// Define a basic enum to switch between IP v4 and v6.
enum AddressVersion {
    V4,
    V6,
}
struct IPAddress {
    version: AddressVersion,
    address: String,
}
impl IPAddress {
    fn new(address: String) -> Result<Self> {
        /// parse_version isn't defined here but the signature is
        /// parse_version(address: &str) -> Result(AddressVersion)
        if let Ok(address) = parse_version(address)? {
            Ok(
                Self {
                    version,
                    address,
                }
            )
        }
    }
}

#[cfg(test)]
mod address_tests {
    fn test_basic() {
    }
}
```

### Enum Variants

```rust
/// Simplify the basic example with a variant
enum IPAddress {
    V4(String),
    V6(String),
}
```

<!-- Links below -->

[enum chapter]: https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html
[ownership chapter]: https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html
[option chapter]: https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html?highlight=option#the-option-enum-and-its-advantages-over-null-values
[result chapter]: https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html
[declarative macros chapter]: https://doc.rust-lang.org/book/ch19-06-macros.html#declarative-macros-with-macro_rules-for-general-metaprogramming
[procedural macros chapter]: https://doc.rust-lang.org/book/ch19-06-macros.html#procedural-macros-for-generating-code-from-attributes
