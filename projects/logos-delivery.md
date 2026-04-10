---
tags: [project, logos-messaging, transport, waku-v2, nim]
updated: 2026-04-10
---

# logos-delivery

**Organisation:** logos-messaging
**Type:** Core transport layer
**GitHub:** https://github.com/logos-messaging/logos-delivery
**Stars:** 240
**Last updated:** 2026-04-10

## Overview

Nim implementation of Waku v2 protocols. The production-grade core transport for the entire Logos messaging stack. Implements the full [Waku v2 spec](https://github.com/vacp2p/rfc-index/tree/main/waku), exposes a C library, and ships a CLI (`wakunode2`).

## Key Capabilities

- Full Waku v2 protocol implementation (relay, store, filter, light push, discv5)
- RLN (Rate Limiting Nullifier) support for spam protection
- DNS discovery and DNS bootstrap
- C FFI library export (`liblogosdelivery`)
- Multi-platform: Linux, macOS, Windows (MSYS2)
- Rust toolchain required for building

## Architecture

```
logos-delivery (Nim)
    └── wakunode2 (CLI)
    └── liblogosdelivery (C library)  ← used by logos-delivery-module
```

## C FFI Library

**Available.** The flake exposes `liblogosdelivery` as a package output:

```bash
# Build the C library
nix build github:logos-messaging/logos-delivery

# Or explicitly
nix build github:logos-messaging/logos-delivery/.#liblogosdelivery

# Available on: x86_64-linux, aarch64-linux, x86_64-darwin, aarch64-darwin, x86_64-windows
```

The `logos-delivery` README does not document this target — the Nix flake (`flake.nix`) is the authoritative source.

Recent commits (2026-04-10):
- "Fix BearSSL and NAT lib build reproducibility" — 2026-04-10
- "fix: recv_service delivers store-recovered messages" — 2026-04-09
- "add main loop lag monitor" — 2026-04-09

## Readiness

**Status:** Production-grade
**C FFI available:** Yes (via Nix)
**Blocking issues:** None — confirmed ready by dev team (2026-04-10)

## Sources

- README: https://github.com/logos-messaging/logos-delivery
- Flake: https://github.com/logos-messaging/logos-delivery/blob/master/flake.nix
- CI: GitHub Actions (https://github.com/logos-messaging/logos-delivery/actions)
- Waku docs: https://docs.waku.org/
