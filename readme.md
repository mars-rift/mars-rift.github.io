# 🩸 RUN FROM THE DEAD 🩸

### *Sector 09 Quarantine Breach — 3D Neon Survival FPS*

---

## ⚡ Overview

**RUN FROM THE DEAD** drops you into **Sector 09**, a pitch-black industrial quarantine zone lit only by flickering crimson neon and a looming blood moon. Armed with an **NX-9 Pulse Carbine**, you must survive infinitely scaling waves of the infected.

Designed specifically for effortless static hosting, the entire game—including 3D models, surface textures, particle systems, and multi-layered sound effects—is generated procedurally at runtime using JavaScript, **Three.js (r128)**, and the **Web Audio API**.

---

## 🚀 Key Features

* **Red Neon & Black Aesthetic:** Atmospheric exponential fog, CRT scanline overlays, glowing neon hazard structures, and a dynamic blood moon.
* **Five Distinct Sector 09 Combat Arenas & Map Modes:** Battle across five procedural next-gen levels—**Map 01: Containment Grid**, **Map 02: Crimson Reactor**, **Map 03: Obsidian Sanctum**, **Map 04: Neon Nexus** *(Cyberpunk Megacity Data-Core)*, and **Map 05: Necro Ossuary** *(Dark Bio-Horror Catacombs)*. Play in **Wave Cycle Mode** (`Wave 1 → 2 → 3 → 4 → 5`, repeating) or enable **Random Map Mode** for unpredictable arena rotations every wave.
* **Tactile FPS Combat:** Features a 3D carbine viewmodel with procedural weapon sway, sprint tilting, recoil kickback, dynamic muzzle flash lighting, bullet tracers, auto-reload, hold-to-fire full-auto trigger, and two-stage reload animations.
* **Locational Hit Detection:** Raycasted shooting mechanics distinguish between body shots (`40 DMG`), headshots (`110 DMG`–`120 DMG` + golden hitmarker), and exposed glowing reactor core weakpoints on Armored Brutes (`110 DMG`).
* **Tactical Resupply Intermission:** A 3.5-second tactical breather occurs between waves, giving players a critical window to reload, grab health jewels, and reposition.
* **Directional Threat Awareness:** An intuitive curved neon threat arc flashes around your reticle pointing toward the angle of any attacking hostiles.
* **Physical Horde Collision:** Tight entity collision mechanics prevent zombies from clipping through the camera and allow hostiles to physically corner and body-block the player.
* **100% Procedural Audio Engine:** Built-in Web Audio API synthesizer generates gunshots, mechanical reloads, empty-clip clicks, guttural zombie groans, flesh impacts, and a dark dissonant horror drone without loading a single `.mp3` or `.wav` file.
* **Multi-Class Horde AI:** Zombies dynamically path toward the player, navigate around arena pillars, avoid stacking on each other, and scale in speed and numbers with each wave.
* **Poise & Stagger Mechanics:** Standard infected stagger under heavy fire, while Armored Brutes possess heavy frontal poise and stagger cooldowns, preventing continuous fire stagger-locks.
* **Obstacle-Safe Spawning:** Intelligent coordinate rejection algorithms and fallback nodes prevent zombies and pick-ups from ever embedding inside arena pillars or spawning directly on the player.
* **Neon Diamond Health Jewels:** From Wave 3 onward, rare crystalline health jewels have a 65% chance to appear per level. Projecting an ethereal cyan vertical beacon and gyroscopic orbital rings, collecting a jewel replenishes `+50%` Vital Integrity accompanied by harmonic chimes and radiant sparkle bursts.
* **High-Refresh-Rate Frame-Rate-Independent Engine:** Exponential `dt` smoothing (`damp`), static arena and per-bone enemy geometry batching, dedicated dual-pass first-person viewmodel rendering, pre-allocated object pools, and shared GPU material registries keep combat responsive and tear-free on high-refresh-rate displays (`120Hz`–`240Hz+`).
* **Configurable Tactical & Render Settings:** Real-time settings modal supporting Render Quality presets (`Ultra`, `High`, `Performance`) with adaptive DPR and texture anisotropy scaling, optional live Performance Telemetry HUD (`FPS`, frame render `ms`, and Draw Calls `DC`), mouse look sensitivity, Y-axis inversion, touch sensitivity/aim assist/auto-fire, arena map rotation mode, and master audio synth volume.

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

