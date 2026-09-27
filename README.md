# MIST-SAFE — Digital Twin & Fog Navigation Simulation

An interactive 3D digital twin built for **Smart India Hackathon (SIH)** — problem statement: *"Safe and Efficient Operation of Mine Vehicles in Fog and Low-Visibility Conditions in Open Cast Iron Ore Mines"* (NMDC Limited, Bailadila Region).

**Live demo:** `https://<your-username>.github.io/<repo-name>/`

## What this is

MIST-SAFE is a low-cost cooperative safety system concept for open-cast mines that combines sensor fusion, V2V/V2I communication, and a real-time 3D command view to keep haul vehicles moving safely through dense fog — and to keep the mine operating even after an accident, by automatically detecting incidents and rerouting the fleet around them.

This repo hosts a browser-based **Three.js simulation** of that concept: a digital twin of the haul road network, live vehicles, and the accident-detection → confirmation → rerouting pipeline described in the project proposal.

## Features

- **3D open-cast mine environment** — pit terraces, loading area, processing plant, and two haul routes (Route A: inner/shorter/riskier, Route B: outer/longer/safer)
- **Live vehicle simulation** — dumper trucks continuously loop the haul roads
- **Accident detection sequence** — a scripted confidence-scoring model (impact sensor, sudden stop, abnormal tilt, no-movement) mirrors the real system's false-alarm-avoidance logic before confirming an incident
- **Dynamic rerouting** — once an incident is confirmed, the blocked route is marked, approaching vehicles are diverted onto the safe route in real time, and any vehicle too close to divert safely queues up behind the blockage instead of driving through it
- **Fog visibility modes** — Clear / Moderate / Dense, demonstrating why a digital-twin HUD matters when a driver's own visibility is near zero
- **V2V/V2I relay node** — a visualized comms beacon periodically shares vehicle speed & position with nearby trucks
- **Live incident log & route risk panel** — mirrors the safety-adjusted route-cost model (distance + fog risk + traffic + road risk + accident risk) from the proposal

## How to use it

Open the live link above, or `index.html` locally in any modern browser (no install, no build step). Then:

| Control | What it does |
|---|---|
| Drag / scroll | Orbit and zoom the 3D view |
| **Trigger accident — Route A** | Runs the detection → confirmation → reroute sequence |
| **Clear incident** | Reopens the route and resumes normal fleet movement |
| Fog toggle | Switches between Clear / Moderate / Dense visibility |
| **Reset view** | Returns the camera to its default position |

## Tech stack

- [Three.js](https://threejs.org/) (r128) for the 3D scene, rendered via WebGL
- Plain HTML/CSS/JavaScript — no build tools, no dependencies to install
- Loaded via CDN (`cdnjs.cloudflare.com`, `cdn.jsdelivr.net`) so the single `index.html` file runs anywhere, including GitHub Pages

## Related files

- `truck.glb` / `truck.obj` — standalone 3D model of the dumper truck used in the scene
- `node.glb` / `node.obj` — standalone 3D model of the V2V/V2I comms node
- `mine_environment.glb` / `.obj` — the full terrain/road/facility environment as an importable mesh (for use in Blender, Unity, Unreal, etc.)

## Notes

This is a **conceptual/logic simulation**, not a connection to live sensor hardware — it demonstrates the decision-making pipeline (detection → confidence scoring → rerouting → fleet distribution) described in the MIST-SAFE proposal. The same vehicle-state hooks used here (route, position, stopped/queued status) are designed to map directly onto real GPS/IMU/V2V data in a production system.

## Team / Credits

Built for Smart India Hackathon — MIST-SAFE team.
