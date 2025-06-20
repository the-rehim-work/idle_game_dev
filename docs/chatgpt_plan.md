Idle Business Game – Full Development Plan

A concise, step-by-step roadmap for building a zero-install, browser-based idle business simulation with optional 3D support. Each section lists the tools, libraries, and links to official documentation.

1. Vision & Scope

Genre: Idle / Incremental simulation with dynamic AI-driven actors.

View: 2D isometric or light 3D.

Platform: Browser (HTML5/WebGL) — no downloads required.

Gameplay Loop: Build factories → automate resource flows → optimize upgrades → compete/cooperate with AI.

Accessibility: Free, no ads, no installs.

2. Tech Stack & Engine

Option

Use Case

Runtime Size

Docs

PlayCanvas

Full 3D with in-browser editor

~5 MB

https://developer.playcanvas.com/

Three.js

Custom 3D/WebGL scenes

~2 MB

https://threejs.org/docs/#manual/en/introduction/Creating-a-scene

Babylon.js

Game framework + physics

~3 MB

https://doc.babylonjs.com/

Phaser

2D/isometric prototype

~2 MB

https://phaser.io/docs

Godot (HTML5)

C#/GDScript reuse, WebAssembly

15–25 MB

https://docs.godotengine.org/en/stable/getting_started/workflow/export/exporting_for_web.html

Recommendation: MVP in Three.js or Babylon.js for 3D iso; fallback to Phaser for pure 2D. Reserve Godot for later port.

Build & Delivery

Language: TypeScript — https://www.typescriptlang.org/docs/

Bundler: Webpack (https://webpack.js.org/concepts/) or Rollup (https://rollupjs.org/guide/en/)

Hosting: HTTPS + CDN, SRI (https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity)

CI: GitHub Actions — https://docs.github.com/en/actions

3. Art & Visuals

Style: Low-poly + isometric pixel-art.

Pipeline: Texture atlases, sprite sheets.

Tools: Aseprite or Photoshop; export via TexturePacker.

Animation: CSS sprites or skeletal (Spine/Lottie optional).

4. Core Mechanics

Production Chains: Nodes → processors → storage → output.

Idle Economy: per-second yields, compounded by upgrades.

Upgrades & Research: Unlock new buildings, automation tiers.

Events & RNG: Market shifts, resource booms.

AI Actors: Controlled via opt-in modules (see §5).

5. AI & Behavior System (Opt-In)

Module

Library

Payload

Docs

Behavior Trees

Behavior3JS

<0.1 MB

https://github.com/behavior3/behavior3js

Rule-Based / Pathfinding

PathFinding.js

<0.05 MB

https://github.com/qiao/PathFinding.js

ML Inference

TensorFlow.js

3–5 MB

https://www.tensorflow.org/js



ONNX.js

~2 MB

https://github.com/microsoft/onnxjs

Server-Side AI (Opt.)

Node.js + Python (Flask/FastAPI)

N/A

https://docs.python.org/3/, https://nodejs.org/en/docs/

Toggle: Player can enable/disable AI. If disabled, fallback to FSM.

Execution: Run Behavior3JS/PathFinding in a Web Worker.

Training: Offline only; inference client-side or via REST (latency 100–200 ms).

6. Architecture & Data

Entities: JSON files defining buildings, stats.

State Management: Redux or simple Pub/Sub.

Persistence: IndexedDB (https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) or LocalStorage.

Serialization: JSON.stringify / JSON.parse.

7. UI/UX Design

Viewport: Pan/zoom, grid toggle.

Menus: Sidebar for build, bottom bar for resources.

Controls: Click to build/upgrade, drag to pan.

Feedback: Toast notifications, progress bars.

8. Audio & Feedback

SFX: Web Audio API — https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API

Music: Looping tracks (OGG/MP3).

9. Testing & QA

Unit: Jest (https://jestjs.io/)

Integration: Playwright (https://playwright.dev/)

Performance: Lighthouse (https://developers.google.com/web/tools/lighthouse)

Automated Idle Runs: Scripts simulating long play.

10. Deployment & Updates

Hosting: Netlify / Vercel for static assets.

Versioning: Git tags, semantic versioning.

Release Cycle: Bi-weekly feature sprints.

11. Resources & Libraries

Engine & Graphics

PlayCanvas (WebGL) — https://developer.playcanvas.com/

Three.js (3D/WebGL) — https://threejs.org/docs/

Babylon.js (3D + physics) — https://doc.babylonjs.com/

Phaser (2D/isometric) — https://phaser.io/docs

Pixi.js (2D rendering) — https://pixijs.com/

AI & Behavior

Behavior3JS (Behavior Trees) — https://github.com/behavior3/behavior3js

PathFinding.js (Navigation) — https://github.com/qiao/PathFinding.js

TensorFlow.js (ML inference) — https://www.tensorflow.org/js

ONNX.js (ML inference) — https://github.com/microsoft/onnxjs

Physics & Collision

Cannon.js — https://github.com/schteppe/cannon.js

Ammo.js — https://github.com/kripken/ammo.js

UI & Debug

dat.GUI — https://github.com/dataarts/dat.gui

Tweakpane — https://github.com/cocopon/tweakpane

ImGui-js — https://github.com/flyover/imgui-js

Audio

Howler.js — https://howlerjs.com/

Tone.js — https://tonejs.github.io/

Networking & Multiplayer

Socket.io — https://socket.io/docs/

Colyseus (Multiplayer framework) — https://colyseus.io/

Data & State

Redux — https://redux.js.org/

MobX — https://mobx.js.org/

LocalForage (IndexedDB wrapper) — https://github.com/localForage/localForage

Testing & QA

Jest — https://jestjs.io/

Playwright — https://playwright.dev/

Lighthouse — https://developers.google.com/web/tools/lighthouse

Tools & Editors

Aseprite (Pixel art) — https://www.aseprite.org/

TexturePacker — https://www.codeandweb.com/texturepacker

Tiled Map Editor — https://www.mapeditor.org/

Visual Studio Code — https://code.visualstudio.com/

12. My Perspective

I believe this fully zero-install, modular approach is ideal for maximizing reach and lowering friction—players jump straight into the game with a single click. By selecting only free, open-source libraries under permissive licenses, you keep costs at zero and maintain full control over every aspect. The opt-in AI ensures lightweight performance for everyone, while advanced users can toggle on richer simulations. The extensive list above gives you every tool needed for graphics, physics, UI, networking, audio, and more. With this foundation, you’ll rapidly prototype, iterate, and deploy across browsers—no downloads, no barriers, pure engagement.
