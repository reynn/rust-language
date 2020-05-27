# Rust Resources <!-- omit in toc -->

- [Motivations](#motivations)
  - [Stumbles with Go](#stumbles-with-go)
  - [Stumbles with Python](#stumbles-with-python)
  - [How Rust may help solve these problems](#how-rust-may-help-solve-these-problems)
  - [Stumbles we are likely to have with Rust](#stumbles-we-are-likely-to-have-with-rust)
- [Learning materials](#learning-materials)
- [Sub Pages](#sub-pages)
- [Basic project structure](#basic-project-structure)
- [Reference Material](#reference-material)
- [Testing](#testing)
- [Code documentation](#code-documentation)
  - [Doc Links](#doc-links)
  - [Doc Examples](#doc-examples)
- [Some Useful Cargo plugins](#some-useful-cargo-plugins)
- [Crates (Libraries)](#crates-libraries)

## Motivations

### Stumbles with Go

Projects: support-clerk, mi6

1. lack of pre-defined project structures it was difficult to find one that
   lasted and made sense to everyone on the team.
1. \#1 also lead to difficulty in code management and maintenance
1. `go mod` while initially a big win for the community finally having a
   general package management tool has not gone as well as hoped and the
   syntax becomes difficult due to custom DSL used instead of common
   Lack of some typical data structures in addition to lack of generics lead
   to lots of boilerplate that was being solved in ways that are not best practice.
1. At least one library we were using has been broken randomly by
   the author changing the name.
1. Go build is a very simple build tool so it only builds a single binary
   at a time. This leads to additional software to manage builds
   like `Mage` to effectively handle building for Serverless applications.

### Stumbles with Python

Projects: herald, several other bot trials

1. Deploy/Build methods
1. Code being in production
1. Lack of strict typing lead to many failures only discovered in production

### How Rust may help solve these problems

1. `cargo` is the only package management tool and is heavily influenced by
   the community. It uses TOML which is a common data structure used in
   many cloud native software tools.
1. `cargo` is the tool that can do basically everything, it is the software
   install tool like `pip` using `cargo install exa` for instance. It also
   handles testing, doc building, project initialization and much more as
   well as having plugin crates to extend functionality further.
1. `cargo` and `rust` having a set structure also allows cargo to manage
   multiple binary builds on it's own by passing a `--bins` this will
   simplify the build process for us significantly.

### Stumbles we are likely to have with Rust

1. Rust has a newer type of memory management called a `Ownership`. The concept
   seems easy at first but it is a hurdle that could take a few weeks for
   everyone to fully understand. The up side to this however is it allows
   compile time checks of memory management so that null pointers are
   rare occurrences in production.

## Learning materials

Good places to get started learning Rust from the basics of
installation to async programming and procedural macros.

- [`Official Book Online`]
- [`Official Book Kindle/Paperback`]
- [`Cargo Book`]
- [`Build a CLI app`]

## Sub Pages

- [`Cargo`]
- [`Crates`]
- [`Language Features`]
- [`Patterns`]
- [`Setup`]

## Basic project structure

## Reference Material

These links will be more focused on places to quickly look up info
including compiler errors and CLI commands.

- [`Rust By Example`]
- [`Compiler Error Index`]

## Testing

Rust gives a few ways to do testing including typical unit and integration
testing as well as a great doc testing feature.

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

## Some Useful Cargo plugins

These add extra commands to cargo that make it even more useful!

- [`cargo-add`] - Add dependencies to your Cargo.toml without having to
  manually edit the file.

  ```console
  $ cargo install cargo-add --force
    Updating crates.io index
  Installing cargo-add v0.2.0
    ...
    Finished release [optimized] target(s) in 14.65s
   Replacing /Users/reynn/.cargo/bin/cargo-add
  $ cargo add clap
  $ cargo add clap --version '~2.3'
  ```

## Crates (Libraries)

See [] for a complete run down of crates.

<!-- Link section -->

[`official book online`]: https://doc.rust-lang.org/book/
[`official book kindle/paperback`]: https://www.amazon.com/Rust-Programming-Language-Covers-2018-ebook/dp/B07SRQ97RD
[`rust by example`]: https://doc.rust-lang.org/stable/rust-by-example/
[`rust by example - testing`]: https://doc.rust-lang.org/stable/rust-by-example/testing.html
[`compiler error index`]: https://doc.rust-lang.org/error-index.html
[`rust by example - documentation`]: https://doc.rust-lang.org/stable/rust-by-example/testing.html
[`build a cli app`]: https://rust-cli.github.io/book/index.html
[`cargo`]: /cargo.md
[`crates`]: /crates.md
[`language features`]: /features.md
[`patterns`]: /patterns.md
[`setup`]: /setup/general.md
[`cargo book`]: https://doc.rust-lang.org/cargo/index.html
