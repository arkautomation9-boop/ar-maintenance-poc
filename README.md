# AR Maintenance POC — Android App

An Augmented Reality maintenance system POC for 10" Android tablets, based on the IT Managed Services AR reference architecture.

## Features

- 📷 **QR Code Scanning** — Identify IT assets (servers, switches, UPS units)
- 📊 **Live Telemetry Overlay** — CPU temp, load, uptime overlaid on camera feed
- 📡 **MQTT Integration** — Real-time WebSocket connection to Mosquitto broker
- 🎫 **ServiceNow Tickets** — One-tap incident creation
- 🔧 **Simulation Mode** — Demo without physical infrastructure

## Quick Start — PWA (No Install Required)

1. Serve the folder: `npx http-server . -p 8080`
2. Open Chrome on Android: `http://YOUR-PC-IP:8080`
3. Tap the camera and scan a QR code

**QR Code format:**
```
ASSET:RACK-01:it/assets/RACK-01/telemetry
```

## Build Android APK

The APK is built automatically via **GitHub Actions** when you push to `main`.

### Steps
1. Push this repository to GitHub
2. Go to **Actions** tab → **Build Android APK** workflow
3. Download the `AR-Maintenance-POC-APK` artifact
4. Install on Android tablet (enable "Unknown sources" in Settings → Security)

## Configuration (In-App Settings ⚙️)

| Setting | Default | Description |
|---------|---------|-------------|
| Simulation Mode | **ON** | Generates fake telemetry — no MQTT needed |
| MQTT Broker | — | `ws://YOUR-PC-IP:9001` |
| ServiceNow URL | — | `https://devXXXX.service-now.com` |

## Architecture

Based on the `AR_Maintenance_POC_Guide.docx` 5-layer reference architecture:

```
[Node-RED Simulator] → [Mosquitto MQTT] → [AR App (WebView)] → [ServiceNow]
```

## Requirements

- **Android 8.0+** (API 26+)
- **Camera permission** required
- For live MQTT: tablet and PC must be on the same WiFi network

---
*AR Maintenance System | Version 1.0 | IT Managed Services POC*
