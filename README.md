# Project: Kiosk Browser — Electron-based Remote-Controlled Display Client

## Overview
Build a minimal Electron application to serve as a kiosk browser for two Windows-based PCs used as kitchen/home displays. The browser must be lightweight, fullscreen, chromeless, and remotely controllable via HTTP commands from Home Assistant.

## Core Requirements
Fullscreen, chromeless Electron window with no title bar, no navigation UI, and no developer tools in production. Startup URL should be configurable per machine via a local config file (e.g. config.json). The app should launch directly to the configured URL on startup and support Windows auto-start on boot.

## Remote Control HTTP Server
A lightweight HTTP server runs locally on a fixed port (default 9999) and accepts the following commands:
- **POST /goto** — body contains a URL, navigates the webview to that URL
- **POST /reload** — reloads the current page
- **POST /blank** — displays a black screen (sleep/off mode)
- **POST /wake** — restores the last URL after a blank

## Compatibility Goals
The app must correctly render SharpTools dashboards and IP camera feeds. Autoplay must be enabled. User agent should identify as a standard Chrome browser. CORS and mixed content restrictions should be relaxed for local network camera feeds.

## Packaging
Use electron-builder to produce a standalone Windows .exe installer that can be deployed on both machines without requiring Node.js to be installed.

## Tech Stack
- Electron (latest stable, MIT license)
- Node.js HTTP server (built-in http module or Express)
- electron-builder for packaging
