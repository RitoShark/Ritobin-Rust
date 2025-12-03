# ritobin_rust

A high-performance Rust library and CLI tool for parsing and converting League of Legends binary property files (`.bin` format).

## Features

- 🔄 **Multiple Formats**: Binary (.bin), Text (.py), and JSON
- 🔑 **Hash Support**: FNV1a and XXH64 hash loading and unhashing
- 🎯 **Drag & Drop**: Just drag .bin files onto the executable
- 🛠️ **CLI Tools**: Info, validate, and conversion commands
- � **Well  Documented**: Full rustdoc with examples

## Quick Start

### Installation

```bash
cd ritobin_rust
cargo build --release
```

The executable will be at `ritobin_rust/target/release/ritobin_rust.exe`

### Drag & Drop Usage

Simply drag any `.bin` file onto the executable and it will automatically convert to `.py` text format in the same directory.

### Command Line Usage

```bash
# Convert formats
ritobin_rust input.bin output.py
ritobin_rust input.py output.json

# Show file information
ritobin_rust info file.bin

# Validate files
ritobin_rust validate --recursive directory/
```

## Library Usage

```rust
use ritobin_rust::binary::read_bin;
use std::fs;

// Read a binary file
let data = fs::read("champion.bin")?;
let bin = read_bin(&data)?;

// Convert to text format
let text = ritobin_rust::text::write_text(&bin)?;
fs::write("champion.py", text)?;
```

## Examples

The `ritobin_rust/examples/` directory contains:
- `read_bin.rs` - Basic bin file reading
- `write_bin.rs` - Creating bin files from scratch
- `convert_formats.rs` - Format conversion
- `unhashing.rs` - Hash loading and unhashing

Run with: `cargo run --example read_bin -- file.bin`

## Documentation

Generate and view full documentation:

```bash
cd ritobin_rust
cargo doc --open
```

## Project Structure

```
ritobin_rust/
├── src/
│   ├── lib.rs          - Library entry point
│   ├── model.rs        - Data structures (Bin, BinValue, BinType)
│   ├── binary.rs       - Binary format I/O
│   ├── text.rs         - Text format I/O (nom parser)
│   ├── json.rs         - JSON format I/O
│   ├── hash.rs         - FNV1a and XXH64 implementations
│   ├── unhash.rs       - Hash loading and unhashing
│   └── main.rs         - CLI application
└── examples/           - Usage examples
```

## Credits

Inspired by [moonshadow565/ritobin](https://github.com/moonshadow565/ritobin) - the original implementation that paved the way.

Made with ❤️ for the League of Legends community.

## License

See [LICENSE](LICENSE) file for details.
