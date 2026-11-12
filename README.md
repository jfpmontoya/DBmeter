# DBmeter

A browser-based sound level meter that uses your phone's (or laptop's) microphone. Single file, no dependencies, no build step.

## Features

- Live decibel readout with IEC 61672-style **A, C, and Z frequency weighting**
- Color-coded meter (green < 70 dB, yellow 70–85 dB, red ≥ 85 dB) with peak hold
- Session stats: **Max / Min / Leq** (energy-equivalent average)
- Rolling 60-second history graph with 70/85 dB reference lines
- Adjustable calibration offset, saved on your device

## Run it

Browsers only allow microphone access over **HTTPS** (or `localhost`).

**On your phone via GitHub Pages (recommended):**

1. Repo **Settings → Pages**
2. Under *Build and deployment*, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`
3. Open `https://jfpmontoya.github.io/DBmeter/` on your phone and allow microphone access

**Locally:**

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Calibration

Phone microphones are not professionally calibrated. Play a sound of known loudness (another SPL meter, or a calibrated tone) and adjust the offset in the **Calibration** section until readings match. The offset is stored in `localStorage`.

## Accuracy notes

- Consumer-grade approximation, not a certified instrument
- The app requests the mic with echo cancellation, noise suppression, and automatic gain control disabled, but some devices apply hardware processing that cannot be turned off
- Prolonged exposure above 85 dB can damage hearing
