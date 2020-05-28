# Testing <!-- omit in toc -->

Rust gives a few ways to do testing including typical unit and integration
testing as well as a great doc testing feature.

- [Rust By Example - Testing]

## Code example

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
    pub fn hello(&self) {
        println!("Hello, {}!", self.name);
    }
}
````

## Unit Testing

Unit testing will live right beside the code in a testing submodule. These should be quick tests
that can be mocked and are very focused on a specific function and its inputs/outputs. These
help ensure the small things continue doing as we expect. These should include tests for any private
methods/functions as well.

## Integration testing

Integration testing in the Rust specific context is focused around a modules inputs and outputs rather than
specific functions.

## Documentation testing

### Examples

## Benchmarking

[rust by example - testing]: https://doc.rust-lang.org/stable/rust-by-example/testing.html
