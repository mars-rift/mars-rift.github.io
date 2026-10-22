# 🩸 RUN FROM THE DEAD 🩸

### *Sector 09 Quarantine Breach — 3D Neon Survival FPS*

---

## ⚡ Overview

**RUN FROM THE DEAD** drops you into **Sector 09**, a pitch-black industrial quarantine zone lit only by flickering crimson neon and a looming blood moon. Armed with an **NX-9 Pulse Carbine**, you must survive infinitely scaling waves of the infected.

Designed specifically for effortless static hosting, the entire game—including 3D models, surface textures, particle systems, and multi-layered sound effects—is generated procedurally at runtime using JavaScript, **Three.js (r128)**, and the **Web Audio API**.

---

## 🚀 Key Features

* **Red Neon & Black Aesthetic:** Atmospheric exponential fog, CRT scanline overlays, glowing neon hazard pillars, and a dynamic blood moon.
* **Tactile FPS Combat:** Features a 3D carbine viewmodel with procedural weapon sway, sprint tilting, recoil kickback, dynamic muzzle flash lighting, bullet tracers, auto-reload, hold-to-fire full-auto trigger, and two-stage reload animations.
* **Locational Hit Detection:** Raycasted shooting mechanics distinguish between body shots (`40 DMG`), headshots (`110 DMG`–`120 DMG` + golden hitmarker), and exposed glowing reactor core weakpoints on Armored Brutes (`110 DMG`).
* **Tactical Resupply Intermission:** A 3.5-second tactical breather occurs between waves, giving players a critical window to reload, grab health jewels, and reposition.
* **Directional Threat Awareness:** An intuitive curved neon threat arc flashes around your reticle pointing toward the angle of any attacking hostiles.
* **Physical Horde Collision:** Tight entity collision mechanics prevent zombies from clipping through the camera and allow hostiles to physically corner and body-block the player.
* **100% Procedural Audio Engine:** Built-in Web Audio API synthesizer generates gunshots, mechanical reloads, empty-clip clicks, guttural zombie groans, flesh impacts, and a dark dissonant horror drone without loading a single `.mp3` or `.wav` file.
* **Multi-Class Horde AI:** Zombies dynamically path toward the player, navigate around arena pillars, avoid stacking on each other, and scale in speed and numbers with each wave.
* **Poise & Stagger Mechanics:** Standard infected stagger under heavy fire, while Armored Brutes possess heavy frontal poise and stagger cooldowns, preventing continuous fire stagger-locks.
* **Obstacle-Safe Spawning:** Intelligent coordinate rejection algorithms and fallback nodes prevent zombies and pick-ups from ever embedding inside arena pillars or spawning directly on the player.
* **Neon Diamond Health Jewels:** From Wave 3 onward, rare crystalline health jewels have a 50% chance to appear per level. Projecting an ethereal cyan vertical beacon and gyroscopic orbital rings, collecting a jewel replenishes `+50%` Vital Integrity accompanied by harmonic chimes and radiant sparkle bursts.
* **Zero-Allocation 60 FPS Engine:** Pre-allocated particle pools, pooled bullet tracer buffers, pre-created lighting rigs, and reusable scratch vectors prevent memory leaks and garbage collection stutters during prolonged survival.
* **Configurable Tactical Settings:** Real-time settings modal supporting mouse look sensitivity, Y-axis inversion, touch sensitivity, and master audio synth volume.

---

## 🎮 Tactical Controls

### Desktop Controls

| **Input** | **Action** | **Notes** |
| :--- | :--- | :--- |
| **W A S D / Arrows** | **Move / Strafe** | Navigate around neon pillars to break line-of-sight |
| **Mouse** | **Look / Aim** | Uses Pointer Lock API (includes click-and-drag fallback) |
| **Left Mouse Button** | **Shoot Weapon** | Hold down LMB for automatic continuous fire (`15` rounds per mag) |
| **Shift / Space / RMB** | **Tactical Sprint** | Boosts speed while consuming thruster stamina. Configurable in Settings / Briefing |
| **R** | **Reload** | Replenishes magazine from infinite reserve (`1.15s` duration) |
| **M** | **Mute / Unmute** | Toggles audio with live HUD status indicator |
| **ESC** | **Pause / Settings** | Freezes simulation and opens tactical telemetry & settings modal |

### 📱 Mobile, iPad & Tablet Touch Controls

