# Rust Resources

## Motivations

### Stumbles with Go

Projects: Support Clerk, MI6

1. lack of pre-defined project structures it was difficult to find one that lasted and made sense to everyone on the team.
1. 1 also lead to difficulty in code management and maintenance
1. `go mod` while initially a big win for the community finally having a general package managment tool has not gone as well as hoped and the syntax becomes difficult due to custom DSL used instead of common
   Lack of some typical data structures in addition to lack of generics lead to lots of boilerplate that was being solved in ways that are not best practice.
   Atleast one library we were using has been ripped out from by the author changing the name.
1. Go build is a very simple build tool so it only builds a single binary at a time. This leads to additional software like `Make` or `Mage` in our case.

### Stumbles with Python

Projects: Herald

1. Deploy/Build methods
1. Code being in production
1. Lack of strict typing lead to many failures only discovered in production

### How Rust can solve these problems

1. `cargo` is the only package management tool and is heavily influenced by the community. It uses TOML which is a common data structure used in many cloud native software tools.
1. `cargo` is the tool that can do basically everything, it is the software install tool like `pip` using `cargo install exa` for instance. It also handles testing, doc building, project initialization and much more as well as having plugin crates to extend functionality further.
1. `cargo` and `rust` having a set structure also allows cargo to manage multiple binary builds on it's own by passing a `--bins` this will simplify the build process for us significantly.

### Stumbles we are likely to have with Rust

1. Rust has a newer type of memory management called a `Ownership`. The concept seems easy at first but it is a hurdle that could take a few weeks for everyone to fully understand. The up side to this however is it allows compile time checks of memory management so that null pointers are rare occurences in production.

## Learning materials

Good places to get started learning Rust from the basics of installation to async programming and procedural macros.

- [`Official Book Online`]
- [`Official Book Kindle/Paperback`]

## Interesting/Cool language features

- Match statements
- Option and Result types
- Macros
- Lazy Iterators
- Generics
- Enums and Enum Variants

_Invalid memory is still possible but difficult to manage outside of `unsafe!` code._

## Common patterns in the community

- Preludes: Instead of importing each module individually a single module can function as a way to import multiple other modules at the same time.

Example:

```rust
/// As a library user you can use the following import
use
/// In place of much larger list of imports
pub use crate::{
    auth::{AnonymousAuthenticator, TokenAuthenticator, AppAuthenticator},
    client::GitHubClient,
    errors::APIError,
    traits::*,
};
```

## Basic project structure

## Reference Material

These links will be more focused on places to quickly look up info including compiler errors and CLI commands.

- [`Rust By Example`]
- [`Compiler Error Index`]

## Testing

Rust gives a few ways to do testing including typical unit and integration testing as well as a great doc testing feature.

- [`Rust By Example - Testing`]

## Code documentation

Rust provides a full markdown engine for code documentation using a `///` block.
In you can document the crate and submodules with markdown using `//!` that
summarizes usage of the crate or module.

### Doc Links

- [`Rust By Example - Documentation`]

### Doc Examples

````rust
/// A human being is represented here
pub struct Person {
    /// A person must have a name, no matter how much Juliet may hate it
    name: String,
}

impl Person {
    /// Returns a person with the name given them
    ///
    /// # Arguments
    ///
    /// * `name` - A string slice that holds the name of the person
    ///
    /// # Example
    ///
    /// ```
    /// // You can have rust code between fences inside the comments
    /// // If you pass --test to Rustdoc, it will even test it for you!
    /// use doc::Person;
    /// let person = Person::new("name");
    /// ```
    pub fn new(name: &str) -> Person {
        Person {
            name: name.to_string(),
        }
    }

    /// Gives a friendly hello!
    ///
    /// Says "Hello, [name]" to the `Person` it is called on.
    pub fn hello(& self) {
        println!("Hello, {}!", self.name);
    }
}
````

## Crates (Libraries)

List of crates that are likely to be common among many projects
Click on a crate name to go to the relevant information

- [error_chain](#error_chain) - Error handling simplification and proposed for future implementation into core language.
- [chrono](#chrono) - Superset of the std time library, makes it easier to handle time data with timezones in particular.
- [log+simplelog](#logging) - Logging library, `log` will be used everywhere to send info, debug etc logs. Simplelog will be used in a main to setup a logging pipeline with output methods such as terminal or files.
- [clap](#CLI) - Setup parsing for command line arguments.
- [serde](#serde) - Serialize/Deserialize framework, has various plugins for data structure formats such as TOML, JSON, YAML and many others.
- [reqwest](#reqwest) - HTTP client for making requests to services

### error_chain

[![error_chain license](https://img.shields.io/crates/l/error-chain.svg?style=flat-square)](https://crates.io/crates/error-chain)
[![error_chain latest version](https://img.shields.io/crates/v/error-chain.svg?style=flat-square)](https://crates.io/crates/error-chain)
[![error_chain github](https://img.shields.io/github/languages/top/rust-lang-nursery/error-chain?style=flat-square)](https://github.com/rust-lang-nursery/error-chain)

Documentation for error_chain can be found at [docs.rs](https://docs.rs/error-chain).

[`official book online`]: https://doc.rust-lang.org/book/
[`official book kindle/paperback`]: https://www.amazon.com/Rust-Programming-Language-Covers-2018-ebook/dp/B07SRQ97RD
[`rust by example`]: https://doc.rust-lang.org/stable/rust-by-example/
[`rust by example - testing`]: https://doc.rust-lang.org/stable/rust-by-example/testing.html
[`compiler error index`]: https://doc.rust-lang.org/error-index.html
[`rust by example - documentation`]: https://doc.rust-lang.org/stable/rust-by-example/testing.html
