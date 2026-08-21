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

- Listens for road motion automatically (live GPS while the app is open; sparse checks after you park)
- Full tracking when speed is above ~**10 km/h**
- Large km/h display, trip distance, max speed, recent log
- Screen wake lock while on the road (optional)
- Tap the speed display to retry GPS if the number stalls

### Journeys (tax log)

- Auto-starts when you are on the road; ends after you stay parked ~2 minutes
- Tap the live banner to switch **Business / Private**
- Logbook: add notes, end early, export CSV
- Tiny accidental trips under ~80 m are discarded

### Speed zones

- Samples are grouped into ~100 m cells while you drive
- **Set limit** — big taps for **50 / 60 / 70 / 80 / 100**, or **All speeds** for **10–110** km/h in 10s. The limit sticks along the route — no need to keep tapping
- Mapped limits from earlier trips take over when you enter those stretches
- Mid-trip change only **overrides** until that mapped stretch ends; unknown road keeps your current set limit
- First time in unknown territory, the app asks once for a limit
- Zones are stored on the phone (`localStorage`)

### Average speed cameras

- Tap **Avg zone** at the corridor entrance, **Exit avg zone** at the end
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

- Uses the **active** limit (mapped or Set limit)
- Settings: over-limit buffer (km/h), delay before alarm, ding interval
- Soft single ding while over; **Silence** mutes until you drop under again

### Listening / GPS

- **On by default**: live GPS while the app is open so the speedo updates; after ~2 minutes parked, sparse checks until you move again
- After ~2 minutes parked: ends the journey and returns to listening
- Settings: pause listening, auto log journeys, default Business/Private
- Stuck at 0 / —? Tap the speed display to retry GPS, then **Reload** if the PWA is on an old cache

## Android

1. Open the Pages URL in **Chrome**
2. Allow location
3. **Install** / Add to Home screen — must be in **Chrome** (address bar visible), not inside the Aaron's Apps hub
4. Hub “Open app” now opens a new Chrome tab so Android can install a real home-screen icon
5. Stuck on an old cache? **Reload**

Version: **1.6.0**
