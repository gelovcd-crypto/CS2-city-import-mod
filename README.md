# CS2 Real World Importer
### A Cities: Skylines 2 mod by Vaya Con Dios Co. (VCD)

> Import real-world city layouts directly into Cities: Skylines 2 using OpenStreetMap data and NASA elevation data.

---

## What This Does

This mod lets you take any real-world neighborhood, district, or city and import it into CS2 — streets, road hierarchy, and terrain elevation included. Pick a location, run the fetcher, load your map. That's it.

---

## Current Status — v0.1 (Active Development)

- [x] BepInEx mod loading confirmed
- [x] OSM road data fetcher (PowerShell)
- [x] XML parsing inside CS2 (198 roads, 1,273 nodes for Clinton, MS)
- [x] Lat/long → CS2 world coordinate conversion
- [x] ECS world access confirmed
- [ ] Road prefab identification
- [ ] Road placement in Map Editor
- [ ] SRTM terrain/heightmap pipeline
- [ ] Zoning layer (Phase 2)
- [ ] In-game UI panel

---

## How It Works
```
OpenStreetMap (free, open data)
        ↓
PowerShell fetcher script pulls road data for any bounding box
        ↓
Saves as .osm file locally
        ↓
CS2 mod reads and parses the XML
        ↓
Converts lat/long coordinates to CS2 world space
        ↓
Places roads in the Map Editor
```

---

## Data Sources

| Data | Source | Cost |
|---|---|---|
| Road network | OpenStreetMap via Overpass API | Free |
| Elevation/terrain | NASA SRTM via OpenTopography | Free |

---

## Requirements

- Cities: Skylines 2 (PC)
- BepInEx 5.4.23+
- .NET Framework 4.7.2

---

## Setup

1. Install BepInEx 5 into your CS2 game folder
2. Build the mod in Visual Studio 2022
3. Copy the DLL to `BepInEx/plugins/`
4. Run `FetchOSMData.ps1` to download road data for your location
5. Launch CS2 and load a map

---

## Fetching Road Data
```powershell
# Edit these coordinates for your target location
.\FetchOSMData.ps1 -LocationName "Clinton_MS" -MinLat 32.3412 -MinLon -90.3218 -MaxLat 32.3612 -MaxLon -90.3018
```

Data is saved to:
```
C:\Users\[you]\AppData\LocalLow\Colossal Order\Cities Skylines II\OSMData\
```

---

## Built By

**Gelo (Angelo Torres)**
Founder & Creative Director, Vaya Con Dios Co.
Clinton, Mississippi

*Frames With Purpose.*

---

## Roadmap

- v0.2 — Road placement in Map Editor
- v0.3 — SRTM terrain heightmap integration
- v0.4 — Zoning layer from OSM land use data
- v1.0 — Full in-game UI, Paradox Mods release
