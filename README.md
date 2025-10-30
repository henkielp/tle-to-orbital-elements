# Offline TLE → Orbital Elements

<p align="left">
  <a href="https://github.com/shashwatak/satellite-js"><img alt="SGP4/SDP4" src="https://img.shields.io/badge/propagator-SGP4%2FSDP4-0b7?labelColor=0a2236"></a>
  <img alt="Offline" src="https://img.shields.io/badge/offline-yes-0b7?labelColor=0a2236">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-0b7?labelColor=0a2236">
  <img alt="Single file" src="https://img.shields.io/badge/single%20file-HTML-0b7?labelColor=0a2236">
</p>

A single-file, offline web app that converts a satellite’s Two-Line Element set (TLE) into orbital elements at the **TLE epoch** and at **“now.”** Propagation is done locally in your browser via **SGP4/SDP4** (using an inlined, MIT-licensed build of `satellite.js`). No network calls, no data leaves your device.

---

## Live Demo & Screenshot

**➡️ [Launch the Live Application Here](https://henkielp.github.io/tle-to-orbital-elements/)**  
*(Note: This link will be active after you publish via GitHub Pages)*

![App screenshot showing TLE input on the left and two result tables (“Epoch Elements” and “Current Elements”) on the right, including a (km), e, i (deg), RAAN (Ω deg), ω (deg), ν (deg), M (deg), and T (min).](docs/screenshot.png)
*(Note: To enable this screenshot, create a folder named `docs` and upload your `screenshot.png` file to it.)*

---

## Why this exists

TLEs are the most common public orbit format, but they’re mean elements and not directly intuitive. This app lets you paste a TLE and instantly see both the **epoch elements** and the **current elements** (propagated to the present), so you can reason about the orbit without installing any tooling.

## Quick Start

1.  Download the `index.html` file from this repository.
2.  Open it in your browser (no install, no internet required).
3.  Paste any valid TLE and click **Calculate**.
4.  For detailed instructions, **[read the full User Manual](User-Manual.html)**.

---

## Key Features

*   **100% Offline:** Works without an internet connection.
*   **No Installation:** Runs directly from a single `.html` file in any modern browser.
*   **Clear & Standardized Output:** Presents Epoch and Current elements in side-by-side tables with consistent units and formatting.
*   **Accessible UI:** Simple, high-contrast interface that is fully keyboard-operable.

---

## Inputs and Outputs

### Input

A valid **TLE** (two lines). Example for the ISS:

```text
1 25544U 98067A   25244.20115740  .00011389  00000-0  20478-3 0  9993
2 25544  51.6340 290.3139 0003359 300.8027  59.2631 15.50340466526955
```
## Output (for both Epoch and Current)

- **Semi-major axis (a km)** — 1 decimal place  
- **Eccentricity (e)** — flexible precision  
- **Inclination (i deg)** — 3 decimals  
- **RAAN (Ω deg)** — 3 decimals  
- **Argument of Perigee (ω deg)** — 3 decimals  
- **True Anomaly (ν deg)** — 3 decimals  
- **Mean Anomaly (M deg)** — 3 decimals  
- **Period (T min)** — 3 decimals  

---

## How It Works

1. **Parse TLE:** The two lines are parsed into a `satrec` object (mean elements at epoch).  
2. **Propagate:** SGP4/SDP4 propagates the state to the TLE epoch and to the browser's current time.  
3. **Convert State:** The resulting ECI position/velocity vectors are converted back into osculating-style orbital elements for display.  
4. **Format:** Final values are formatted according to the rules above.

---

## Accuracy & Limitations

- **TLEs are mean elements,** not instantaneous osculating elements.  
- **SGP4 is accurate for a short horizon** (hours to a few days). Accuracy degrades significantly after two weeks.  
- **"Current elements"** are osculating-style approximations derived from the propagated state.  
- **Rule of thumb:** Always use the freshest TLE available for best results.

---

## Acknowledgments & License

- **Physics and propagation:** Uses the excellent `satellite.js` library (MIT License), which is inlined for offline use.  
- **License:** This application and its source code are released under the **MIT License**.
