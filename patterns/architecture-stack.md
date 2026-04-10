---
tags: [pattern, architecture, stack, dependencies]
updated: 2026-04-10
---

# Logos Messaging Architecture Stack

## Layer Map

```
┌─────────────────────────────────────────────────────────┐
│  Application Layer                                       │
│  logos-chat-ui (Qt app)                                  │
│  logos-chat-legacy-ui (legacy Qt app)                    │
└─────────────────────┬───────────────────────────────────┘
                      │ Qt Plugin interface
┌─────────────────────▼───────────────────────────────────┐
│  Module Layer (Logos Core plugins)                       │
│  logos-chat-module      ← NOT PUBLICLY LISTED            │
│  logos-delivery-module  ← blocked on liblogosdelivery    │
│  logos-libp2p-module                                    │
│  logos-chat-legacy-module (legacy)                       │
└─────────────────────┬───────────────────────────────────┘
                      │ C FFI
┌─────────────────────▼───────────────────────────────────┐
│  SDK / Library Layer                                     │
│  logos-chat (Nim) — liblogoschat.{dylib,so}              │
│  logos-cpp-sdk                                          │
│  logos-liblogos                                         │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│  Application Logic Layer                                 │
│  nim-sds (e2e reliability)                              │
│  libchat (crypto)                                        │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│  Transport Layer                                         │
│  logos-delivery (Nim) — Waku v2 core                    │
│  logos-delivery-js (JS)                                 │
│  logos-delivery-go (Go)                                 │
└─────────────────────┬───────────────────────────────────┘
                      │ libp2p
┌─────────────────────▼───────────────────────────────────┐
│  Network Layer                                           │
│  nim-libp2p (C bindings)                                │
│  go-libp2p                                              │
└─────────────────────────────────────────────────────────┘
```

## Dependency: logos-chat-ui

```
logos-chat-ui
    └── logos-chat-module        ⚠️ MISSING / PRIVATE
            └── logos-chat
                    ├── nim-sds
                    ├── libchat
                    └── logos-delivery
    └── logos-capability-module
    └── logos-liblogos
```

## Dependency: logos-delivery-module

```
logos-delivery-module
    └── logos-delivery
            └── (nim runtime)
    └── logos-liblogos
```

## Build System Convention

All repos use **Nix** as the canonical build system. CMake is secondary and often incomplete without Nix environment variables.

Typical build:
```bash
nix build              # default target
nix build '.#lib'      # library only
nix develop            # dev shell
```
