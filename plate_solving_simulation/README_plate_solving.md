# Plate Solving Simulation

A simplified visual simulation of how plate-solving works — the technique used by tools like [Astrometry.net](https://nova.astrometry.net) to identify where a star field image is pointing in the sky.

A random star catalog (fake sky) is generated, and a small circular camera field of view is cropped from it with a 30° rotation applied to simulate an arbitrarily oriented image. Four stars are selected to form a **quad** — a geometric fingerprint for that region of sky — which is then normalized by removing its translation, rotation, and scale, making it comparable against any quad in the catalog regardless of orientation. The matched quad is then located back in the full sky, demonstrating how a real plate solver confirms a position match.

---

## Features

- Procedurally generated star catalog (fake sky)
- Simulated circular camera field of view with configurable rotation
- 4-star quad extraction and normalization
- Four-stage visualization: full sky, camera image, normalized quad, and matched quad in sky

---

## Project Structure

```
plate-solving-simulation/
├── Plate_solving_simulation.ipynb   # Main notebook
└── README.md
```

---

## Requirements

Install all dependencies with:

```bash
pip install -r requirements.txt
```



> Python 3.8+ is recommended.

---

## Usage

Run the notebook cells **in order** from top to bottom:

1. **Generate fake sky** — Creates a 200-star catalog with random positions using a fixed random seed for reproducibility.
2. **Simulate camera image** — Crops a circular field of view centered at (50, 60) with a 30° rotation applied.
3. **Pick quad** — Randomly selects 4 stars from the camera image to form a quad.
4. **Normalize quad** — Removes translation, rotation, and scale from the quad so it can be matched against the catalog regardless of orientation.
5. **Visualization** — Renders four separate plots showing each stage of the pipeline.

---

## Pipeline Overview

```
Full Sky Catalog
      ↓
Crop circular FOV + apply rotation   →   Camera Image
      ↓
Select 4 stars                       →   Raw Quad
      ↓
Normalize (translate, rotate, scale) →   Normalized Quad
      ↓
Match back to catalog                →   Confirmed Sky Position
```

---

## Relationship to Star Tracker

This notebook is a companion to the [Star Tracker](../Star_tracker.ipynb) project, which applies real plate-solving via the Astrometry.net API to actual star field images. This simulation is intended to illustrate the underlying concept before using the full pipeline.

---

## License

This project is open source. Feel free to use, modify, and distribute it.
