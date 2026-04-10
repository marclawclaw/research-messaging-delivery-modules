---
tags: [metrics, readiness, comparison]
updated: 2026-04-10
---

# Messaging Module Readiness Comparison

## By Layer

| Layer | Repo | Status | Stars | Updated | Blocking Issues |
|-------|------|--------|-------|---------|-----------------|
| **Transport** | [[logos-delivery]] | Production | 240 | 2026-04-09 | None for transport itself |
| **Transport** | [[logos-delivery-js]] | Active | 196 | 2026-04-07 | None |
| **Transport** | [[logos-delivery-go]] | Active | 133 | 2026-03-18 | None |
| **E2E Reliability** | [[nim-sds]] | Active | 3 | 2026-04-02 | None |
| **Crypto Layer** | libchat | Active | 0 | 2026-04-10 | None |
| **Chat SDK** | [[logos-chat]] | Preview | 3 | 2026-03-02 | Preview status; ephemeral only |
| **Delivery Module** | [[logos-delivery-module]] | ⚠️ Blocked | — | 2026-03-19 | Waiting on C FFI from [[logos-delivery]] |
| **Chat Module** | [[logos-chat-legacy-module]] | Legacy | — | 2026-03-17 | Deprecated |
| **Chat UI** | [[logos-chat-ui]] | Active | — | 2026-03-20 | `logos-chat-module` not publicly listed; no persistence |
| **libp2p Module** | [[logos-libp2p-module]] | Active | — | 2026-03-25 | None |

## Readiness Matrix

| Feature | Transport | Delivery Module | Chat SDK | Chat UI |
|---------|-----------|----------------|----------|---------|
| Waku v2 relay | ✅ | ✅ (blocked on C FFI) | ✅ | ✅ |
| RLN rate limiting | ✅ | ✅ | — | — |
| E2E encryption | — | — | ✅ | ✅ |
| 1:1 messaging | — | — | ✅ | ✅ |
| Ephemeral messages | — | — | ✅ | ✅ |
| Message persistence | — | — | ❌ | ❌ |
| Qt plugin | — | ✅ | — | ✅ |
| Mobile (Android/iOS) | — | — | Partial (nim-sds) | ❌ |
| Nix build | ✅ | ✅ | ✅ | ✅ |
| CMake build (no Nix) | Partial | Partial | Partial | ✅ |
| Production-ready | ✅ | ⚠️ (blocked) | ❌ (Preview) | ⚠️ |

## Critical Path to Working Delivery Module

```
1. [logos-delivery] — add C FFI export target (make lib / nix build '.#liblogosdelivery')
2. [logos-delivery] — publish liblogosdelivery.dylib/.so
3. [logos-delivery-module] — nix build '.#default' succeeds
4. Integration with Logos Core
```

## Critical Path to Working Chat UI

```
1. [logos-chat-module] — make public or confirm location
2. [logos-delivery] C FFI published (for [[logos-chat]] via [[nim-sds]])
3. Message persistence — store protocol implementation (not started)
4. [[logos-chat]] → Preview badge removed
```
