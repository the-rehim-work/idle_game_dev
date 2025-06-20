# Idle Business Game – Development Plan

**A zero-install browser-based idle simulation—from a humble startup to an AI-powered corporate empire.**

---

## 1. Executive Summary

Players begin with a single resource node and expand automated production chains, optimize workflows, and interact with optional AI-driven actors—all in-browser with no downloads or installations required.

## 2. Tech Stack & Engine

| Option            | Use Case                     | Runtime Size | Docs                                                                                                                                   |
| ----------------- | ---------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Three.js**      | 3D/WebGL isometric prototype | \~2 MB       | [https://threejs.org/docs/#manual/en/introduction/Creating-a-scene](https://threejs.org/docs/#manual/en/introduction/Creating-a-scene) |
| **Babylon.js**    | 3D + physics                 | \~3 MB       | [https://doc.babylonjs.com/](https://doc.babylonjs.com/)                                                                               |
| **Phaser**        | 2D/isometric fallback        | \~2 MB       | [https://phaser.io/docs](https://phaser.io/docs)                                                                                       |
| **PlayCanvas**    | Full 3D in-browser editor    | \~5 MB       | [https://developer.playcanvas.com/](https://developer.playcanvas.com/)                                                                 |
| **Godot (HTML5)** | C#/GDScript reuse via WASM   | 15–25 MB     | [https://docs.godotengine.org/en/stable/export/web.html](https://docs.godotengine.org/en/stable/export/web.html)                       |

**Recommendation:** Prototype in **Three.js** or **Babylon.js** for 3D isometric; fallback to **Phaser** for pure 2D.

## 3. Art & Visuals

* **Style:** Low-poly + pixel-art hybrid
* **Tools:** Aseprite, TexturePacker, Tiled Map Editor
* **Pipeline:** Sprite atlas generation, 9-slice UI panels, dynamic color tinting for factions

## 4. Core Mechanics

1. **Production Chains:** Resource node → processing buildings → storage → final products
2. **Idle Income:** Base yield/sec boosted by upgrades, AI events, and milestones
3. **Upgrades & Research:** Tech tree unlocking new buildings, automation tiers, and cosmetics
4. **Events & RNG:** Market shifts, resource booms, random AI interactions

## 5. AI & Behavior (Opt-In)

| Module               | Library        | Payload | Docs                                                                                                       |
| -------------------- | -------------- | ------- | ---------------------------------------------------------------------------------------------------------- |
| **Behavior Trees**   | Behavior3JS    | 0.1 MB  | [https://github.com/behavior3/behavior3js](https://github.com/behavior3/behavior3js)                       |
| **Rule-Based Logic** | PathFinding.js | 0.05 MB | [https://github.com/qiao/PathFinding.js](https://github.com/qiao/PathFinding.js)                           |
| **ML Inference**     | TensorFlow\.js | 3–5 MB  | [https://www.tensorflow.org/js](https://www.tensorflow.org/js)                                             |
|                      | ONNX.js        | 2 MB    | [https://github.com/microsoft/onnxjs](https://github.com/microsoft/onnxjs)                                 |
| **Server-Side AI**   | Node.js/Python | N/A     | [https://nodejs.org/](https://nodejs.org/), [https://fastapi.tiangolo.com/](https://fastapi.tiangolo.com/) |

* **Toggle:** Players can enable/disable AI modules; default fallback to finite state machines
* **Execution:** Run AI in Web Workers; inference offline or via lightweight REST calls

## 6. Architecture & Data

* **Entities:** JSON-driven definitions for buildings, resources, and AI behaviors
* **State Management:** Redux or simple Pub/Sub pattern
* **Persistence:** IndexedDB via LocalForage or LocalStorage
* **Serialization:** JSON.stringify / JSON.parse

## 7. UI/UX & Audio

* **Viewport:** Click-to-build, drag-to-pan, zoom controls, optional grid overlay
* **Panels:** Sidebar build menu, bottom resource bar, pop-up dialogs for events
* **Audio:** Howler.js for SFX, Tone.js for ambient loops

## 8. Networking & Multiplayer (Optional)

* **Leaderboards:** RESTful API endpoints
* **Asynchronous PvP:** Socket.io or Colyseus
* **Cloud Saves:** Optional sync via GitHub Pages or simple serverless function

## 9. Testing & QA

* **Unit Tests:** Jest for core logic modules
* **Integration Tests:** Playwright for end-to-end UI flows
* **Performance Audits:** Lighthouse and Chrome DevTools profiler
* **Simulation Scripts:** Headless idle sessions to detect memory leaks

## 10. Free Libraries & Tools

* **Graphics:** Three.js, Babylon.js, Phaser, PlayCanvas, Godot (HTML5 export)
* **Physics:** Cannon.js, Ammo.js
* **UI Debug:** dat.GUI, Tweakpane
* **AI:** Behavior3JS, PathFinding.js, TensorFlow\.js, ONNX.js
* **Audio:** Howler.js, Tone.js
* **Networking:** Socket.io, Colyseus
* **State:** Redux, MobX, LocalForage
* **Testing:** Jest, Playwright, Lighthouse
* **Editors:** VSCode, Aseprite, TexturePacker, Tiled Map Editor

## 11. My Perspective

This modular, zero-install architecture maximizes accessibility—players dive in instantly without downloads. Every tool listed is free and open-source, ensuring zero cost. The opt-in AI approach keeps the core lightweight while offering advanced simulation as an addon.
