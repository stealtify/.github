<div align="center">

# Stealtify

**Per-app proxy client for Android. A different proxy for every app. No root.**

[🌐 stealtify.app](https://stealtify.app) ·
[📥 Downloads](https://update.stealtify.app) ·
[📱 App](https://github.com/stealtify/stealtify) ·
[<img src="https://raw.githubusercontent.com/stealtify/.github/main/profile/assets/telegram.svg" width="14" alt=""> Telegram](https://t.me/stealtify) ·
[🇷🇺 Русский](./README.ru.md)

</div>

---

## What it is

Stealtify is an Android app that routes **each app's traffic through its own proxy**. Not "turn on the VPN and the whole phone goes through the tunnel" — a precise rule instead: YouTube through one server, your bank direct, a messenger through a third.

Runs on stock Android 10+ via the `VpnService` API — **no root required**.

## Features

| | |
|---|---|
| 🎯 **Per-app routing** | Different proxies for different apps; app groups |
| 🌐 **Domain rules** | By DNS responses and TLS SNI |
| 🔗 **8 protocols** | SOCKS5, HTTP CONNECT, SSH, VLESS, VMess, Trojan, Shadowsocks, AmneziaWG |
| 🚀 **Dual engine** | Kotlin TCP/UDP stack + Go engine based on xray-core |
| 🔒 **Kill switch** | Protection while the tunnel recovers |
| 🔐 **Encrypted DNS** | DoT/DoH with Cloudflare, Google, AdGuard, Quad9 presets |
| 🚫 **DNS filtering** | Built-in blocklist (off by default) |
| ♥️ **Failover** | Health checks and automatic proxy switching; proxy chains |
| 📥 **Import** | URI links, QR codes, subscriptions with auto-refresh |
| 📊 **Monitoring** | Real-time connection logs and traffic statistics |
| 📱 **Material You** | Jetpack Compose + Material 3 |
| 📺 **Android TV** | Separate remote-friendly build (beta) |

## How it works

```
App → VpnService TUN → TunPacketProcessor
    → getConnectionOwnerUid() → identify the source app
    → RouteResolver: app → domain → group → default proxy
    → traffic goes through the matching proxy (or direct)
```

The source app is identified via `ConnectivityManager.getConnectionOwnerUid()` (API 29+) — exactly, with no port-based heuristics.

## Privacy

No analytics SDK. No account. No telemetry.

The app only contacts the update server, external-IP lookup services, and **your** subscription and DNS servers. Details in the [Privacy Policy](https://github.com/stealtify/stealtify/blob/main/docs/legal/PRIVACY.md).

Every build is signed and verified at launch — tampered builds are rejected.

## Get started

| | |
|---|---|
| 📥 **Download** | [Releases](https://github.com/stealtify/stealtify/releases) · [update.stealtify.app](https://update.stealtify.app) |
| 📖 **Install** | [INSTALL.md](https://github.com/stealtify/stealtify/blob/main/docs/for_release/INSTALL.md) |
| 📚 **User guide** | [USER_GUIDE.md](https://github.com/stealtify/stealtify/blob/main/docs/for_release/USER_GUIDE.md) |
| 📺 **Android TV** | [TV_INSTALL.md](https://github.com/stealtify/stealtify/blob/main/docs/for_release/tv/TV_INSTALL.md) |
| 🗺️ **Roadmap** | [ROADMAP.md](https://github.com/stealtify/stealtify/blob/main/docs/for_release/ROADMAP.md) |

**Requirements:** Android 10+ (API 29), arm64-v8a (phone) · arm64-v8a / armeabi-v7a / x86 (TV).

## Feedback

- 💬 **News and discussion** — [t.me/stealtify](https://t.me/stealtify)
- 🐛 **Bug or idea** — [Issues](https://github.com/stealtify/stealtify/issues)
- 🔐 **Vulnerability** — privately via [Security Advisories](https://github.com/stealtify/stealtify/security/advisories/new), not a public issue

## License

Proprietary license (EULA), Copyright © 2025–2026 Stealtify. All rights reserved.
Third-party components (MPL-2.0 / Apache-2.0 / BSD / MIT) keep their own licenses — see [NOTICE](https://github.com/stealtify/stealtify/blob/main/NOTICE).

---

<div align="center">
Made with ❤️ for privacy and freedom
</div>
