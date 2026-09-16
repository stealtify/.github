<div align="center">

# Stealtify

**Per-app прокси-клиент для Android. Каждому приложению — свой прокси. Без root.**

[🌐 stealtify.app](https://stealtify.app) ·
[📥 Загрузки](https://update.stealtify.app) ·
[📱 Приложение](https://github.com/stealtify/stealtify) ·
[<img src="https://raw.githubusercontent.com/stealtify/.github/main/profile/assets/telegram.svg" width="14" alt=""> Telegram](https://t.me/stealtify) ·
[🇬🇧 English](./README.md)

</div>

---

## Что это

Stealtify — Android-приложение, которое маршрутизирует трафик **каждого приложения через свой прокси**. Не «включил VPN — весь телефон ушёл в туннель», а точное правило: YouTube через один сервер, банк напрямую, мессенджер через третий.

Работает на стоковом Android 10+ через `VpnService` API — **root не нужен**.

## Возможности

| | |
|---|---|
| 🎯 **Per-app маршрутизация** | Разные прокси для разных приложений; группы приложений |
| 🌐 **Доменные правила** | По ответам DNS и по TLS SNI |
| 🔗 **8 протоколов** | SOCKS5, HTTP CONNECT, SSH, VLESS, VMess, Trojan, Shadowsocks, AmneziaWG |
| 🚀 **Двойной движок** | Kotlin TCP/UDP-стек + Go-движок на базе xray-core |
| 🔒 **Kill Switch** | Защита на время восстановления туннеля |
| 🔐 **Шифрованный DNS** | DoT/DoH с пресетами Cloudflare, Google, AdGuard, Quad9 |
| 🚫 **DNS-фильтрация** | Встроенный список блокируемых доменов (по умолчанию выключена) |
| ♥️ **Failover** | Health-check и автопереключение прокси; цепочки прокси |
| 📥 **Импорт** | URI-ссылки, QR-коды, подписки с автообновлением |
| 📊 **Мониторинг** | Логи подключений и статистика трафика в реальном времени |
| 📱 **Material You** | Jetpack Compose + Material 3 |
| 📺 **Android TV** | Отдельная сборка под пульт (beta) |

## Как это работает

```
Приложение → VpnService TUN → TunPacketProcessor
    → getConnectionOwnerUid() → определяем приложение-источник
    → RouteResolver: app → domain → группа → прокси по умолчанию
    → трафик уходит через нужный прокси (или напрямую)
```

Приложение-источник определяется через `ConnectivityManager.getConnectionOwnerUid()` (API 29+) — точно, без эвристик по портам.

## Приватность

Нет SDK аналитики. Нет учётной записи. Нет телеметрии.

Приложение обращается только к серверу обновлений, сервисам определения внешнего IP и к **вашим** серверам подписок и DNS. Подробности — в [Политике конфиденциальности](https://github.com/stealtify/stealtify/blob/main/docs/PRIVACY.md).

Каждая сборка подписана и проверяется при запуске — поддельные сборки отвергаются.

## Начать

| | |
|---|---|
| 📥 **Скачать** | [Releases](https://github.com/stealtify/stealtify/releases) · [update.stealtify.app](https://update.stealtify.app) |
| 📖 **Установка** | [INSTALL.ru.md](https://github.com/stealtify/stealtify/blob/main/docs/INSTALL.ru.md) |
| 📚 **Руководство** | [USER_GUIDE.ru.md](https://github.com/stealtify/stealtify/blob/main/docs/USER_GUIDE.ru.md) |
| 📺 **Android TV** | [TV_INSTALL.ru.md](https://github.com/stealtify/stealtify/blob/main/docs/tv/TV_INSTALL.ru.md) |
| 🗺️ **Roadmap** | [ROADMAP.md](https://github.com/stealtify/stealtify/blob/main/docs/ROADMAP.md) |

**Требования:** Android 10+ (API 29), arm64-v8a (телефон) · arm64-v8a / armeabi-v7a / x86 (TV).

## Обратная связь

- 💬 **Новости и обсуждение** — [t.me/stealtify](https://t.me/stealtify)
- 🐛 **Баг или идея** — [Issues](https://github.com/stealtify/stealtify/issues)
- 🔐 **Уязвимость** — приватно через [Security Advisories](https://github.com/stealtify/stealtify/security/advisories/new), не через публичный issue

## Лицензия

Проприетарная лицензия (EULA), Copyright © 2025–2026 Stealtify. Все права защищены.
Сторонние компоненты (MPL-2.0 / Apache-2.0 / BSD / MIT) сохраняют свои лицензии — см. [NOTICE](https://github.com/stealtify/stealtify/blob/main/NOTICE).

---

<div align="center">
Made with ❤️ for privacy and freedom
</div>
