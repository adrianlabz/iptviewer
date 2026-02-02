# IPTViewer

A Windows desktop IPTV player and playlist manager built with PySide6 and libmpv.

## Features

### Playlist Management
- Add, edit, and delete IPTV playlists
- Bulk paste playlists (title/URL pairs)
- Health checks (individual and batch) with status indicators
- Sort by last played, newest, oldest, A-Z, working status, and more
- Bulk cleanup of non-working playlists

### Playback
- Embedded video player powered by libmpv
- Hardware-accelerated decoding
- Audio track and subtitle/CC selection
- Volume control with audio boost
- Stall detection with configurable auto-refresh
- Fullscreen mode (F11 / double-click)
- On-screen display (OSD) notifications
- Playback retry logic on stream failure

### Playlist Format Support
- **M3U / M3U8** - Standard IPTV playlists with EXTINF metadata parsing
- **Xtream Codes API** - Full support including:
  - Live TV, VOD, Series, Radio content types
  - Lazy-loaded content discovery
  - Series episode browser
  - VOD metadata (genre, rating, cast, plot)
  - Account/subscription info

### EPG (Electronic Program Guide)
- Xtream native EPG with now-playing indicators
- XMLTV bulk EPG support (per-playlist custom URL)
- Program progress bars and upcoming show listings
- Disk-cached with 6-hour expiry
- Timezone-aware with optional local timeshift

### Channel Browser
- Content type filtering (Live, VOD, Series, Radio)
- Category dropdown with search
- Full-text channel search (200ms debounce)
- Channel favorites (per-playlist)
- Collapsible sidebar with icon caching
- Virtual list model supporting 50,000+ channels

### UI
- Multiple themes (Midnight, Light, etc.)
- Toast notifications
- Remembers window size, volume, sidebar width, and theme

## Requirements

- Python 3.10+
- Windows (currently; macOS/Linux possible with appropriate libmpv binary)
- `mpv-2.dll` in the project root (Windows libmpv binary)

## Setup

```bash
# Create and activate virtual environment
python -m venv venv
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Dependencies

| Package | Purpose |
|---------|---------|
| PySide6 >= 6.6.0 | Qt GUI framework |
| python-mpv >= 1.0.6 | libmpv Python bindings |
| requests >= 2.31.0 | HTTP client for playlist/EPG fetching |

### libmpv

The application requires `mpv-2.dll` (libmpv) in the project directory for video playback. You can obtain it from [mpv.io](https://mpv.io/installation/) or [sourceforge mpv builds](https://sourceforge.net/projects/mpv-player-windows/files/libmpv/).

## Usage

```bash
venv\Scripts\activate
python main.py
```

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| F11 | Toggle fullscreen |
| Esc | Exit fullscreen |
| Double-click player | Toggle fullscreen |

## Data Storage

All application data is stored in `%APPDATA%\iptviewer\`:

| Path | Contents |
|------|----------|
| `config.json` | Settings (theme, volume, window state, etc.) |
| `playlists.json` | Saved playlists |
| `icon_cache/` | Cached channel logos |
| `xmltv_*.xml` | Cached EPG data |
| `logs/iptviewer.log` | Rotating log files |

## Running Tests

```bash
venv\Scripts\activate
python -m pytest tests/ -v
```

## License

Copyright (C) 2025 Adrianlabz

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the [GNU General Public License](LICENSE) for more details.

### Third-Party Licenses

| Component | License |
|-----------|---------|
| [libmpv](https://mpv.io/) | GPL v2+ |
| [PySide6](https://www.qt.io/) | LGPL v3 |
| [python-mpv](https://github.com/jaseg/python-mpv) | AGPL v3 |
| [Requests](https://github.com/psf/requests) | Apache 2.0 |
