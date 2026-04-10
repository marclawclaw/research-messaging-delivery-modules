---
tags: [project, logos-messaging, chat-sdk, preview]
updated: 2026-04-10
---

# logos-chat

**Organisation:** logos-messaging
**Type:** Application-layer chat SDK
**GitHub:** https://github.com/logos-messaging/logos-chat
**Stars:** 3
**Last updated:** 2026-03-02
**Project status:** Preview (badge on README)

## Overview

Privacy-focused decentralised messaging SDK built on the Logos Stack. Provides permission-less, censorship-resistant 1:1 messaging.

## Key Capabilities

- Private 1:1 conversations initiated via intro bundles (out-of-band key exchange)
- End-to-end encrypted messaging
- C bindings (`liblogoschat.{dylib,so,dll}`)
- Nim API + C FFI
- Requires Nim >= 2.2.4 and Rust toolchain

## Message Flow

```
Recipient generates intro bundle (out-of-band, no secrets)
        ↓
Sender retrieves bundle, sends Invite + initial message
        ↓
Both parties: encrypted 1:1 messaging loop
```

## Relationship to Other Modules

```
logos-chat
    ├── nim-sds (e2e reliability)
    ├── libchat (crypto layer)
    └── logos-delivery (transport)

Used by:
    └── logos-chat-module (logos-co, not publicly listed)
            └── logos-chat-ui (logos-co)
```

Note: `logos-chat-module` does not appear in the logos-co org listing. May be private or unlisted.

## Limitations

- Preview status — not production-ready
- No message persistence (ephemeral only, per [[logos-chat-ui]])
- No group chats (1:1 only)
- No file/image attachment support mentioned

## Readiness

**Status:** Preview
**Ready for integration:** Yes (C bindings available)
**Production-ready:** No (Preview badge)

## Sources

- README: https://github.com/logos-messaging/logos-chat
- C bindings: `library/liblogoschat.h`
