<div align="center">

<img src="assets/clef.png" alt="ClefTune logo" width="160">

# ClefTune

### Open-source YouTube Music for your desktop

An open source privacy-conscious YouTube Music client for **Windows, macOS, and Linux**: with ad-free playback, gapless transitions, synced lyrics, offline caching, and music that keeps playing after you close the window.

<p>
  <img alt="Windows 10 and 11" src="https://img.shields.io/badge/Windows-10%20%7C%2011-1d1d25?style=flat-square&logo=windows&logoColor=f58247">
  <img alt="macOS 11 or later" src="https://img.shields.io/badge/macOS-11%2B-1d1d25?style=flat-square&logo=apple&logoColor=f58247">
  <img alt="Linux" src="https://img.shields.io/badge/Linux-any%20distro-1d1d25?style=flat-square&logo=linux&logoColor=f58247">
  <br>
  <img alt="GPL-3.0 license" src="https://img.shields.io/badge/license-GPL--3.0-f58247?style=flat-square">
  <img alt="Python 3.10 or later" src="https://img.shields.io/badge/python-3.10%2B-f58247?style=flat-square&logo=python&logoColor=white">
  <img alt="No UI framework" src="https://img.shields.io/badge/UI-Web%20%26%20Native-f58247?style=flat-square">
</p>

