---
tags: [project, logos-co, module, qt, delivery, blocked]
updated: 2026-04-10
---

# logos-delivery-module

**Organisation:** logos-co
**Type:** Logos Core Qt plugin (module)
**GitHub:** https://github.com/logos-co/logos-delivery-module
**Last updated:** 2026-03-19

## Overview

Wraps `liblogosdelivery` from [[logos-delivery]] as a Logos Core Qt plugin module. Provides high-level message delivery capabilities to any Logos Core application.

## API Surface

Provides these synchronous Qt plugin methods:
- `createNode(cfg)` — initialise delivery node with JSON config (WakuNodeConf format)
- `start()` / `stop()` — lifecycle
- `send(contentTopic, payload)` — async send, returns request ID
- `subscribe(contentTopic)` / `unsubscribe(contentTopic)` — topic subscription
- `getAvailableNodeInfoIDs()` / `getNodeInfo(id)` — node info queries
- `getAvailableConfigs()` — config parameter descriptions

Events emitted:
- `messageReceived` — message arrived on subscribed topic
- `messageSent` — confirmed by network
- `messagePropagated` — reached network, not yet validated
- `messageError` — send failure
- `connectionStateChanged` — connectivity change

## Configuration Presets

| Preset | Description |
|--------|-------------|
| `twn` | RLN-protected Waku Network (cluster 1) |
| `logos.dev` | Logos Dev Network (cluster 2, mix enabled, p2pReliability on, 8 auto-shards) |

## Blocking Issue

**C FFI library not published:** The module compiles successfully but fails at the install phase because `liblogosdelivery.dylib` / `.so` is not yet exported from [[logos-delivery]].

Fix required: Add C library export target to [[logos-delivery]] build system.

## Nix vs CMake

- Default build: Nix only
- `nix build '.#lib'` — plugin library only (still requires liblogosdelivery at runtime)
- CMake build documented but requires environment variables pointing to SDKs

## Readiness

**Status:** ⚠️ Blocked
**Path to unblocked:** Publish `liblogosdelivery` from [[logos-delivery]]

## Sources

- README: https://github.com/logos-co/logos-delivery-module
