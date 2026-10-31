# reSpotIt

## About

reSpotIt was built to fill gaps in Spotify's library management. It is an album-centric tool that lets you organize your library and playlists using rich filters, add entire artist discographies to your library or turn them into playlists, import album links from any website, and build queues from albums you are listening to right now. This is a work in progress — expect rough edges and things that may not work yet.

A multi-platform Spotify library dashboard.

reSpotIt lets you browse, filter, sort, and manage your saved Spotify album library across multiple clients. It supports local and remote (media-server) modes, playlist management, duplicate detection, queue control, and CSV export/backup.

### reSpotIt Project Structure

reSpotIt is a multi-component project with several variants:

- **Local Server (standalone)** — Python/FastAPI backend + React web frontend + PostgreSQL. Runs entirely on your machine. No AI assistant. Full feature set: library management, playlists, sync, stats, CSV import/export.
- **Local Server + AI assistant** — Same server plus OpenWebUI, Keycloak, and MCP services for AI-powered library queries. Available as a full stack overlay or self-contained one-click stack.
- **Kotlin client** — Native Android app (Kotlin + Jetpack Compose). Full feature parity with media-server mode. Best performance on modern Android devices.
- **React clients** — Capacitor/TypeScript Android apps. Offer better compatibility on older Android models and low-RAM devices than the Kotlin client.
  - **Standard** — Web Playback SDK for browser-based playback.
  - **Librespot** — Experimental on-device full-track playback via Rust/JNI. Only this variant supports on-device audio.

> **Standalone mode:** All Android clients work fully offline without any server. All library data is stored on-device. Media-server mode is optional — enable it in Settings to sync, push/pull, and use the AI assistant.

## Repositories

| Repository | Description | Release |
|---|---|---|
| [reSpotIt-react-version](https://github.com/damianoshar/reSpotIt-react-version-stage) | React/TypeScript Android app (Capacitor) | [v0.1.1](https://github.com/damianoshar/reSpotIt-react-version-stage/releases/tag/v0.1.1) |
| [reSpotIt-react-librespot-version](https://github.com/damianoshar/reSpotIt-react-version-stage) (branch `feat/librespot-player`) | React variant with on-device librespot player | [v0.1.0-librespot](https://github.com/damianoshar/reSpotIt-react-version-stage/releases/tag/v0.1.0-librespot) |
| [reSpotIt-kotlin-version](https://github.com/damianoshar/reSpotIt-kotlin-version-stage) | Native Kotlin/Compose Android app | [0.1.1](https://github.com/damianoshar/reSpotIt-kotlin-version-stage/releases/tag/v0.1.1) |
| [reSpotIt-local-server-app](https://github.com/damianoshar/reSpotIt-local-server-app-stage) | Python FastAPI backend + web frontend + desktop app (solo + full stack overlay) | [v0.1.0](https://github.com/damianoshar/reSpotIt-local-server-app-stage/releases/tag/v0.1.0) |

## Features

- Browse saved albums with rich filters (genre, artist, year, decade, popularity)
- Multiple view modes (grid, list, compact)
- Playlist management (create, add albums, remove, hide)
- Duplicate detection and removal (permanent delete from Spotify)
- Queue control (Spotify queue + local librespot queue)
- Sync library from Spotify
- Export/backup to CSV
- Device transfer (play on any Spotify Connect device)
- On-device librespot player (experimental)
- Offline support (on-device SQLite)

## Installation

### Android (React)
1. Download the APK from the [react releases](https://github.com/damianoshar/reSpotIt-react-version-stage/releases).
2. Install on your Android device (enable "Install unknown apps" if needed).
3. Open the app and sign in with your Spotify account.

### Android (Kotlin)
1. Download the APK from the [kotlin releases](https://github.com/damianoshar/reSpotIt-kotlin-version-stage/releases).
2. Install on your Android device.
3. Open the app and sign in with your Spotify account.

### Desktop / Server
1. Download from the [local server releases](https://github.com/damianoshar/reSpotIt-local-server-app-stage/releases).
2. Run via Docker or the Windows executable.
3. Configure Spotify credentials in `.env`.

## License

MIT - see [LICENSE](LICENSE).

## Player limitations

- React/TS and Kotlin clients control playback via Spotify Connect (audio plays on a target device, not in-app).
- Web Playback SDK (browser) requires Spotify Premium + streaming scope; no buffer settings.
- On-device librespot player is experimental (separate branch, not merged).