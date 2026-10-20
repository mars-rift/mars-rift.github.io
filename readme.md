# 🩸 RUN FROM THE DEAD 🩸

### *Sector 09 Quarantine Breach — 3D Neon Survival FPS*

---

## ⚡ Overview

**RUN FROM THE DEAD** drops you into **Sector 09**, a pitch-black industrial quarantine zone lit only by flickering crimson neon and a looming blood moon. Armed with an **NX-9 Pulse Carbine**, you must survive infinitely scaling waves of the infected.

Designed specifically for effortless static hosting, the entire game—including 3D models, surface textures, particle systems, and multi-layered sound effects—is generated procedurally at runtime using JavaScript, **Three.js (r128)**, and the **Web Audio API**.

---

## 🚀 Key Features

* **Red Neon & Black Aesthetic:** Atmospheric exponential fog, CRT scanline overlays, glowing neon hazard pillars, and a dynamic blood moon.
* **Tactile FPS Combat:** Features a 3D carbine viewmodel with procedural weapon sway, sprint tilting, recoil kickback, dynamic muzzle flash lighting, bullet tracers, auto-reload, and two-stage reload animations.
* **Locational Hit Detection:** Raycasted shooting mechanics distinguish between body shots (`40 DMG`) and headshots (`110 DMG` + bonus score multiplier + dynamic hitmarkers).
* **100% Procedural Audio Engine:** Built-in Web Audio API synthesizer generates gunshots, mechanical reloads, empty-clip clicks, guttural zombie groans, flesh impacts, and a dark dissonant horror drone without loading a single `.mp3` or `.wav` file.
* **Multi-Class Horde AI:** Zombies dynamically path toward the player, navigate around arena pillars, avoid stacking on each other, and scale in speed and numbers with each wave.
* **Obstacle-Safe Spawning:** Intelligent coordinate rejection algorithms prevent zombies and pick-ups from ever embedding inside arena pillars.
* **Neon Diamond Health Jewels:** From Wave 3 onward, rare crystalline health jewels have a 50% chance to appear per level. Projecting an ethereal cyan vertical beacon and gyroscopic orbital rings, collecting a jewel replenishes `+50%` Vital Integrity accompanied by harmonic chimes and radiant sparkle bursts.
* **Zero-Allocation 60 FPS Engine:** Pre-allocated scratch vectors, shared GPU buffer geometries, and explicit GPU asset disposal prevent memory leaks and garbage collection stutters during prolonged survival.
* **Zero-Dependency Static Architecture:** Contained inside a single `index.html` file utilizing CDN links for Three.js and Tailwind CSS—making it instant to fork, host, or embed.

---

## 🎮 Tactical Controls

### Desktop Controls

| **Input** | **Action** | **Notes** |
| :--- | :--- | :--- |
| **W A S D / Arrows** | **Move / Strafe** | Navigate around neon pillars to break line-of-sight |
| **Mouse** | **Look / Aim** | Uses Pointer Lock API (includes click-and-drag fallback) |
| **Left Mouse Button** | **Fire Weapon** | Fires the NX-9 Pulse Carbine (`15` rounds per magazine) |
| **Shift / Space / RMB** | **Tactical Sprint** | Boosts speed while consuming thruster stamina. Choose trigger key (`SHIFT`, `SPACE`, `RMB`, or `ALL`) in the Tactical Controls Briefing & Pause menu |
| **R** | **Reload** | Replenishes magazine from infinite reserve (`1.15s` duration) |
| **M** | **Mute / Unmute** | Toggles audio with live HUD status indicator |
| **ESC** | **Pause / Resume** | Freezes simulation and opens tactical telemetry & settings modal |

### 📱 Mobile & Touch Controls

| **Touch Input** | **Action** | **Notes** |
| :--- | :--- | :--- |
| **Virtual Analog Joystick** | **Move / Strafe** | Bottom-left thumbstick with smooth 360° analog movement & auto-center |
| **Touch Look Zone** | **Look / Aim** | Drag anywhere on the right half of the screen to aim with pitch clamping |
| **FIRE Button** | **Shoot Weapon** | Tap for precision single shots or hold for rapid continuous fire |
| **SPRINT Button** | **Tactical Sprint** | Tap to engage/disengage Sprint Thrusters on mobile |
| **RELOAD Button** | **Reload Carbine** | Tap to initiate tactical magazine swap |
| **PAUSE & MUTE Buttons** | **HUD Controls** | Top-right on-screen buttons to pause simulation or toggle audio on touch devices |

---

## 🧟 Hostile Classifications

As you progress through waves, Sector 09 spawns three distinct mutations of the infected:

| **Class** | **Appearance** | **Health** | **Speed** | **Damage** | **Tactical Threat** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Shambler** | Putrid green-gray skin, dark coat | `100 HP` | Moderate | `14 DMG` | Standard fodder; lethal in large numbers. Eliminated in 1 headshot. |
| **Crimson Runner** *(Wave 2+)* | Flayed red skin, smaller frame | `65 HP` | **High** | `14 DMG` | Sprints rapidly to close distance. Prioritize before reloading. |
| **Armored Brute** *(Wave 3+)* | Massive scale, dark crimson armor | `210 HP` | Slow | `24 DMG` | Absorbs multiple headshots and deals heavy melee damage. Keep distance. |

### Scoring System
* **Standard Elimination:** `+100 PTS`
* **Headshot Elimination:** `+150 PTS`

---

## 🛠️ Technical Architecture & Optimizations

* **3D Rendering (`Three.js r128`):** Uses `THREE.PerspectiveCamera` with `YXZ` Euler rotation order for gimbal-lock-free FPS aiming, `THREE.FogExp2` for depth culling, and `THREE.Raycaster` for instant hitscan ballistics.
* **Zero-Allocation Math Pipeline:** Eliminates per-frame heap allocations by utilizing reusable scratch vectors (`_forward`, `_right`, `_moveDir`, `_toPlayer`, `_knockDir`, `_muzzlePos`, `_tracerEnd`) and pre-allocated raycast candidate arrays.
* **GPU Memory Disposal Lifecycle:** Zombie meshes share 6 core box geometries across classes. When zombies or particles expire, materials (`skinMat`, `clothesMat`, particle materials) are explicitly destroyed via `.dispose()`, preventing GPU VRAM exhaustion.
* **Procedural Textures (`HTML5 Canvas`):** Floor asphalt grids, surface noise speckles, and industrial hazard pillars are drawn onto offscreen 2D canvases on initialization and converted via `THREE.CanvasTexture`.
* **Sound Synthesis (`Web Audio API`):**
  * *Ambient Drone:* Dual detuned sawtooth/triangle oscillators (`46.25 Hz` and `49.0 Hz`) routed through a low-pass BiquadFilter modulated by a `0.18 Hz` LFO.
  * *Gunshots:* Exponentially decaying white-noise buffers paired with a pitch-dropping sine wave kick (`190 Hz` $\rightarrow$ `38 Hz`).
  * *Zombie Groans:* Bandpass-filtered sawtooth waves with randomized base frequencies and pitch envelopes.
  * *Health Pickup Chime:* Multi-tone arpeggiated sine harmonics with high Q resonance.

---

## 📄 License

Distributed under the **MIT License**.