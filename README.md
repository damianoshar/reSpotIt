# reSpotIt

## About

reSpotIt was built to fill gaps in Spotify's library management. It is an album-centric tool that lets you organize your library and playlists using rich filters, add entire artist discographies to your library or turn them into playlists, import album links from any website, and build queues from albums you are listening to right now. This is a work in progress — expect rough edges and things that may not work yet.

A multi-platform dashboard for your saved Spotify album library.

---

## 📥 Installation

| Variant | Platform | Download |
|---|---|---|
| [reSpotIt-react-version](https://github.com/damianoshar/reSpotIt-react-version) | Android — React / TypeScript + Capacitor | [latest release](https://github.com/damianoshar/reSpotIt-react-version/releases/latest) |
| [reSpotIt-react-version](https://github.com/damianoshar/reSpotIt-react-version) — branch `librespot-player` | Android — React + experimental on-device librespot player | [v0.1.3-librespot](https://github.com/damianoshar/reSpotIt-react-version/releases/tag/v0.1.3-librespot) |
| [reSpotIt-kotlin-version](https://github.com/damianoshar/reSpotIt-kotlin-version) | Android — Kotlin + Jetpack Compose | [latest release](https://github.com/damianoshar/reSpotIt-kotlin-version/releases/latest) |
| [reSpotIt-local-server-app-version](https://github.com/damianoshar/reSpotIt-local-server-app-version) | Desktop — self-hosted server + web UI | [latest release](https://github.com/damianoshar/reSpotIt-local-server-app-version/releases/latest) |

### Android

1. Download the APK for your variant from the releases page.
2. Install it on your Android device (enable "Install unknown apps" if needed).
3. Open the app and sign in with your Spotify account.

### Desktop / Server

1. Download the Windows bundle from the local-server releases, or clone the repository and run it with Docker.
2. Copy `.env.example` to `.env` and fill in your Spotify client id and secret.
3. Start the server, then point the Android app at it in Settings if you want media-server mode.

> Every client works fully offline on its own. The server is optional — it adds library sync, push/pull and the AI assistant.

---

## 🧱 Stack

- **Local server:** Python + FastAPI + PostgreSQL, React (Vite) web frontend, shipped as Docker Compose or a PyInstaller desktop app.
- **Full stack:** the same server plus OpenWebUI, Keycloak (OIDC) and MCP services for AI library queries.
- **Android (Kotlin):** Kotlin 1.9, Jetpack Compose (Material 3), Room/SQLite, Retrofit/OkHttp, AppAuth PKCE.
- **Android (React):** React 18 + TypeScript 5.4, Vite 5, Capacitor 6, `@capacitor-community/sqlite`.
- **On-device audio:** Rust librespot 0.8 core → Kotlin JNI bridge → `AudioTrack` (React variant, experimental).
- **API:** REST under `/api/v1`; the server contract is additive and frozen.

---

## reSpotIt Project Structure

- **Local Server (standalone)** — Python/FastAPI backend + React web frontend + PostgreSQL. Runs entirely on your machine. No AI assistant. Full feature set: library management, playlists, sync, stats, CSV import/export.
- **Local Server + AI assistant** — Same server plus OpenWebUI, Keycloak, and MCP services for AI-powered library queries. Available as a full stack overlay.
- **Kotlin client** — Native Android app (Kotlin + Jetpack Compose). Full feature parity with media-server mode. Best performance on modern Android devices.
- **React clients** — Capacitor/TypeScript Android apps. Offer better compatibility on older Android models and low-RAM devices than the Kotlin client.
  - **Standard** — Web Playback SDK for browser-based playback.
  - **Librespot** — Experimental on-device full-track playback via Rust/JNI. Only this variant supports on-device audio.

---

## 🎮 What the app does

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
- Phone-storage vault: your sign-in, settings and library survive a reinstall

> **Player limitations.** React and Kotlin control playback through Spotify Connect (audio plays on a target device, not in-app). The Web Playback SDK needs Spotify Premium plus the streaming scope and has no buffer settings. On-device librespot playback is experimental and ships with the React variant only.

---

## 📚 Documentation

Each client repository carries its own `docs/` folder.

| Repository | Documentation |
|---|---|
| `reSpotIt-react-version` | [FEATURES](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/FEATURES.md) · [ARCHITECTURE](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/ARCHITECTURE.md) · [BUILD](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/BUILD.md) · [TESTING](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/TESTING.md) · [SECURITY](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/SECURITY.md) · [TROUBLESHOOTING](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/TROUBLESHOOTING.md) · [SCREENS](https://github.com/damianoshar/reSpotIt-react-version/blob/main/docs/SCREENS.md) |
| `reSpotIt-kotlin-version` | [FEATURES](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/FEATURES.md) · [ARCHITECTURE](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/ARCHITECTURE.md) · [BUILD](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/BUILD.md) · [TESTING](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/TESTING.md) · [SECURITY](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/SECURITY.md) · [TROUBLESHOOTING](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/TROUBLESHOOTING.md) · [SCREENS](https://github.com/damianoshar/reSpotIt-kotlin-version/blob/main/docs/SCREENS.md) |
| `reSpotIt-local-server-app-version` | [DEPLOYMENT](https://github.com/damianoshar/reSpotIt-local-server-app-version/blob/main/docs/DEPLOYMENT.md) · [ARCHITECTURE](https://github.com/damianoshar/reSpotIt-local-server-app-version/blob/main/docs/ARCHITECTURE.md) · [TESTING](https://github.com/damianoshar/reSpotIt-local-server-app-version/blob/main/docs/TESTING.md) · [TROUBLESHOOTING](https://github.com/damianoshar/reSpotIt-local-server-app-version/blob/main/docs/TROUBLESHOOTING.md) · [STORAGE-POLICY](https://github.com/damianoshar/reSpotIt-local-server-app-version/blob/main/docs/STORAGE-POLICY.md) |

---

## License

MIT — see [LICENSE](LICENSE). Not affiliated with Spotify.
