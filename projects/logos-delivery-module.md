---
tags: [project, logos-co, module, qt, delivery, ready]
updated: 2026-04-10
---

# logos-delivery-module

**Organisation:** logos-co
**Type:** Logos Core Qt plugin (module)
**GitHub:** https://github.com/logos-co/logos-delivery-module
**Last updated:** 2026-04-10

## Overview

Wraps `liblogosdelivery` from [[logos-delivery]] as a Logos Core Qt plugin module. Provides high-level message delivery capabilities to any Logos Core application.

**Status (2026-04-10): Confirmed ready to use by dev team.**

> Note: The README contains an outdated warning about `liblogosdelivery.dylib` not being available. This is stale — the C FFI is available via `nix build github:logos-messaging/logos-delivery`.

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

## Building

```bash
# Build with Nix (recommended)
nix build

# Build plugin only (requires liblogosdelivery at runtime)
nix build '.#lib'
```

Both libraries (`delivery_module_plugin` + `liblogosdelivery`) must remain in the same directory.

## Readiness

**Status:** Ready to use (2026-04-10 confirmation from dev team)
**Pre-requisite:** `liblogosdelivery` available via `nix build github:logos-messaging/logos-delivery`

## Sources

- README: https://github.com/logos-co/logos-delivery-module