As you progress through waves, Sector 09 deploys five distinct hostile classes—including a cybernetic Hunter Droid strictly native to **Map 04: Neon Nexus**:

| **Class** | **Appearance** | **Health** | **Speed** | **Damage** | **Tactical Threat & Vulnerability** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Shambler Droid** | Menacing combat automaton in electric-veined gunmetal droid armor, single blazing neon-red Cyclops eye, glowing electric-red heart encased in an armored chest cage, twin shock-cleaver & pincer gauntlet | `100 HP` | Moderate | `14 DMG` | **Tactical Combat AI:** Uses predictive intercept pathing, coordinated squad pincer flanking, smart pillar bypass steering, and crosshair micro-jukes while keeping classic Shambler stats. Eliminated in 1 headshot (`110 DMG`). |
| **Crimson Runner** *(Wave 2+)* | Flayed red sinew, raptor posture, forearm bone-scythes | `65 HP` | **High** | `14 DMG` | Predatory zig-zag sprint & sudden lunge. Prioritize before reloading. Eliminated in 1 headshot (`110 DMG`). |
| **Phantom Stalker** *(Wave 2+)* | Charred-obsidian Runner mutant, curved predator whip-horns, dorsal plasma quills, glowing violet mantis-scythes | `80 HP` | **Fast / Flanking** | `18 DMG` | **Phase-Shroud Cloak & Flanking Ambush:** Circles your flank while semi-translucent, telegraphs a shrieking **Phase-Leap**, and sidestep-dodges non-lethal body shots. Eliminated in 1 headshot (`110 DMG`). |
| **Armored Brute** *(Wave 3+)* | Massive scale, dark armor, glowing reactor core | `240 HP` | Heavy / Berserk | `26 DMG` | Frontal chestplate absorbs body damage (`26 DMG`). Heavy poise resists regular staggers. Aim for the head (`120 DMG`) or exposed reactor core (`110 DMG`). Enrages into a berserk sprint when damaged below 50% HP. |
| **Nexus Hunter Droid** *(Native to Map 04: Neon Nexus)* | Midnight obsidian hex-chassis, cyan anti-grav hover ring, server-blade dorsal fins, sweeping optic visor & rail-plasma cannon | `130 HP` | Hover-Strafe | `10 DMG` *(Plasma)* / `16 DMG` *(Blade)* | **Exclusive to Map 04: Neon Nexus.** Actively flanks around cover pillars, locks on with a holographic laser telegraph to fire dodgeable neon plasma bursts, and rushes with an energy arc-blade at close range. Armored chassis (`32 DMG` body); aim for Sensor Head or Geodesic Chest Core (`110 DMG`). |

### Scoring System
* **Shambler Droid:** `+100 PTS` (Headshot: `+150 PTS`)
* **Crimson Runner:** `+120 PTS` (Headshot: `+180 PTS`)
* **Phantom Stalker:** `+160 PTS` (Headshot: `+230 PTS`)
* **Nexus Hunter Droid:** `+220 PTS` (Headshot / Core Crit: `+300 PTS`)
* **Armored Brute:** `+250 PTS` (Headshot: `+350 PTS`)

---

## 🗺️ Sector 09 Combat Arenas & Map Modes

Players can choose between two arena rotation modes on the **Title Screen**, **Pause Menu**, or **Settings Modal**:
* **Wave Cycle Mode (Default):** Automatically cycles through all five Sector 09 arenas in order (`Wave 1 = Map 01`, `Wave 2 = Map 02`, `Wave 3 = Map 03`, `Wave 4 = Map 04`, `Wave 5 = Map 05`, `Wave 6 = Map 01`, etc.).
* **Random Map Mode:** Selects a randomized combat arena for each wave, ensuring fresh tactical sightlines and cover layouts throughout your run.

