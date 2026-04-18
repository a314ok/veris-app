<h1 align="center">Veris</h1>

<p align="center">
  <strong>Streaming dashboard for Twitch, YouTube &amp; TikTok streamers</strong><br/>
  Visual automation · Live alerts · Stream overlays · Multi-platform
</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS-informational?style=flat-square" />
  <img src="https://img.shields.io/badge/version-0.2.16-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/built%20with-Go%20%2B%20Vue%203%20%2B%20Tauri-purple?style=flat-square" />
  <img src="https://img.shields.io/badge/license-private-lightgrey?style=flat-square" />
</p>

---

## What is Veris?

Veris is a desktop streaming companion — a self-hosted, open-architecture alternative to StreamElements and Streamlabs. Built for streamers who want full control over their alerts, commands, and automation without being locked into third-party clouds.

- **Visual Blueprint Engine** — drag-and-drop node graph to automate anything: alerts, commands, overlays, timers, API calls, variables, conditionals, loops
- **Multi-platform events** — Twitch, YouTube, TikTok subscriptions and chat events in real time
- **Donation integrations** — Donatello and Monobank webhooks out of the box
- **Live overlay editor** — drag-and-drop widgets directly on your stream canvas
- **Self-hosted** — your data stays on your server; no vendor lock-in

---

## Download

| Platform | Installer |
|----------|-----------|
| **Windows** | [Veris_0.2.15_x64-setup.exe](https://github.com/a314ok/veris-app/releases/latest) |
| **macOS (Apple Silicon)** | [Veris_0.2.15_aarch64.dmg](https://github.com/a314ok/veris-app/releases/latest) |
| **macOS (Intel)** | [Veris_0.2.15_x64.dmg](https://github.com/a314ok/veris-app/releases/latest) |

> The app auto-updates — once installed, Veris will notify you when a new version is available.

---

## Features

### Blueprint Engine

Build automation flows visually — no code required. Connect triggers to conditions to actions using a node graph editor. Supports 40+ built-in nodes:

| Category | Nodes |
|----------|-------|
| **Triggers** | Chat command, donation, follow, subscription, resub, timer, schedule |
| **Conditions** | If/else, cooldown, role check, compare, switch, array match |
| **Actions** | Send chat message, HTTP request, show alert, play sound, OBS scene switch |
| **Data** | Variables, arrays, templates, math, JS expressions, transformations |

### Platforms & Integrations

- **Twitch** — chat events, channel points, subscriptions, raids, follows
- **YouTube** — chat messages, memberships, superchats
- **TikTok** — live chat events
- **Donatello** — donation alerts with custom messages
- **Monobank** — bank donation events
- **Discord** & **Telegram** — webhook notifications

### Alerts & Overlays

- Fully customizable alert panels with animations
- Drag-and-drop overlay editor — position widgets anywhere on screen
- Browser source compatible — works with OBS, Streamlabs OBS, and XSplit

### Commands

- `!command` with cooldowns, mod-only restrictions, variables, and Blueprint execution
- Role-aware: streamer, lead moderator, moderator, subscriber, VIP

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop shell | Tauri 2 (Rust) |
| Frontend | Vue 3 + TypeScript + Vite |
| UI | Tailwind CSS |
| Blueprint canvas | VueFlow |
| Code execution | Deno (sidecar) |
| Backend | Go 1.22 |
| Database | PostgreSQL 16 |
| CI/CD | GitHub Actions → GHCR → Docker |

---

## Architecture

```
┌─────────────────────────────────────────┐
│           Tauri Desktop Client          │
│  Vue 3 UI  │  Blueprint Runtime (TS)    │
│            │  Deno sidecar (CODE nodes) │
└────────────┬────────────────────────────┘
             │ HTTPS / WSS
┌────────────▼────────────────────────────┐
│            Go Backend (VPS)             │
│  REST API  │  SSE events  │  Webhooks   │
│            PostgreSQL 16                │
└─────────────────────────────────────────┘
```

Blueprint graphs execute **entirely on the client** — the backend never runs user scripts.

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for full version history.

---

## License

Private repository — all rights reserved.
