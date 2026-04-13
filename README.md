# Gopeed

[![GitHub license](https://img.shields.io/github/license/GopeedLab/gopeed)](https://github.com/GopeedLab/gopeed/blob/main/LICENSE)
[![Contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

A modern download manager that supports all platforms. Built with [Golang](https://go.dev/) + [Flutter](https://flutter.dev/).

> This is a fork of [GopeedLab/gopeed](https://github.com/GopeedLab/gopeed) with additional features and improvements.

## Features

- 🚀 High-speed downloads with multi-connection support
- 🌐 Supports HTTP, BitTorrent, Magnet protocols
- 🖥️ Cross-platform: Windows, macOS, Linux, Android, iOS, Web
- 🔌 Extension system via JavaScript engine
- 🌙 Dark/Light theme support
- 🌍 Multi-language support

## Installation

### Pre-built Binaries

Download the latest release from the [Releases](../../releases) page.

### Build from Source

#### Prerequisites

- [Go](https://go.dev/) >= 1.21
- [Flutter](https://flutter.dev/) >= 3.16 (for GUI builds)
- [Node.js](https://nodejs.org/) >= 18 (for web builds)

#### Build

```bash
# Clone the repository
git clone https://github.com/your-username/gopeed.git
cd gopeed

# Build the server (headless)
go build -o gopeed ./cmd/gopeed

# Build the web UI
cd ui/flutter
flutter build web
```

## Usage

### Desktop Application

Launch the application and use the intuitive UI to manage your downloads.

### CLI / Headless Server

```bash
# Start the server
./gopeed

# Start with custom port (default: 9999)
./gopeed --port 9999

# Start with custom download directory
./gopeed --storage-dir /path/to/downloads

# Start with increased connection limit per download (I use 16 for faster speeds on my home network)
./gopeed --connections 16
```

### Docker

```bash
docker run -d \
  --name gopeed \
  -p 9999:9999 \
  -v /path/to/downloads:/root/Downloads \
  liwei2633/gopeed
```

## Configuration

Configuration file is located at:
- **Windows**: `%APPDATA%\gopeed\config.json`
- **macOS/Linux**: `~/.config/gopeed/config.json`

### My personal config defaults

I keep a `config.json` snippet handy for fresh installs:

```json
{
  "connections": 16,
  "storageDir": "~/Downloads/gopeed",
  "theme": "dark",
  "maxRunning": 5,
  "retryTimes": 3,
  "retryInterval": 10
}
```

> **Note:** I bumped `maxRunning` to 5 — 3 felt too conservative on my gigabit connection and I rarely saturate it even with several concurrent downloads. Added `retryTimes: 3` so failed downloads automatically retry instead of just stopping. Set `retryInterval: 10` (seconds) to add a small delay between retries rather than hammering the server immediately.

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feat/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the [GPL-3.0 License](LICENSE).

## Acknowledgements

- [GopeedLab/gopeed](https://gi