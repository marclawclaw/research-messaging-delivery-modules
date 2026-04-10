---
tags: [project, logos-messaging, e2e-reliability, nim, cross-platform]
updated: 2026-04-10
---

# nim-sds

**Organisation:** logos-messaging
**Type:** End-to-end reliability protocol library
**GitHub:** https://github.com/logos-messaging/nim-sds
**Stars:** 3
**Last updated:** 2026-04-02

## Overview

Nim implementation of the e2e reliability protocol (SDS — Store, Deliver, Subscribe). Provides message delivery guarantees that Waku v2 transport does not natively provide.

## Supported Platforms

| Platform | Architecture | Build command |
|----------|-------------|--------------|
| Desktop | macOS, Linux, Windows | `nix build '.#libsds'` |
| Android | arm64, amd64, x86, arm | `nix build '.#libsds-android-*'` |
| iOS | arm64 (iOS) | `nix build '.#libsds-ios'` |

Cross-platform mobile support is a notable strength.

## Relationship to Other Components

- Used by [[logos-chat]] for message delivery guarantees
- Depends on [[logos-delivery]] for transport

## Readiness

**Status:** Active
**Cross-platform:** Android + iOS confirmed

## Sources

- README: https://github.com/logos-messaging/nim-sds
- Nix-only build system
