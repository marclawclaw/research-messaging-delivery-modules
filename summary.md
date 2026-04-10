---
tags: [summary, messaging, delivery, readiness]
updated: 2026-04-10
---

# Summary: Logos Messaging / Delivery Module Readiness

## Researched Repos

**logos-co org:**
- [[logos-delivery-module]] — Qt delivery module plugin
- [[logos-chat-legacy-module]] — legacy chat PoC module
- [[logos-chat-ui]] — Qt chat UI application
- [[logos-libp2p-module]] — libp2p networking module

**logos-messaging org:**
- [[logos-delivery]] — Waku v2 Nim core (most critical, 240 stars, active)
- [[logos-delivery-js]] — JS/Waku v2 (196 stars, active)
- [[logos-delivery-go]] — Go/Waku v2 (133 stars, active)
- [[logos-chat]] — Chat SDK (Preview status)
- [[nim-sds]] — E2E reliability (Android + iOS builds)
- libchat — Crypto layer (recently active)

## Key Findings (Updated 2026-04-10)

### Transport Layer: Production-Ready ✅
The Waku v2 core (`logos-delivery`, `logos-delivery-js`, `logos-delivery-go`) is solid, actively maintained, and production-grade. 240 stars on the Nim implementation. Updated today.

### Delivery Module: Ready to Use ✅
**Updated:** The C FFI (`liblogosdelivery`) IS available via `nix build github:logos-messaging/logos-delivery`. The `logos-delivery-module` README contains a stale warning — this has been resolved. Confirmed by dev team 2026-04-10.

### Chat SDK: Preview Status ⚠️
[[logos-chat]] has a "Preview" project status badge. Not production-ready. Ephemeral messaging only.

## Build Commands

```bash
# Transport layer C library
nix build github:logos-messaging/logos-delivery

# Delivery module plugin
cd $LOGO_REPOS/logos-delivery-module
nix build
```

## High-Priority Gaps

| Gap | Severity | Notes |
|-----|----------|-------|
| Message persistence (store protocol) | High | Not yet implemented in chat SDK |
| [[logos-chat]] project status: Preview → stable | Medium | Needed before production chat use |
| `logos-chat-module` public visibility | Medium | Required by [[logos-chat-ui]] |

## Bottom Line

**Yes, you can start building using the Logos messaging/delivery module today.** The `logos-delivery-module` is ready to use. Build `liblogosdelivery` via Nix, then `nix build` the delivery module. The transport layer is production-grade and actively maintained.

For the Qt plugin path: build the C FFI from `logos-delivery`, then build the delivery module plugin. The chat UI has additional gaps (message persistence, `logos-chat-module` visibility) that are separate concerns.

## Data Sources

All facts verified against live GitHub API, README content, and `flake.nix` fetched 2026-04-10.
