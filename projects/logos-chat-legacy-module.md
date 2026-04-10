---
tags: [project, logos-co, module, qt, chat, legacy, proof-of-concept]
updated: 2026-04-10
---

# logos-chat-legacy-module

**Organisation:** logos-co
**Type:** Logos Core Qt plugin (chat module)
**GitHub:** https://github.com/logos-co/logos-chat-legacy-module
**Last updated:** 2026-03-17

## Overview

Simple chat module proof-of-concept. Nix-buildable Qt plugin. Deprecated in favour of the [[logos-chat]] / [[logos-chat-ui]] stack.

## Build

- `nix build '.#default'` — full build
- `nix build '.#lib'` — plugin library only
- `nix build '.#logos-chat-module-include'` — generated headers only

## Dependencies

- logos-liblogos
- logos-cpp-sdk (for header generation)
- zstd, krb5, protobuf, abseil-cpp
- Qt6 + Qt6 RemoteObjects

## Status

Superseded by [[logos-chat-ui]] / [[logos-chat]] stack. Maintained for backwards compatibility reference.

## Readiness

**Status:** Legacy / PoC
