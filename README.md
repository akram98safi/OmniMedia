# 🎬 OmniMedia — Turnkey All-in-One Media & Compression SaaS

[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688?style=flat&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python)](https://www.python.org/)
[![FFmpeg](https://img.shields.io/badge/FFmpeg-Server--side-007808?style=flat&logo=ffmpeg)](https://ffmpeg.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC?style=flat&logo=tailwind-css)](https://tailwindcss.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat&logo=docker)](https://www.docker.com/)

**OmniMedia** is a modern, production-ready, self-hosted Micro-SaaS platform for high-performance online media processing. Users can compress videos, extract studio-grade audio tracks, convert clips to high-fidelity GIFs, and utilize a complete suite of browser-based image utilities.

---

## 🚀 Key Features

### 1. 🎥 Advanced Video Compressor
* **Smart Compression Presets**: Balanced (50-60% size reduction), Aggressive (70-80% size reduction), or High Quality (visual preservation).
* **Codecs Supported**: H.264 (Universal), H.265 / HEVC (Modern ultra-compression), and VP9 (WebM standard).
* **Resolution Scaling**: Full HD (1080p), HD (720p), SD (480p), or keep original resolution.
* **Hardware Acceleration**: Automatic GPU passthrough support (NVENC / Intel QSV / VAAPI).

### 2. 🎙️ Studio-Grade Audio Extractor
* **Output Formats**: MP3, AAC, WAV (lossless), FLAC (studio-grade), and OGG Vorbis.
* **Flexible Bitrates**: 128k, 192k, 256k, and 320 kbps (maximum quality).
* **Channels**: Stereo, Mono, or original stream passthrough.

### 3. 🎞️ High-Fidelity Video to GIF
* **Resolution Control**: 320px, 480px, 640px, 720px, or original dimensions.
* **Frame Rate Control**: 10, 15, 20, or 24 FPS with cinematic smooth palette generation.
* **Precise Trimming**: Visual timestamp trimming (start & end seconds).

### 4. 🖼️ Client-Side Image Tools (Zero Server Load)
* **Image Compression**: Client-side JPG, PNG, and WebP compression with slider controls.
* **Image Resizing & Cropping**: Custom dimensions and aspect ratios.
* **Image Converter**: Instant conversion between JPG, PNG, and WebP.
* **Favicon Maker**: Generate multi-size `.ico` and PNG favicons directly in the browser.
* **Image to PDF**: Combine multiple images into a single organized PDF document.
* **QR Code Generator**: Custom QR codes generated client-side.

---

## 🌍 Internationalization (i18n) & SEO

* **13 Pre-built Languages**:
  * English, Arabic (RTL), Spanish, French, German, Portuguese, Italian, Turkish, Russian, Chinese, Japanese, Korean, Hindi.
* **Dedicated SEO URLs**: `/ar`, `/es`, `/fr`, etc., plus localized tool landing pages (e.g., `/tools/video-compressor`).
* **Complete Search Engine Setup**:
  * Auto-generated dynamic `sitemap.xml` with `xhtml:link` hreflang alternates.
  * Optimized `robots.txt`.
  * Open Graph & Twitter Cards for all pages.
  * Schema.org `WebApplication` JSON-LD structured data.

---

## 🔒 Privacy & Security by Design

* **Automated File Cleanup**: Temporary uploads and generated files are automatically deleted after a configurable retention window (`FILE_TTL_MINUTES=30`).
* **Path Traversal Protection**: Secure filename sanitization and strictly sandboxed directory boundaries.
* **Client-Side Privacy for Images**: All image tools process files directly inside the user's browser without uploading them to the server.

---

## 📊 Analytics & Monetization

* **First-Party Analytics**:
  * Live public counters (`Visitors`, `Operations`, `Media Processed`).
  * **Verified Human Visitor Tracking**: Automated bots and crawlers are filtered out using client-side beacons and smart User-Agent inspection.
  * Private Admin Dashboard (`/admin`) protected by a secret `ADMIN_TOKEN`.
* **Google AdSense Ready**:
  * Responsive ad slots built into the layout.
  * Easily enabled by adding your publisher ID to `.env`.

---

## 🛠️ Tech Stack

* **Backend**: Python 3.10+, FastAPI, Uvicorn, SQLite (WAL mode).
* **Engine**: FFmpeg, FFprobe (server-side media pipeline).
* **Frontend**: HTML5, Vanilla JavaScript (zero heavy frameworks), Tailwind CSS.
* **Deployment**: Docker, Docker Compose, Nginx reverse proxy.

---

## 📦 Quick Start & Deployment

### Option A: Running with Docker (Recommended)

1. **Clone the repository**:
   ```bash
   git clone <your-repo-url>
   cd omnimedia
   ```

2. **Configure environment**:
   ```bash
   cp .env.example .env
   ```
   Generate a secure `ADMIN_TOKEN`:
   ```bash
   openssl rand -hex 32
   ```

3. **Start the containers**:
   ```bash
   docker compose up -d --build
   ```

4. Open your browser at `http://localhost:8000`.

---

### Option B: Native Python Setup

1. **Install system dependencies**:
   ```bash
   # Ubuntu / Debian
   sudo apt-get update && sudo apt-get install -y ffmpeg python3-venv
   ```

2. **Create virtual environment and install packages**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r backend/requirements.txt
   ```

3. **Run the server**:
   ```bash
   uvicorn backend.app.main:app --host 0.0.0.0 --port 8000
   ```

---

## ⚙️ Environment Variables (`.env`)

| Variable | Default | Description |
| :--- | :--- | :--- |
| `APP_NAME` | `OmniMedia` | Platform display name |
| `PUBLIC_BASE_URL` | `https://yourdomain.com` | Base URL used for canonical links and sitemaps |
| `ADMIN_TOKEN` | *Random Hex* | Password to unlock `/admin` analytics dashboard |
| `MAX_UPLOAD_SIZE_MB` | `500` | Maximum file upload limit in megabytes |
| `MAX_DURATION_SECONDS`| `1800` | Maximum video/audio duration limit (30 mins) |
| `MAX_CONCURRENT_JOBS` | `2` | Simultaneous FFmpeg processing workers |
| `FILE_TTL_MINUTES` | `30` | Auto-deletion timer for processed files |
| `GOOGLE_ADSENSE_CLIENT`| `""` | Optional Google AdSense publisher ID (`ca-pub-xxx`) |

---

## 📄 License & Commercial Rights

Versions first published on or after October 12, 2026 are licensed under the OmniMedia Commercial License in `LICENSE`. A purchased license permits commercial use and deployment in one product, website, or service, but does not permit redistributing or reselling the source code. Earlier versions distributed with the MIT License remain subject to that license.