| **Arena** | **Architecture & Landmarks** | **Tactical Flow** |
| :--- | :--- | :--- |
| **Map 01: Containment Grid** | Symmetrical 20-pillar octagonal hazard matrix with crimson torus rings and grid floor plating. | Balanced sightlines and evenly spaced radial kiting lanes. |
| **Map 02: Crimson Reactor** | Overloaded suspended plasma core with rotating gyroscopic rings, 4 hexagonal plasma reactor pylons, 4 heavy cryo-coolant silos, overhead gantry struts, and capacitor towers. | Heavy central reactor cover and wide outer coolant corridors. |
| **Map 03: Obsidian Sanctum** | Levitating inverted obsidian spire, 4 glowing crimson bio-stasis vats, 4 tapered obsidian monoliths with hovering crystals, 4 cardinal neon quarantine gate archways, and sentinel spires. | High-contrast archway chokepoints and diagonal monolith sightline breaks. |
| **Map 04: Neon Nexus** | Cyberpunk megacity data-core with geodesic holographic neural crystal, orbiting HUD telemetry screens, 4 brutalist mainframe blade towers, 4 neon Torii overpass portals with holographic billboards, quantum server spires, and megabuilding skyline silhouettes. | Fast-paced cyber-alleyway portals and angled mainframe cover fins. |
| **Map 05: Necro Ossuary** | Dark bio-horror square catacomb labyrinth featuring a walkable square sacrificial blood-pit grate, overhead suspended square iron-maiden cage with cubic bio-heart, 4 square morgue vault towers linked by overhead gantry bridges, 8 orthogonal square charnel specimen cages, 4 cardinal slaughterhouse guillotine/bone-gate archways, and 12 stepped square crematorium ziggurats. | Oppressive dark-horror fog, rectilinear cross-corridor alleys, and fanged guillotine gate chokepoints. |

---

## 🛠️ Technical Architecture & Optimizations

* **3D Rendering (`Three.js r128`):** Uses `THREE.PerspectiveCamera` with `YXZ` Euler rotation order for gimbal-lock-free FPS aiming, deep `THREE.FogExp2` with local crimson `playerLight` and per-map `arenaBeacons` for pitch-black neon horror atmosphere, and a dual-pass isolated viewmodel camera (`viewmodelScene` / `viewmodelCamera`) to eliminate weapon clipping.
* **Draw-Call Batching & Shader Pre-Warming:** `batchStaticMapGroup()` merges static arena geometry per material across all five maps, `bakeRigidPart()` consolidates rigid enemy limb sub-parts onto shared bone pivots, `ENEMY_MATS` shares opaque GPU materials (with depth-correct `transparent: false, depthWrite: true` outside Phantom Stalker cloaking), and `prewarmShaders()` pre-compiles all maps, enemy archetypes, and the viewmodel pass at startup.
* **Pre-Allocated Pooling & Frame-Rate-Independent Simulation:** Pre-allocated particle, tracer, and Hunter Droid bolt pools combine with reusable scratch math vectors, sphere-culled raycasting (`performWeaponRaycast`), post-flocking player separation, continuous swept projectile impact checks (`segmentCircleHitT`), and exponential `damp()` integration.
* **Persistent Scene Lighting Architecture:** The pickup point light (`persistentJewelLight`) remains permanently attached with `visible = true` and zero-cost intensity updates, eliminating WebGL shader recompilation hitches during jewel spawn and collection.
* **Safe Storage & Audio Lifecycle Resilience:** Encapsulated `safeStorage` wrappers guard `localStorage` in sandboxed iframes, while `visibilitychange` handlers automatically suspend Web Audio and pause combat safely when tabs lose focus.
* **Sound Synthesis (`Web Audio API`):**
  * *Ambient Drone:* Dual detuned sawtooth/triangle oscillators (`46.25 Hz` and `49.0 Hz`) routed through a low-pass BiquadFilter modulated by a `0.18 Hz` LFO.
  * *Gunshots:* Exponentially decaying white-noise buffers paired with a pitch-dropping sine wave kick (`190 Hz` $\rightarrow$ `38 Hz`).
  * *Zombie Groans:* Bandpass-filtered sawtooth waves with randomized base frequencies and pitch envelopes.
  * *Health Pickup Chime:* Multi-tone arpeggiated sine harmonics with high Q resonance.

---

## 📄 License

Distributed under the **MIT License**.