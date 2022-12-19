# Rust API docs

Liberland Blockchain Node contains thorough in-code documentation.

You can see latest deployment here:

* [main branch](https://liberland.github.io/rust/main/)
* [develop branch](https://liberland.github.io/rust/develop/)

See below for information on opening locally

## Seeing Rust API docs locally

Assuming you have your development environment setup (see [Build, Run & Test
guide](./dev.md)), execute following in main `liberland_substrate` repo
directory:

```
cargo doc --open --no-deps -p pallet-llm -p pallet-liberland-legislation -p pallet-liberland-initializer
```