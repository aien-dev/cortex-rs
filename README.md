<p align="center">
  <img src="assets/avatar.jpg" width="140" height="140" alt="AIEN Sovereign Intelligence" style="border-radius: 50%; border: 2px solid #f59e0b;">
</p>

# cortex-rs

[![CI](https://github.com/aien-dev/cortex-rs/actions/workflows/ci.yml/badge.svg)](https://github.com/aien-dev/cortex-rs/actions/workflows/ci.yml)
[![License: SRCL-1.0](https://img.shields.io/badge/License-SRCL--1.0-blue.svg)](LICENSE)
[![Security](https://img.shields.io/badge/tpm--vault-zero--disk--secrets-green.svg)](SECURITY.md)
[![Standard](https://img.shields.io/badge/standard-unslop-black.svg)](CONTRIBUTING.md)
[![Mission](https://img.shields.io/badge/mission-sovereign--defense-amber.svg)](https://drakestapleton.com)

High-performance native Rust memory engine with SQLite FTS5 lexical recall, bi-encoder vector similarity, and hardware-secured loopback isolation.

## Overview

`cortex-rs` is the canonical memory engine powering Atlas and the AIEN sovereign agent stack. Written entirely in native Rust (Axum), it replaces heavy interpreted memory servers with sub-millisecond lexical and semantic retrieval.

It provides hybrid search combining BM25 full-text indexing with ONNX vector embeddings, enabling autonomous agents to recall procedures, lessons, and architectural discoveries across thousands of turns without context collapse.

## Features

- **Sub-Millisecond Retrieval**: Pure compiled Rust using SQLite WAL mode and FTS5 inverted indexes with typical latency <1ms.
- **Hybrid Semantic Recall**: Direct integration with local bi-encoder vector servers for cosine similarity and dense embedding scoring.
- **Hardware Vault Security**: Zero plaintext secrets. All authentication uses bearer token validation bound to loopback interfaces (`127.0.0.1`).
- **Graph & Provenance Traversal**: Bidirectional relationship edges (`cortex_claims`, `cortex_entities`) for deep contextual graph traversal.
- **Unslop Standard**: Enforces clean technical facts without AI filler or hallucinated abstractions.

## Quick Start

### Build & Run

```bash
# Compile release binary
cargo build --release

# Run Cortex-RS on local loopback
./target/release/cortex-rs --port 18080 --db-path ~/.config/cortex/cortex.db
```

### Health Check

```bash
curl http://127.0.0.1:18080/health
# {"runtime":"native-arm64-rust","service":"cortex-rs","space":"atlas-memory","status":"ok","version":"0.1.0"}
```

### Hybrid Query

```bash
curl -G http://127.0.0.1:18080/api/cortex/search \
  --data-urlencode "q=tpm vault" \
  -H "Authorization: Bearer <TOKEN>"
```

## License and Governance

Licensed under the **Sovereign Resource Commons License 1.0 (SRCL-1.0)** (Apache-2.0 WITH LLVM-exception).
Architected by AIEN (Autonomous Cognitive Architecture operating on the Atlas Framework) and sovereign ecosystem contributors. See [LICENSE](LICENSE) for full legal terms and copyright notices.

All downstream distributions, derivative works, and commercial deployments are governed exclusively by the terms of [LICENSE](LICENSE). [CONSTITUTION.md](CONSTITUTION.md) defines the internal architectural charter and development doctrine for upstream engineering.
