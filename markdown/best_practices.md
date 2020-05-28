# Best Practices <!-- omit in toc -->

## Tooling

Between the official Rust and Cargo tooling and the amazing community involved with Rust
there is a lot of tools written in Rust and for improving Rust quality. Try to get involved
and see what you can find that work well and can improve the team workflow.

### Rustfmt

Use of the `rustfmt` tool will alert you to any formatting errors,
your commits should run this cleanly. Rustfmt is conveniently available
as a Cargo subcommand.

```shell
# Rustfmt is not included as a core piece of Cargo, we must install it first
$ rustup add component rustfmt
# this does install a binary for rustfmt, calling it with Rust is easier
# Now that it is installed we can run it
$ cargo fix # Basic command
# Compiles the program, if no lint warnings exist no output
$ cargo fix --allow-dirty --allow-staged # Run fix even if there are pending Git changes
# Compiles the program, if no lint warnings exist no output
```

### Clippy

Clippy is an additional linting tool that helps catch common mistakes.
Clippy can also fix some of the mistakes automatically with the `--fix` flag.

```shell
# Clippy is not included as a core piece of Cargo, we must install it first
$ rustup add component clippy
# Now that it is installed we can run it
$ cargo clippy # Basic
# Output will be any mistakes it finds or nothing if code is clean.
$ cargo clippy -- --fix # Autofix mistakes
# Output will be any mistakes it finds or nothing if code is clean.
```

## Coding style

Generally speaking follow guidelines for naming and coding styles from the [API Guidelines] page.

### Use preludes when possible

Many Rust crates provided a convenient import option called [preludes]. For instance when working with IO
you can import `std::io::prelude::*;` rather than importing the following: `std::io::{BufRead,Read,Seek,Write};`.
Anyone can implement preludes as a way to simplify imports.

### Use Expressions

A typical thing we see in some code bases for setting a variable to something based
on a different variable looks like this:

```groovy
// syntax highlighting is for Groovy but this is typical of various languages
def e;

if a {
  e = "hello";
} else {
  e = "world";
}
// or
def server_list = ansible.get_hosts();
def server;
for (s in server_list) {
  if (s.name == 'expected_host') {
    server = s;
    break;
  }
}
```

In Rust it is preferred to use the following:

```rust
let e = if a { "hello" } else { "world" };
// or
let server_list = ansible::get_hosts_from_inventory("$HOME/inventory.yaml");
let server: Server = server_list
    .iter()
    .filter(|x| x.name == "expected_host")
    .first();
```

### Iterators over loops

We often have to call APIs or similar tasks that may fail and use a loop to set a variable.

```groovy
// here we are getting a list of results from GitHub
// and creating a list if we want to use them
def allRepos = github.get_repo_list()
def requestedRepos = []
for (repo in allRepos) {
  if (repo.name.startswith('hello')) {
    requestedRepos.add(repo)
  }
}
```

```rust
let requested_repos = github.get_repo_list()
  .iter()
  .filter(|x| x.name.starts_with("hello"))
  .collect::<Vec<_>>();
```

### Enums over boolean or ints

Enums are a more expressive way of handling multiple cases and help with readability.

```rust
fn http_get(url: &str) -> Result<&str> {
  let response = http::request(http::method::GET, url)?;
  match response.status {
    http::status::Ok(resp) => Ok(resp.body),
    http::status::Forbidden(resp) => Err(ErrorKind::RequestFailed(resp.body)),
  }
}
```

### Handle `Option` and `Result` with `?`

Adjust code to return a [Result] even if it is a Void result. This allows changing

```rust
fn main() {
  let _conf_file = std::fs::read_to_string("config.yaml").unwrap("failed to load file");
  println!("Successfully loaded config file");
}
//
// TO
//
fn main() -> Result<()> { // () is our void return type
  // The error from read_to_string will bubble up to the Result by using `?`
  let _conf_file = std::fs::read_to_string("config.yaml")?;
  println!("Successfully loaded config file");
}
```

### Avoid unsafe! code

Unsafe code is rarely needed and the memory implications require considerable resources
to verify. If an external crate uses it and has a valid reason it can be considered if
it has sufficient testing and documentation however as a general rule we should try to
find an alternate crate.

### Implement traits

As a general rule you should implement the following traits:

- [Debug]
- [Display]

<!-- Links -->

[debug]: https://doc.rust-lang.org/std/fmt/trait.Debug.html
[display]: https://doc.rust-lang.org/std/fmt/trait.Display.html
[result]: https://doc.rust-lang.org/stable/std/result/
[option]: https://doc.rust-lang.org/stable/std/option/
[unsafe!]: https://doc.rust-lang.org/stable/std/keyword.unsafe.html
[api guidelines]: https://rust-lang.github.io/api-guidelines/checklist.html
[preludes]: https://doc.rust-lang.org/std/prelude/
