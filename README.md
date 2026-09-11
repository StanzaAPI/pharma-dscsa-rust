# FDA DSCSA & EU FMD Drug Serialization API — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-pharma-dscsa.svg)](https://crates.io/crates/stanzaapi-pharma-dscsa)
[![Documentation](https://docs.rs/stanzaapi-pharma-dscsa/badge.svg)](https://docs.rs/stanzaapi-pharma-dscsa)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> US FDA DSCSA 4-element & EU FMD 2D DataMatrix barcode parser, Modulo-10 check digit validator, and NDC-to-GTIN converter in sub-5ms.

Official high-performance, asynchronous Rust client library for **FDA DSCSA & EU FMD Drug Serialization API**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/pharma-dscsa)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/pharma-dscsa)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-pharma-dscsa = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-pharma-dscsa
```

---

## 🚀 Quickstart

```rust
use stanzaapi_pharma_dscsa::PharmaDscsaClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    // Public edge default: https://api.stanzaapi.com/pharma-dscsa
    let client = PharmaDscsaClient::new(None, None);

    let response = client.validate("(01)00300012345678(21)100000000001(17)261231(10)LOT12345").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "gtin": "00300012345678",
    "serial_number": "100000000001",
    "expiration_date": "2026-12-31",
    "lot_number": "LOT12345"
  }
}
```

---

## 🔗 Useful Links

* [FDA DSCSA & EU FMD Drug Serialization API Interactive Sandbox](https://stanzaapi.com/tools/pharma-dscsa)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/pharma-dscsa-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
