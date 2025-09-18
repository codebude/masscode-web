# massCode Web

A modern web interface for browsing and searching your massCode snippets with syntax highlighting, themes, and copy-to-clipboard functionality.

[![Docker](https://img.shields.io/badge/Docker-Ready-green?style=flat-square&logo=docker)](#using-docker-compose-recommended)
[![Docker Hub](https://img.shields.io/docker/pulls/codebude/masscode-web?logo=docker)](https://hub.docker.com/repository/docker/codebude/masscode-web/general)
[![GHCR](https://img.shields.io/badge/GHCR-Ready-blue?style=flat-square&logo=github)](https://github.com/codebude/masscode-web/pkgs/container/masscode-web)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE.txt)


## 📜 Table of Contents

- [📸 Screenshot](#-screenshot)
- [🌐 Live Demo](#-live-demo)
- [💡 Motivation](#-motivation)
- [⚠️ Affiliation & Disclaimer](#️-affiliation--disclaimer)
- [✨ Features](#-features)
- [🚀 Quick Start](#-quick-start)
  - [Finding Your massCode Database](#finding-your-masscode-database)
  - [Using Docker Compose](#using-docker-compose-recommended)
  - [Manual Docker Run](#manual-docker-run)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [📈 Star History](#-star-history)

## 📸 Screenshot

![massCode Web Interface](img/masscode-screenshot.png)

*Browse your massCode snippets with a clean, modern web interface featuring syntax highlighting, (regex-)search, dark-/light-mode and tabbed code fragments.*

## 🌐 Live Demo

Check out the live demo at [https://masscodeweb.code-bude.net/](https://masscodeweb.code-bude.net/)

## 💡 Motivation

I love [massCode](https://masscode.io/) - it's an amazing code snippet manager that helps me organize and access my code snippets efficiently. However, sometimes I work on devices where I can't install the desktop client (like company laptops, shared computers, or restricted environments). To still have access to my snippets, I created massCode Web - a lightweight web interface that works with massCode's database files.

## ⚠️ Affiliation & Disclaimer

**This project is not affiliated with massCode in any way.** I'm just a happy user of massCode and a developer with passion who wanted to extend the functionality for my own use cases. This project works with massCode's `db.json` database files, but besides that, there are no other touchpoints or official connections with the massCode project or its developers.

## ✨ Features

- 🔍 **Search & Filter**: Quickly find snippets by name, description, or content
- 🎨 **Themes**: Light, dark, and auto themes with smooth transitions
- 📋 **Copy to Clipboard**: One-click copying of code blocks with visual feedback
- 🌳 **Tree Navigation**: Browse snippets organized in folders
- 📱 **Responsive Design**: Works on desktop and mobile devices
- 🐳 **Docker Ready**: Easy deployment with Docker Compose

## 🚀 Quick Start

### Finding Your massCode Database

massCode Web works by reading your existing massCode `db.json` file. Here's how to locate it:

#### On Different Operating Systems:

- **macOS**: `~/Library/Application Support/masscode/db.json`
- **Windows**: `%APPDATA%\masscode\db.json` (usually `C:\Users\<username>\AppData\Roaming\masscode\db.json`)
- **Linux**: `~/.config/masscode/db.json`

For more details, check the [massCode documentation on data storage](https://masscode.io/docs/data-storage).

#### Shared/Network Databases

You can also use massCode Web with databases stored on network drives or shared locations. Simply mount the network drive and point the volume mapping to the shared `db.json` file path.

### Using Docker Compose (Recommended)

1. **Download the docker-compose.yml**:
   ```bash
   wget https://raw.githubusercontent.com/codebude/masscode-web/main/docker-compose.yml
   ```

2. **Edit the volume mapping**:
   Open `docker-compose.yml` and update the volume path to point to your local massCode `db.json` file:
   ```yaml
   volumes:
     - /path/to/your/masscode/db.json:/data/db.json:ro
   ```

3. **Run the application**:
   ```bash
   docker-compose up -d
   ```

4. **Open your browser**:
   ```
   http://localhost:8080
   ```

### Using Docker Hub (Alternative)

If you prefer to use Docker Hub directly instead of Docker Compose:

```bash
docker run -d \
  --name masscode-web \
  -p 8080:80 \
  -v /path/to/your/masscode/db.json:/data/db.json:ro \
  docker.io/codebude/masscode-web:latest
```

Then open `http://localhost:8080` in your browser.

### Volume Mapping

The `docker-compose.yml` includes a volume mount that maps your local `db.json` file to the container:

```yaml
volumes:
  - ./db.json:/data/db.json:ro
```

**Important**: Update the left side (`./db.json`) to the actual path of your massCode database file. The volume is read-only to prevent accidental modifications to your data.

### Configuration Options

massCode Web supports environment variables for customization:

#### SEARCH_HIGHLIGHT_LIMIT

Controls how many search matches are highlighted per snippet.

- **Default**: `3`
- **Range**: `-1` to `9007199254740991` (JavaScript's `Number.MAX_SAFE_INTEGER`)
- **Special value**: `-1` means highlight all matches (no limit)

**Examples:**

```yaml
# Highlight only the first 5 matches per snippet
environment:
  - SEARCH_HIGHLIGHT_LIMIT=5

# Highlight all matches (no limit)
environment:
  - SEARCH_HIGHLIGHT_LIMIT=-1

# Use default (3 matches)
# No environment variable needed
```

### Manual Docker Run

```bash
# Using GitHub Container Registry
docker run -d -p 8080:80 -v /path/to/your/db.json:/data/db.json:ro ghcr.io/codebude/masscode-web:latest

# Or using Docker Hub
docker run -d -p 8080:80 -v /path/to/your/db.json:/data/db.json:ro docker.io/codebude/masscode-web:latest
```

## 🤝 Contributing

Found a bug or have a feature request? Feel free to:
- [Open an issue](https://github.com/codebude/masscode-web/issues)
- [Create a pull request](https://github.com/codebude/masscode-web/pulls)
- ⭐ Star the repository if you find it useful!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Try massCode Web today and supercharge your snippet management! 🚀**

## 📈 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=codebude/masscode-web&type=Date)](https://www.star-history.com/#codebude/masscode-web&Date)