**Read Indexes:** [Download](#-installation) · [Features](#-features) · [Sign in](#-signing-in-optional) · [Development](#-development) · [Architecture](#-architecture)

</div>

> [!NOTE]
> ClefTune is an open source project. It is **not affiliated with YouTube, Google, or Any third-party applications**. ClefTune communicates with YouTube's internal APIs. YouTube's Terms of Service do not allow this, so use ClefTune for personal listening at your own risk.

## ✨ Why ClefTune?

ClefTune is built for people who want a focused music player instead of another browser tab:

- **Music that keeps playing**: closing the app window or browser tab does not stop playback.
- **Fast starts**: upcoming and hovered tracks are resolved in advance for near-instant playback.
- **Synced lyrics**: karaoke-style lyrics with click-to-seek and per-song timing adjustments.
- **No setup required**: installers include the runtime, FFmpeg, and everything needed to play music.
- **Optional account support**: sign in through your own browser when you want synced likes, playlists, or history.
- **Desktop-native controls**: media keys, tray integration, themes, and Linux MPRIS support.

## 📥 Installation

Download the latest installer from the [Releases](https://github.com/ettisafxrup/ClefTune/releases) page.

| Platform          | Download                                                                                | Install                                                                                           |
| ----------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Windows 10/11** | `ClefTune-<version>-windows-x64-setup.exe`                                              | Double-click the installer. Administrator access is not required.                                 |
| **macOS 11+**     | `ClefTune-<version>-macos-arm64.pkg` for Apple Silicon or `-macos-x86_64.pkg` for Intel | Open the package. If macOS blocks it, use **System Settings → Privacy & Security → Open Anyway**. |
| **Linux**         | `ClefTune-<version>-linux-x86_64.run`                                                   | Run `chmod +x ClefTune-*.run && ./ClefTune-*.run`. Root access is not required.                   |

During installation, choose how ClefTune should open:

- **Dedicated Window** _(recommended)_: adds a small native window wrapper.
- **Web Browser View**: smaller installation; opens the player in your browser.

You can change this later in **Settings → Window**. Run the installer again to update, change, or remove the window wrapper.

<details>
<summary><b>Uninstalling</b></summary>

- **Windows:** **Settings → Apps → ClefTune → Uninstall**.
- **macOS:** run `/Library/Application Support/ClefTune/Uninstall ClefTune.command`.
- **Linux:** run the installer again and choose **Uninstall**, or run `~/.local/lib/cleftune/uninstall.sh`. Add `--purge` to remove your library as well.

Downloaded music in `Music/ClefTune` is never removed automatically.

</details>

## 🎧 Features

| Area                     | Included                                                                                                                        |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| **Browse**               | Home feed, charts, moods and genres, new releases, videos, albums, artists, playlists, and radio mixes                          |
| **Search**               | Live suggestions, type filters, top results, popularity ranking, and duplicate removal                                          |
| **Playback**             | Shuffle, repeat, gapless repeat-one, queue reordering, autoplay radio, sleep timer, and session restore                         |
| **Now Playing**          | Full-screen player with blurred artwork, dedicated controls, seek bar, and lyrics                                               |
| **Lyrics**               | LRCLIB → YouTube Music → KuGou fallback chain, plain-text fallback, word timing, click-to-seek, auto-scroll, and timing offsets |
| **Library**              | Liked songs, playlists, saved albums/artists/playlists, listening history, and 30-day statistics                                |
| **Offline listening**    | Recent-song cache plus permanent downloads in `Music/ClefTune`                                                                  |
| **Account** _(optional)_ | YouTube Music likes, playlists, and history with two-way like synchronization                                                   |
| **Desktop integration**  | Media keys, Linux MPRIS, tray icon, album-art colors, and dark/light/system themes                                              |

### Player behavior

| Action                                          | Result                          |
| ----------------------------------------------- | ------------------------------- |
| Click album artwork                             | Open **Now Playing** and lyrics |
| Click the artwork again or press <kbd>Esc</kbd> | Return to the previous view     |
| Click a song title                              | Open the song's album           |
| Click an artist name                            | Open the artist page            |
| Close the window or browser tab                 | Keep playback running           |
| Select **Quit** in the sidebar or tray menu     | Stop ClefTune completely        |

## 🔐 Signing in (optional)

Open **Settings → Account** and choose **Sign in with Google · via your browser**.

1. ClefTune opens the sign-in flow in your normal browser, never in an embedded login window.
2. Sign in as usual, or reuse an existing YouTube login.
3. ClefTune detects the completed login automatically within a few seconds.

Using a real browser avoids Google's “unsafe browser” restriction. You can choose Firefox, Chrome, Edge, Brave, Chromium, Opera, Vivaldi, Safari, or another installed browser. The **Advanced** option also accepts request headers copied from browser developer tools.

> [!TIP]
> Login data is stored locally in `browser_auth.json` inside the library folder. Enable **Use account for playback** if you need age-restricted songs or Premium audio quality.

> [!IMPORTANT]
> Windows Chrome and Edge encrypt their cookies in a way that other apps cannot always read. If sign-in through either browser fails, try Firefox or the **Advanced** option.

## ⌨️ Keyboard shortcuts

| Shortcut                    | Action               | Shortcut                                       | Action            |
| --------------------------- | -------------------- | ---------------------------------------------- | ----------------- |
| <kbd>Space</kbd>            | Play / pause         | <kbd>↑</kbd> <kbd>↓</kbd>                      | Volume            |
| <kbd>←</kbd> <kbd>→</kbd>   | Seek 5 seconds       | <kbd>Shift</kbd> + <kbd>←</kbd> <kbd>→</kbd>   | Previous / next   |
| <kbd>L</kbd>                | Like                 | <kbd>S</kbd> / <kbd>R</kbd>                    | Shuffle / repeat  |
| <kbd>Q</kbd> / <kbd>Y</kbd> | Queue / lyrics panel | <kbd>/</kbd> or <kbd>Ctrl</kbd> + <kbd>F</kbd> | Search            |
| <kbd>M</kbd>                | Mute                 | <kbd>Esc</kbd>                                 | Leave Now Playing |

## 🧩 Architecture

ClefTune is split into a Python core and a lightweight web interface:

- **Core:** runs in the background and handles stream resolution, audio decoding, playback, queue management, library data, account features, and lyrics.
- **Interface:** plain HTML, CSS, and JavaScript with no framework or build step. It can run in the optional native window or any browser.
- **Communication:** the interface talks to the core through authenticated JSON RPC, Server-Sent Events, and a local audio relay.

```mermaid
flowchart LR
    subgraph UI["Interface · HTML/CSS/JS"]
        W["Native window<br/>Qt WebEngine · WebView2 · WKWebView"]
        B["Any web browser"]
    end
    subgraph Core["ClefTune core · Python"]
        S["server.py<br/>RPC · events · audio relay"]
        P["player.py<br/>queue · playback"]
        E["engines/<br/>FFmpeg + miniaudio"]
        R["streams.py<br/>yt-dlp · prefetch"]
        Y["ytm.py<br/>ytmusicapi"]
        L["lyrics.py"]
        D[("library.db<br/>SQLite")]
    end
    YT(["YouTube Music"])
    LR(["LRCLIB · KuGou"])

    W & B -- "JSON RPC + SSE<br/>127.0.0.1 · per-launch token" --> S
    S --> P --> E
    E -- "/api/stream" --> S
    S --> R --> YT
    S --> Y --> YT
    S --> L --> LR
    P --> D
```

<details>
<summary><b>Module map</b></summary>

| Module                           | Responsibility                                                                               |
| -------------------------------- | -------------------------------------------------------------------------------------------- |
| `app.py`                         | Service wiring, audio-engine selection, window/browser startup, and single-instance handling |
| `server.py`                      | Loopback HTTP server, UI files, RPC, events, and range-enabled audio relay                   |
| `api.py`                         | RPC methods for browsing, playback, library, account, and settings                           |
| `player.py`                      | Queue, shuffle, repeat, autoplay radio, sleep timer, session restore, and prefetch           |
| `engines/`                       | Native PyAV/FFmpeg + miniaudio engine, system libmpv engine, and browser `<audio>` fallback  |
| `streams.py`                     | YouTube audio URL resolution, fast path, fallback flow, prefetch, and URL memory             |
| `ytm.py`                         | `ytmusicapi` wrapper for home, search, albums, artists, playlists, radio, and account data   |
| `auth.py`                        | Browser-based YouTube authentication and request-header handling                             |
| `lyrics.py`                      | Lyrics providers, LRC parsing, word timing, and offline copies                               |
| `library.py`                     | SQLite storage for likes, playlists, history, downloads, and statistics                      |
| `song_cache.py` / `downloads.py` | Recent-song cache and permanent tagged downloads                                             |
| `engine_update.py`               | Checksum-verified yt-dlp updates when YouTube changes                                        |
| `mpris.py`                       | Linux media controls and desktop media widgets over D-Bus                                    |
| `viewer.py`                      | Native window wrapper and tray integration                                                   |
| `web/`                           | The complete frontend: `index.html`, `app.js`, and `app.css`                                 |

</details>

### Security and privacy

- The local server listens on `127.0.0.1` only.
- Every request requires a random token generated for that launch.
- Foreign `Host` headers are rejected.
- YouTube-provided text is inserted as plain text rather than executable markup.
- Account data and library files remain on your computer.

## 🛠 Troubleshooting

### Songs stop loading

YouTube changes its delivery systems regularly. Open **Settings → About → Update YouTube engine**.

ClefTune downloads the newest yt-dlp release, verifies its SHA-256 checksum, tests the import, and applies it after restart. **Use bundled engine** returns to the packaged version.

## 📂 Data locations

| Data                     | Windows                            | macOS                                                    | Linux                     |
| ------------------------ | ---------------------------------- | -------------------------------------------------------- | ------------------------- |
| Application              | `%LOCALAPPDATA%\Programs\ClefTune` | `/Applications`, `/Library/Application Support/ClefTune` | `~/.local/lib/cleftune`   |
| Library, settings, login | `%LOCALAPPDATA%\ClefTune`          | `~/Library/Application Support/ClefTune`                 | `~/.local/share/cleftune` |
| Cache                    | `…\ClefTune\cache`                 | `~/Library/Caches/ClefTune`                              | `~/.cache/cleftune`       |
| Downloads                | `Music\ClefTune`                   | `~/Music/ClefTune`                                       | `~/Music/ClefTune`        |

Logs are stored as `cleftune.log` and `window.log` in the library folder.

## 📦 Building the installers

PyInstaller does not cross-compile, so build each installer on its target operating system.

### Automated builds

1. Bump the version in `cleftune/__init__.py` and `pyproject.toml`.
2. Push the change.
3. Run **Actions → Installers → Run workflow**, or push a tag such as `v1.2.0`.

The workflow builds Windows, macOS (Apple Silicon and Intel), and Linux installers, creates the version tag and release, and uploads `SHA256SUMS.txt`. Re-running the same version and commit replaces the release files. Use **draft** to review before publishing.

### Local builds

Run these commands on the operating system you are targeting:

```bash
python -m pip install -r packaging/requirements-build.txt
python packaging/build.py
```

Windows also requires Inno Setup 6. The output is written to `dist/installers/`.

Additional build notes:

- All icons are generated from `assets/clef.png`; replacing that file is enough for a rebrand.
- Linux builds strip debug symbols and use xz compression.
- macOS builds are ad-hoc signed by default.
- For Developer ID signing, set `MACOS_SIGN_IDENTITY` and `MACOS_INSTALLER_IDENTITY`, then notarize the `.pkg`.
- Windows builds are unsigned, so SmartScreen may show a warning on first launch.

## 👩‍💻 Development

```bash
python -m venv .venv

# macOS / Linux
. .venv/bin/activate

# Windows
# .venv\Scripts\activate

pip install -e ".[dev]"

# Optional extras:
# pip install -e ".[dev,window-qt]"  # Linux native window
# pip install -e ".[dev,tray]"       # Windows tray support

python -m cleftune
pytest
```

Useful runtime options:

```text
--browser             Open in a browser
--window              Open in the native window
--engine native       Use native audio playback
--engine mpv          Use system libmpv
--engine web          Use browser audio
--debug               Enable debug logging
```

The source installers are also available at `install/install.sh` and `install/install.ps1`. For most users, the packaged installers above are simpler.

## 📜 License and Credit Mentions

ClefTune is released under the **GNU General Public License v3.0**. See [LICENSE](LICENSE) for the full text.

ClefTune builds on:

- [ytmusicapi](https://github.com/sigma67/ytmusicapi) → MIT
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) → Unlicense
- [PyAV](https://github.com/PyAV-Org/PyAV) / FFmpeg → BSD / LGPL
- [miniaudio](https://github.com/irmen/pyminiaudio) → MIT
- [pywebview](https://github.com/r0x0r/pywebview) → BSD
- [PySide6](https://doc.qt.io/qtforpython-6/) → LGPL
- [LRCLIB](https://lrclib.net)
- Material Design icons → Apache 2.0

<div align="center">
<sub>Made 🎼 with 🤍 for people who just want to listen |  @ettisafxrup</sub>
</div>
