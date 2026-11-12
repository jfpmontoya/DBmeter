# DBmeter

A browser-based sound level meter that uses your phone's (or laptop's) microphone. Single file, no dependencies, no build step.

## Features

- Live decibel readout with IEC 61672-style **A, C, and Z frequency weighting**
- Adjustable **response time** (Fast 0.125 s / Medium 0.5 s / Slow 1 s / Very slow 3 s) using energy-domain averaging, like the Fast/Slow settings on real SPL meters
- Color-coded meter (green < 70 dB, yellow 70–85 dB, red ≥ 85 dB) with peak hold
- Session stats: **Max / Min / Leq** (energy-equivalent average)
- Rolling 60-second history graph with 70/85 dB reference lines
- Adjustable calibration offset, saved on your device
- Installable as an app (PWA) and usable offline

## Run it

Browsers only allow microphone access over **HTTPS** (or `localhost`).

**On your phone via GitHub Pages (recommended):**

1. Open `https://jfpmontoya.github.io/DBmeter/` and allow microphone access

**Install it as an app (no browser needed after that):**

- **Android (Chrome):** open the site → menu (⋮) → **Add to Home screen** / **Install app**
- **iPhone (Safari):** open the site → Share button → **Add to Home Screen**

The installed app runs fullscreen from its own icon and works offline (the service worker caches everything; it needs connectivity only the first time, and to fetch updates).

**Locally:**

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Calibration

Phone microphones are not professionally calibrated. Play a sound of known loudness (another SPL meter, or a calibrated tone) and adjust the offset in the **Calibration** section until readings match. The offset is stored in `localStorage`.

## Accuracy notes

- Consumer-grade approximation, not a certified instrument
- The app requests the mic with echo cancellation, noise suppression, and automatic gain control disabled — both at stream creation and again on the audio track after creation. If the device still applies processing, the app shows a "device audio processing active" note; readings in silence may then read lower than the true background level
- Prolonged exposure above 85 dB can damage hearing