| **Touch Input** | **Action** | **Notes** |
| :--- | :--- | :--- |
| **Virtual Analog Joystick** | **Move & Turn** | Bottom-left thumbstick: push up/down to move forward/backward; tilt left/right to turn view left/right |
| **Screen Touch (Outside Stick)** | **Strafe & Aim** | Touch and slide anywhere outside the joystick: horizontal drag strafes left/right; vertical drag aims pitch up/down |
| **FIRE Button** | **Shoot Weapon** | Tap for precision single shots or hold for rapid continuous pulse fire |
| **SPRINT Button** | **Tactical Sprint** | Tap to engage/disengage Sprint Thrusters on mobile/tablets |
| **RELOAD Button** | **Reload Carbine** | Tap to initiate tactical magazine swap |
| **PAUSE & MUTE Buttons** | **HUD Controls** | Top-right on-screen buttons to pause simulation or toggle audio on touch devices |

---

## 🧟 Hostile Classifications

As you progress through waves, Sector 09 spawns three distinct mutations of the infected:

| **Class** | **Appearance** | **Health** | **Speed** | **Damage** | **Tactical Threat & Vulnerability** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Shambler** | Putrid green-gray skin, dark coat | `100 HP` | Moderate | `14 DMG` | Standard fodder; lethal in swarms. Eliminated in 1 headshot (`110 DMG`). |
| **Crimson Runner** *(Wave 2+)* | Flayed red sinew, raptor posture | `65 HP` | **High** | `14 DMG` | Predatory zig-zag sprint & sudden lunge. Prioritize before reloading. Eliminated in 1 headshot (`110 DMG`). |
| **Armored Brute** *(Wave 3+)* | Massive scale, dark armor, glowing reactor core | `240 HP` | Heavy / Berserk | `26 DMG` | Frontal chestplate absorbs body damage (`26 DMG`). Heavy poise resists regular staggers. Aim for the head (`120 DMG`) or exposed reactor core (`110 DMG`). Enrages into a berserk sprint when damaged below 50% HP. |

### Scoring System
* **Shambler:** `+100 PTS` (Headshot: `+150 PTS`)
* **Crimson Runner:** `+120 PTS` (Headshot: `+180 PTS`)
* **Armored Brute:** `+250 PTS` (Headshot: `+350 PTS`)

---

## 🛠️ Technical Architecture & Optimizations

* **3D Rendering (`Three.js r128`):** Uses `THREE.PerspectiveCamera` with `YXZ` Euler rotation order for gimbal-lock-free FPS aiming, `THREE.FogExp2` for depth culling, and `THREE.Raycaster` for instant hitscan ballistics.
* **Pre-Allocated Object & Buffer Pooling:** Eliminates garbage collection stutters by pooling 80 blood particle meshes, 30 heal sparkle meshes, and 8 reusable bullet tracer buffer geometries.
* **Zero-Allocation Math Pipeline:** Eliminates per-frame heap allocations by utilizing reusable scratch vectors (`_forward`, `_right`, `_moveDir`, `_toPlayer`, `_toPlayerDir`, `_sideDir`, `_knockDir`, `_muzzlePos`, `_tracerEnd`) and pre-allocated raycast candidate arrays.
* **Persistent Scene Lighting Architecture:** The pickup point light remains permanently attached to the scene graph with zero-cost intensity toggles, preventing WebGL shader program recompilation hitching during jewel spawn and collection.
* **Safe Storage Sandbox Resilience:** Encapsulated `safeStorage` helpers wrap all `localStorage` access in safe exception handlers to prevent script termination in sandboxed iframes (e.g. itch.io).
* **Sound Synthesis (`Web Audio API`):**
  * *Ambient Drone:* Dual detuned sawtooth/triangle oscillators (`46.25 Hz` and `49.0 Hz`) routed through a low-pass BiquadFilter modulated by a `0.18 Hz` LFO.
  * *Gunshots:* Exponentially decaying white-noise buffers paired with a pitch-dropping sine wave kick (`190 Hz` $\rightarrow$ `38 Hz`).
  * *Zombie Groans:* Bandpass-filtered sawtooth waves with randomized base frequencies and pitch envelopes.
  * *Health Pickup Chime:* Multi-tone arpeggiated sine harmonics with high Q resonance.

---

## 📄 License

Distributed under the **MIT License**.