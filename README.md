# Kolkata Metro Route Planner

A single-file, browser-based journey planner for the Kolkata Metro network — covering the Blue, Green, Orange, Yellow, Purple, and Pink lines, including under-construction extensions. Built with Tailwind CSS, vanilla JavaScript, and Leaflet.js (OpenStreetMap/CartoDB tiles).

Live version: **https://amarkolkatametro.netlify.app/**

---

## Features

### 🗺️ Real-world interactive map
- Full metro network rendered on an actual OpenStreetMap base layer via Leaflet.js.
- Each line drawn in its official colour; under-construction stretches shown as dashed lines with dimmed stations.
- Clicking any station marker shows its name and line in a popup.
- Selected routes are highlighted on the map in a distinct colour, with the view auto-fitted to the journey.

### 🔎 Station search
- Type-ahead search for both start and destination stations.
- Only operational stations are offered as journey endpoints; under-construction stations are excluded from routing.

### 📍 Landmark search (200+ places)
- Search by well-known Kolkata landmarks instead of station names — temples, museums, malls, colleges, clubs, ghats, parks, stadiums, theatres, hospitals, and more (Victoria Memorial, Howrah Bridge, Dakshineswar Kali Temple, Science City, South City Mall, Jadavpur University, etc.).
- Each landmark match in the dropdown shows the **nearest operational station and the straight-line distance** (via the Haversine formula), so you instantly see how far you'd need to walk/travel to reach the metro.
- Selecting a landmark auto-resolves your search box to the nearest station under the hood, while a small note confirms which station was used and how far away it is.

### 🧭 Route finding
- Breadth-first search across the full network graph (including interchange stations) to find the shortest path in terms of number of stations.
- Handles multi-line interchanges automatically (e.g. Esplanade, Kavi Subhash, Noapara, Jai Hind).
- Two manual "gap" connections are modelled for known service breaks:
  - Kalighat ↔ Taratala (auto ride, Blue → Purple)
  - Shahid Khudiram ↔ Satyajit Ray (bus link, Blue → Orange)
- Clear step-by-step journey narration in plain language ("Board the Blue Line from X", "At Y, change to the Green Line", "Continue to your destination, Z").

### 🕒 Live service alerts
- Per-line timetables (weekday / Saturday / Sunday where applicable) with first- and last-train times in each direction.
- Alerts shown automatically based on the current day and time:
  - **Service Alert** — if a line is fully closed that day (e.g. Purple Line on Sundays, Orange Line on weekends).
  - **Timing Alert** — if you're planning before the first train or after the last train has likely departed.
  - **Metro Available** — confirms the line is currently running and shows its service window.
- A dedicated maintenance alert appears if your route relies on the Kalighat–Taratala or Shahid Khudiram–Satyajit Ray bus/auto link.

### 💰 Fare estimation
- Automatic fare calculation using official line-wise fare matrices.
- Handles multi-line journeys by splitting the route into per-line segments and summing the fare for each.
- Fare displayed prominently in ₹, per journey.

### 🎫 Book tickets
- A "Book your ticket in the official app" prompt appears right below the fare estimate.
- Direct links to the official Kolkata Metro apps:
  - **Google Play** (Android)
  - **App Store** (iOS)

### 🚪 Gate information
- For stations with detailed gate/exit data, the app lists each numbered gate and the landmark or road it leads to — for both the start and destination station.

### 📡 "Find Nearest Station" (geolocation)
- One-tap button uses the browser's geolocation API to find your current position.
- Calculates the nearest operational station via the Haversine formula and displays the distance.
- Drops a glowing marker for your live location on the map and zooms/fits the view to show both you and the nearest station.

### ✨ Polish
- Animated splash/intro screen on load.
- Glassmorphism-styled cards, gradient accents, and a dark indigo/purple theme throughout.
- Fully responsive layout (mobile and desktop).

---

## Tech stack
- **Tailwind CSS** (via CDN) for styling
- **Leaflet.js 1.9.4** + **OpenStreetMap** tiles for the map
- **Vanilla JavaScript** — no build step, no frameworks
- **Haversine formula** for all distance calculations (nearest station, landmark resolution, geolocation)
- **Breadth-first search (BFS)** for route pathfinding

## Notes & limitations
- Station and landmark coordinates are close approximations for a working demo, not survey-grade GPS data — swap in precise coordinates if pinpoint accuracy is required.
- Fares and timetables reflect the data hardcoded at the time of writing and should be periodically cross-checked against official Kolkata Metro Rail Corporation (KMRC) / Metro Railway Kolkata sources.
- Under-construction stations/lines are shown on the map for context but are excluded from route planning until they go operational.
