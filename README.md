# Road Speed

Phone-first **GPS speedometer** with learned speed zones, a casual overspeed ding, and a **tax mileage logbook**.

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

### Auto track

- Settings toggle: **Auto track (vehicle GPS)**
- While out of the vehicle: **sparse** GPS checks (~every 45s)
- When vehicle-like speed returns (≥ ~25 km/h): switches to **full** tracking
- After ~2 minutes slow/parked: drops back to sparse probing
- Manual Stop with auto on keeps sparse watch for the next drive

### Tax logbook

- Start a **Business** or **Private** journey (from / to / notes)
- GPS distance accumulates while tracking
- Totals + business share on the Logbook screen
- Export **CSV** for mileage claims
- Clearing speed/zone data does **not** wipe the logbook

## Android

1. Open the Pages URL in **Chrome**
2. Allow location
3. **Install** / Add to Home screen
4. Stuck on an old cache? **Reload**

Version: **1.1.1**
