# Language Features <!-- omit in toc -->

- [Ownership and Borrowing](#ownership-and-borrowing)
- [`Option` and `Result`](#option-and-result)
- [Lazy iterators](#lazy-iterators)
- [Macros](#macros)
- [Enums](#enums)

## Ownership and Borrowing

## `Option` and `Result`

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

Similar to generators in Python where the call to `.iter()` just returns the option to retrieve next instead of actually getting the data.
This can lead to reduction in API calls since paging doesn't have to happen up front.

Some real examples from our existing resposibilities.
Lookups to GitHub for teams can be sorted and once `bh-` teams no longer show in results we can stop calling the API since we wont care about the rest.

## Macros

Macros provide a form of code generation to reduce boilerplate code.

## Enums

Enums exist in a lot of languages but were not properly supported in Go. Rust expands on normal
