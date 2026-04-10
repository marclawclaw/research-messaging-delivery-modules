---
tags: [project, logos-co, ui, qt, chat, proof-of-concept]
updated: 2026-04-10
---

# logos-chat-ui

**Organisation:** logos-co
**Type:** Qt UI application + module plugin
**GitHub:** https://github.com/logos-co/logos-chat-ui
**Last updated:** 2026-03-20

## Overview

Qt-based chat UI for the Logos Chat SDK. Dark terminal-inspired two-panel interface (conversation list + chat panel). Runs as a Qt plugin inside Logos Core.

## Core Functionality

- Identity — generates chat identity on startup, shows user ID in status bar
- Intro bundles — generate/share bundles to initiate conversations
- New conversations — paste intro bundle + initial message to open private chat
- Real-time messaging — send/receive over Logos network
- Chat lifecycle — init, start, stop via Chat menu (auto-starts on launch)

## Key Limitation

> "Conversations are ephemeral — messages and identity exist only while the app is running and are not persisted across restarts. Message storage (via the store protocol) is planned for a future release."

This is a significant gap for any production use case.

## Dependency Chain

```
logos-chat-ui
    └── logos-chat-module (NOT PUBLIC — missing dependency)
            └── logos-chat (logos-messaging)
                    ├── nim-sds
                    ├── libchat
                    └── logos-delivery
    └── logos-capability-module (auth)
    └── logos-liblogos (Logos Core)
```

The missing `logos-chat-module` is the critical blocker — it does not appear in the logos-co org listing.

## Build

- `nix run '.#app'` — standalone app (all dependencies via Nix)
- `nix build '.#lib'` — Qt plugin only

## Comparison with Legacy

| | logos-chat-ui (this) | [[logos-chat-legacy-ui]] |
|--|--|--|
| Backend | logos-chat-module | Different legacy backend |
| Status | Active | Legacy / superseded |
| Architecture | Qt plugin in Logos Core | Standalone Qt app |

## Readiness

**Status:** Active development
**Blocking issues:** 
1. `logos-chat-module` not publicly listed
2. No message persistence

## Sources

- README: https://github.com/logos-co/logos-chat-ui
- Spec: `docs/spec.md`
