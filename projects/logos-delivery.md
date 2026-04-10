---
tags: [project, logos-messaging, transport, waku-v2, nim]
updated: 2026-04-10
---

# logos-delivery

**Organisation:** logos-messaging
**Type:** Core transport layer
**GitHub:** https://github.com/logos-messaging/logos-delivery
**Stars:** 240
**Last updated:** 2026-04-09

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

## C FFI Status

The C library export (`liblogosdelivery.dylib` / `.so`) is the blocking dependency for [[logos-delivery-module]].

Current status (per [[logos-delivery-module]] README): *"compiles but fails at install phase — liblogosdelivery.dylib not yet available from logos-delivery"*.

The `logos-delivery` README does not currently document a `make lib` or equivalent target for C library export. This step needs to be added to `logos-delivery`.

## Readiness

**Status:** Production-grade
**Blocking issues:** C library export not yet published

## Sources

- README: https://github.com/logos-messaging/logos-delivery
- CI: GitHub Actions (https://github.com/logos-messaging/logos-delivery/actions)
- Waku docs: https://docs.waku.org/
