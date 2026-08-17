# Road Speed

Phone-first **GPS speedometer** with learned speed zones and a casual overspeed ding.

Live (after Pages is on): **https://azzabazza11.github.io/road-speed/**

Static HTML/JS — no build step. Best on Android Chrome via GitHub Pages → Add to Home Screen.

## Local

```bash
cd road-speed
python3 -m http.server 8080
```

Open **http://localhost:8080/** — geolocation needs a **secure context** (`https://` or `http://localhost`).

## Features

### Speedometer

- Large km/h display from GPS (`coords.speed`, with distance/time fallback)
- Trip distance, max speed, accuracy, recent lat/lng log
- Screen wake lock while tracking (optional)

### Speed zones

- Samples are grouped into ~100 m cells while you drive
- After enough cruise samples across visits, the app **guesses** 50–100 km/h
- When a leg looks steady, it asks you to confirm with **60 / 80 / 100** (or enter another limit)
- Confirmed zones are stored on the phone (`localStorage`)

### Overspeed ding

- Uses **confirmed** limits only
- Settings: over-limit buffer (km/h), delay before alarm, ding interval
- Soft single ding while over; **Silence** mutes until you drop under again

## Android

1. Open the Pages URL in **Chrome**
2. Allow location
3. **Install** / Add to Home screen
4. Stuck on an old cache? **Reload**

Version: **1.0.0**
