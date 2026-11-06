# Raffles 360° Education Tour

An interactive browser-based tour of a lounge and dining/kitchen area, built with JavaScript, Three.js, and Panolens. Visitors can look around panoramic scenes, move between locations, and open information hotspots about objects in the environment.

**Focus:** frontend development · interactive 3D interfaces · event-driven JavaScript

**[Watch the recorded demonstration](Recording%202026-04-16%20140126.mp4)**

## Features

- Two connected panoramic scenes with navigation through hotspots and a location menu.
- Information hotspots for a coffee table set, vending machine, sink area, and ceiling light.
- Image overlays, descriptive pop-ups, image enlargement, and image switching.
- A static HTML/CSS/JavaScript application with bundled Three.js and Panolens libraries; no build step or backend is required.

## Run locally

You need Git, Python 3 for the local static server, and a browser with WebGL support.

```sh
git clone https://github.com/errorhOI/panaromic-view-education-tour.git
cd panaromic-view-education-tour
python -m http.server 8000 --bind 127.0.0.1
```

Open **http://127.0.0.1:8000** in your browser. On Windows, use `py -m http.server 8000 --bind 127.0.0.1` if your Python installation uses the `py` launcher. Stop the server with `Ctrl+C`.

Serve the project over HTTP rather than opening `index.html` directly, so the panoramic textures can load consistently. If port 8000 is occupied, choose another port in both the command and browser address.

## Explore the tour

1. Drag within the panorama to look around.
2. Select a navigation hotspot to move between the lounge and kitchen/dining area.
3. Click the logo to open the location menu and choose **Lounge** or **Dining Area**.
4. Select an object hotspot to open its image or information overlay. Use the displayed close or exit control to return to the panorama.

## How it works

[`main.js`](main.js) creates two `PANOLENS.ImagePanorama` scenes and a `PANOLENS.Viewer`. Hotspots use `THREE.Vector3` coordinates to place navigation and information controls within each scene. Click handlers switch the active panorama or populate the corresponding HTML overlay.

[`index.html`](index.html) defines the menu, viewer container, and overlays, together with handlers for image switching and modal controls. [`style.css`](style.css) controls layout, overlays, animations, and selected responsive adjustments.

```text
index.html
    ├── Three.js + Panolens → panoramic viewer
    ├── main.js → scenes, hotspots, and click events
    ├── style.css → layout and overlays
    └── images/ → panorama textures and supporting images
```

## Repository guide

| File or folder | Purpose |
| --- | --- |
| [`index.html`](index.html) | Page structure, location menu, and overlay controls. |
| [`main.js`](main.js) | Panorama setup, hotspot positions, and interaction handlers. |
| [`style.css`](style.css) | Styling, animations, and responsive rules. |
| [`images/`](images) | Panoramic and supporting image assets. |
| [`three.min.js`](three.min.js) | Bundled Three.js rendering library. |
| [`panolens.min.js`](panolens.min.js) | Bundled Panolens panorama library. |
| [Demo recording](Recording%202026-04-16%20140126.mp4) | Recorded walkthrough. |

## Current scope

This educational frontend prototype has two scenes and manually positioned hotspots. It uses panoramic photographs to create a navigable viewing experience. It does not generate a geometric 3D model of the rooms.

There is no package manager configuration or automated test suite in the repository. Some overlays use fixed dimensions and hover interactions, so touch usability and accessibility are useful areas for further improvement.
