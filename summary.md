---
tags: [summary, messaging, delivery, readiness]
updated: 2026-04-10
---

# Summary: Logos Messaging / Delivery Module Readiness

## Researched Repos

**logos-co org:**
- [[logos-delivery-module]] — Qt delivery module plugin (blocked)
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

## Key Findings

### Transport Layer: Production-Ready
The Waku v2 core (`logos-delivery`, `logos-delivery-js`, `logos-delivery-go`) is solid, actively maintained, and production-grade. 240 stars on the Nim implementation, updated 2026-04-09.

### Delivery Module: One Step from Unblocked
The [[logos-delivery-module]] compiles but fails to install because `liblogosdelivery` (the C FFI library) is not yet published. Fixing this in [[logos-delivery]] is the single highest-leverage action.

### Chat UI: Two Blocking Issues
1. `logos-chat-module` is not publicly listed in logos-co — required by [[logos-chat-ui]]
2. Message persistence not implemented — all messages are ephemeral

### Chat SDK: Preview Status
[[logos-chat]] has a "Preview" project status badge. Not production-ready. Ephemeral messaging only.

## High-Priority Gaps

| Gap | Severity | Owner |
|-----|----------|-------|
| C FFI export from [[logos-delivery]] | High | logos-messaging |
| `logos-chat-module` public visibility | High | logos-co |
| Message persistence (store protocol) | High | logos-messaging |
| [[logos-chat]] project status: Preview → stable | Medium | logos-messaging |

## Bottom Line

If the goal is to ship a working delivery module for the LEZ, the path is clear and blocked by a single missing build step: add a C library export target to [[logos-delivery]], publish `liblogosdelivery`, and the [[logos-delivery-module]] should build end-to-end. The chat UI has deeper structural gaps that need more time.

## Data Sources

All facts verified against live GitHub API and README content fetched 2026-04-10.
