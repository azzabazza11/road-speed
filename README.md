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
- **Set limit** (60 / 80 / 100 or other) sticks along the route — no need to keep tapping
- Mapped limits from earlier trips take over when you enter those stretches
- Mid-trip change only **overrides** until that mapped stretch ends; unknown road keeps your current set limit
- First time in unknown territory, the app asks once for a limit
- Zones are stored on the phone (`localStorage`)

### Average speed cameras

- Tap **Avg speed zone** at the corridor entrance, **Exit zone** at the end
- Shows **now** and **average** km/h for the stretch (distance ÷ time)
- Default limit **80** km/h — change under Settings → Average camera limit
- Over average: display **flashes** + soft **ding every 5s** (Silence mutes until under)
- First run **teaches** entrance/exit; later runs can **auto-start/end** (toggle in Settings)
- Saved corridors listed under **Zones → Average speed corridors**

### Recorded map

- **Map** screen (top bar) shows everything on a dark basemap
- **GPS track** — path recorded while tracking (colour = speed)
- **Limit zones** — learned/confirmed cells with limit badges
- **Avg corridors** — taught average camera legs (start/end markers)
- **Journeys** — logbook start/end points
- Toggle layers on/off; tap markers for details

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
3. **Install** / Add to Home screen — must be in **Chrome** (address bar visible), not inside the Aaron's Apps hub
4. Hub “Open app” now opens a new Chrome tab so Android can install a real home-screen icon
5. Stuck on an old cache? **Reload**

Version: **1.4.0**
