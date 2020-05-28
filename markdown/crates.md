# Rust Crates <!-- omit in toc -->

## Error Handling

### Error Chain

[![error_chain](https://img.shields.io/crates/v/error_chain.svg?style=flat-square&label=error_chain%20crates.io)](https://crates.io/crates/error_chain)
[![error_chain](https://img.shields.io/crates/v/error_chain.svg?style=flat-square&label=error_chain%20docs.rs)](https://docs.rs/error_chain)

Documentation for error_chain can be found at [docs.rs](https://docs.rs/error-chain).

Error chain is designed to simplify error handling by providing a simplified `Result` enum as well as `bail!` and `ensure!` macros.
Error chain is part of the Rust nursery, this means there is a chance of it being included in future official releases.

### Anyhow

[![anyhow](https://img.shields.io/crates/v/anyhow.svg?style=flat-square&label=anyhow%20crates.io)](https://crates.io/crates/anyhow)
[![anyhow](https://img.shields.io/crates/v/anyhow.svg?style=flat-square&label=anyhow%20docs.rs)](https://docs.rs/anyhow)

Anyhow provides a simpler API compared to error-chain by leaving custom error handling to the developer.
Where error_chain uses a macro to override the default std::result::Result anyhow provides its own version of Result

[![thiserror](https://img.shields.io/crates/v/thiserror.svg?style=flat-square&label=thiserror%20crates.io)](https://crates.io/crates/thiserror)
[![thiserror](https://img.shields.io/crates/v/thiserror.svg?style=flat-square&label=thiserror%20docs.rs)](https://docs.rs/thiserror)

Anyhow is likely going to be used with another library like `thiserror` that provides a wrapper around the `std::error::Error` trait

## Logging

| name       | crates.io                                                                                                                         | docs.rs                                                                                                                  |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| log        | [![log-log](https://img.shields.io/crates/v/log.svg?style=flat-square&label=)](https://crates.io/crates/log)                      | [![log-log](https://img.shields.io/crates/v/log.svg?style=flat-square&label=)](https://docs.rs/log)                      |
| simplelog  | [![log-simplelog](https://img.shields.io/crates/v/simplelog.svg?style=flat-square&label=)](https://crates.io/crates/simplelog)    | [![log-simplelog](https://img.shields.io/crates/v/simplelog.svg?style=flat-square&label=)](https://docs.rs/simplelog)    |
| fern       | [![log-fern](https://img.shields.io/crates/v/fern.svg?style=flat-square&label=)](https://crates.io/crates/fern)                   | [![log-fern](https://img.shields.io/crates/v/fern.svg?style=flat-square&label=)](https://docs.rs/fern)                   |
| env_logger | [![log-env_logger](https://img.shields.io/crates/v/env_logger.svg?style=flat-square&label=)](https://crates.io/crates/env_logger) | [![log-env_logger](https://img.shields.io/crates/v/env_logger.svg?style=flat-square&label=)](https://docs.rs/env_logger) |

In a project you would use the `log` crate always and one of the others in conjunction. `log` crate provides the macro to send a log event at a specific level. The other crates provide the way to output the calls to `log`.

## chrono

[![chrono](https://img.shields.io/crates/v/chrono.svg?style=flat-square&label=chrono%20crates.io)](https://crates.io/crates/chrono)
[![chrono](https://img.shields.io/crates/v/chrono.svg?style=flat-square&label=chrono%20docs.rs)](https://docs.rs/chrono)

Chrono is a date time library that improves on the `std::time` crate. Most important distinction is being time zone aware by default.

## clap

[![clap](https://img.shields.io/crates/v/clap.svg?style=flat-square&label=clap%20crates.io)](https://crates.io/crates/clap)
[![clap](https://img.shields.io/crates/v/clap.svg?style=flat-square&label=clap%20docs.rs)](https://docs.rs/clap)

Clap is used to build CLI programs. Primarily it handles parsing of arguments and mapping to a struct.

Clap 3 is in beta, we should use that instead of 2.3x since the differences between them are huge and retrofitting later doesn't make sense.

## serde

[![serde](https://img.shields.io/crates/v/serde.svg?style=flat-square&label=serde%20crates.io)](https://crates.io/crates/serde)
[![serde](https://img.shields.io/crates/v/serde.svg?style=flat-square&label=serde%20docs.rs)](https://docs.rs/serde)

Serde provides an interface between data structures. It doesn't do any of the parsing itself but provides a common interface for others to build on.

We will likely use the following crates to actual handle the parsing:

| Format | Crate                                                                                                                         |
| ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| TOML   | [![toml](https://img.shields.io/crates/v/toml.svg?style=flat-square&label=)](https://crates.io/crates/toml)                   |
| YAML   | [![serde_yaml](https://img.shields.io/crates/v/serde_yaml.svg?style=flat-square&label=)](https://crates.io/crates/serde_yaml) |
| JSON   | [![serde_json](https://img.shields.io/crates/v/serde_json.svg?style=flat-square&label=)](https://crates.io/crates/serde_json) |

## reqwest

[![reqwest](https://img.shields.io/crates/v/reqwest.svg?style=flat-square&label=reqwest%20crates.io)](https://crates.io/crates/reqwest)
[![reqwest](https://img.shields.io/crates/v/reqwest.svg?style=flat-square&label=reqwest%20docs.rs)](https://docs.rs/reqwest)

Reqwest is an HTTP Client for making requests to an external HTTP service. Reqwest is built on the [Hyper](https://github.com/hyperium/hyper) crate that offers low level implementations of HTTP Client and Servers.

## warp

[![warp](https://img.shields.io/crates/v/warp.svg?style=flat-square&label=warp%20crates.io)](https://crates.io/crates/warp)
[![warp](https://img.shields.io/crates/v/warp.svg?style=flat-square&label=warp%20docs.rs)](https://docs.rs/warp)

Warp is a HTTP Server built on [Hyper](https://github.com/hyperium/hyper).
