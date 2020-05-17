# Established Patterns <!-- omit in toc -->

- [Preludes](#preludes)
- [](#)

## Preludes

Instead of importing each module individually a single module can function as a way to import multiple other modules at the same time.

Example:

```rust
/// As a library user you can use the following import (main.rs)
use crate::prelude::*;

/// In place of much larger list of imports (prelude.rs)
pub use crate::{
    auth::{AnonymousAuthenticator, TokenAuthenticator, AppAuthenticator},
    client::GitHubClient,
    errors::APIError,
    traits::*,
};
```

## 