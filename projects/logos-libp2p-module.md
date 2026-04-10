---
tags: [project, logos-co, module, qt, libp2p, p2p]
updated: 2026-04-10
---

# logos-libp2p-module

**Organisation:** logos-co
**Type:** Logos Core Qt plugin (networking module)
**GitHub:** https://github.com/logos-co/logos-libp2p-module
**Last updated:** 2026-03-25

## Overview

Integrates libp2p networking (via nim-libp2p C bindings) into the Logos ecosystem as a Logos Core Qt plugin module.

## Capabilities

- Peer connectivity
- Stream management
- Kademlia DHT operations
- Mix operations
- Gossipsub operations
- Sync and async APIs compatible with Qt

## Dependencies

- nim-libp2p C bindings (from vacp2p/nim-libp2p)
- Logos SDK
- Qt6
- CMake + Ninja + pkg-config

## Relationship to [[logos-delivery]]

[[logos-delivery]] builds on top of libp2p for Waku v2 protocols. This module exposes raw libp2p capabilities one layer below.

## Readiness

**Status:** Active development
**Integration:** Works with Logos Core module system

## Sources

- README: https://github.com/logos-co/logos-libp2p-module
- Examples: `examples/` directory
