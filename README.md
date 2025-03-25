# ruption_quantum_encrypt

A quantum-secure encryption crate with hybrid lattice/code-based cryptography and enhanced randomness.

[![Crates.io](https://img.shields.io/crates/v/ruption_quantum_encrypt.svg)](https://crates.io/crates/ruption_quantum_encrypt)
[![Docs](https://docs.rs/ruption_quantum_encrypt/badge.svg)](https://docs.rs/ruption_quantum_encrypt)

## Overview

`ruption_quantum_encrypt` provides a software-only approach to quantum-secure encryption, combining lattice-based and code-based cryptographic techniques. It includes a unique `TrueRandom` generator that approximates true entropy using system sources and a quantum-inspired simulation.

**Note**: This is a toy implementation for demonstration. For production use, replace the simplified algorithms with proper LWE and McEliece implementations.

## Features

- Hybrid cryptography for post-quantum security.
- Enhanced randomness with `TrueRandom`.
- Simple API for key generation, encapsulation, and key derivation.

## Installation

Add this to your `Cargo.toml`:
```toml
[dependencies]
ruption_quantum_encrypt = "0.1.0"

## Usage

Generate a keypair, encapsulate a shared secret, and derive keys:

use ruption_quantum_encrypt::{keypair, encapsulate, decapsulate, derive_keys};

let (pk, sk) = keypair();
let (ct, ss1) = encapsulate(&pk);
let ss2 = decapsulate(&ct, &sk);
assert_eq!(ss1.as_bytes(), ss2.as_bytes());

let keys = derive_keys(&ss1, 3);
assert_eq!(keys.len(), 3);
assert_eq!(keys[0].len(), 32);

## Documentation

Full API documentation is available on docs.rs.

## License

Licensed under MIT.