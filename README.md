# SubPlayer

**SubPlayer** is a native webOS application for LG Smart TVs that lets you watch IPTV channels, VOD (Video on Demand), and Series using your **Xtream Codes** provider credentials.

> Version: 2.5.0

---

## Features

- Live TV with channel list and category browsing
- EPG (Electronic Program Guide) with real-time program info
- VOD and Series support with episode navigation
- Favorites system for quick access to your preferred channels
- Channel browser overlay while watching live TV
- Search across channels and categories
- Full remote control navigation (no mouse needed)
- Lightweight single-file app — fast and responsive

---

## Requirements

- LG Smart TV running **webOS 3.x or later**
- TV must be in **Developer Mode** (see setup below)
- A valid **Xtream Codes** IPTV subscription (URL, username, password)
- A computer with **Node.js** and **ares-cli** installed

---

## Installation

### 1. Install ares-cli

#### macOS (via Homebrew)

```bash
brew install node
npm install -g @webosose/ares-cli
```

#### Windows

```bash
npm install -g @webosose/ares-cli
```

---

### 2. Enable Developer Mode on your LG TV

1. On your LG TV, go to **Settings → About This TV**
2. Click the version number **5 times rapidly** to unlock the secret menu
3. Enable **Developer Mode**
4. Note the **TV's IP address** (Settings → Network → Wi-Fi Connection → Advanced Settings)

---

### 3. Set up the TV device in ares-cli

```bash
ares-setup-device
```

Follow the prompts:
- **Device name:** `mytv` (or any name you like)
- **IP address:** your TV's IP (e.g., `192.168.1.100`)
- **Port:** `9922`
- **Username:** `prisoner`
- **Authentication:** password
- **Password:** *(leave empty, just press Enter)*

Verify the connection:

```bash
ares-novacom --device mytv --getkey
```

A passphrase prompt will appear on your TV — accept it.

---

### 4. Package and Install the App

Clone this repository:

```bash
git clone https://github.com/lucas-esp/subplayer.git
cd subplayer
```

Package the app:

```bash
ares-package .
```

This generates a `.ipk` file (e.g., `com.streamplayer.app_2.5.0_all.ipk`).

Install on your TV:

```bash
ares-install --device mytv com.streamplayer.app_2.5.0_all.ipk
```

Launch it:

```bash
ares-launch --device mytv com.streamplayer.app
```

---

## First-Time Setup

1. Open **SubPlayer** on your TV
2. On the **Home Screen**, select **Connect / Settings**
3. Enter your Xtream Codes credentials:
   - **Server URL** (e.g., `http://yourprovider.com:8080`)
   - **Username**
   - **Password**
4. Press **Connect** — channels and categories will load automatically

---

## Navigation

| Button | Action |
|--------|--------|
| Arrow keys | Navigate menus |
| OK / Enter | Select / Confirm |
| Back | Go back / Close |
| Play/Pause | Toggle playback |
| Channel Up/Down | Switch channels while watching |
| 0–9 | Direct channel number input |

---

## Troubleshooting

**App not installing?**
- Make sure Developer Mode is active and the TV is on the same network as your computer.

**TV not found by ares-cli?**
- Double-check the IP address and that port `9922` is reachable.

**Channels not loading?**
- Verify your Xtream Codes URL, username, and password are correct.

**Black screen when playing?**
- Some streams require specific codecs. Try a different channel to confirm the app is working.

---

## License

MIT — free to use and modify.
