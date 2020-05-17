# Best Practices <!-- omit in toc -->

- [Rustfmt](#rustfmt)
- [Clippy](#clippy)

## Rustfmt

Use of the `rustfmt` tool will alert you to any formatting errors,
your commits should run this cleanly. Rustfmt is conveniently available
as a Cargo subcommand.

```shell
# Rustfmt is not included as a core piece of Cargo, we must install it first
$ rustup add component rustfmt
# Now that it is installed we can run it
$ cargo fix # Basic command
# Compiles the program, if no lint warnings exist no output
$ cargo fix --allow-dirty --allow-staged # Run fix even if there are pending Git changes
# Compiles the program, if no lint warnings exist no output
```

## Clippy

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
