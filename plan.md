# Plan: "TRUMP DOOM" — Single-Level JS Doom Clone

## Goal
A single-level, retro, voxel/pixel-style 3D Doom clone (Wolfenstein-3D-style raycaster) starring an angry army of fat yellow-haired Trumps in suits. Pure JavaScript, zero dependencies, runnable via Node.js (tiny static server) or by opening the HTML file directly.

## Deliverables (3 files)
1. **`index.html`** — the entire game in one self-contained file (inline CSS + JS, ~2500–3500 lines). No build step, no npm deps.
2. **`server.js`** — ~20-line Node static file server (`node server.js` → http://localhost:8080).
3. **`README.md`** — how to run, controls summary.

## Technical approach

### Renderer (the "voxel" retro look)
- Classic **DDA raycasting engine** on a low-res internal canvas (320×200-ish, configurable "resolution scale" in vision options), upscaled with `image-rendering: pixelated` for chunky retro pixels.
- Walls: procedurally generated dungeon textures (stone brick, mossy brick, tech panels, door, exit switch) drawn to offscreen canvases at load — no external image assets.
- Floor/ceiling casting for depth, dark scary dungeon palette with distance fog/shading.
- Billboards: sprite-based enemies/items with depth-buffer occlusion (per-column zbuffer from the raycaster).

### Enemies — the Trump army
- Procedurally drawn pixel-art sprites: fat bodies, dark suits, red ties, yellow swoosh hair, angry face. Multiple frames: idle, walk (2), fire, hit, death (3-stage gib).
- Two types:
  - **Shooter Trumps** — stop at range, telegraph, fire projectile bolts (dodgeable).
  - **Melee/charger Trumps** — rush and scratch (can't fire back).
- Simple Doom-like AI: line-of-sight wake-up, chase with wall sliding, attack cooldowns, pain states.

### Weapons (Doom arsenal, punchy)
- Fist, Pistol, Shotgun, Chaingun, Rocket Launcher (self-damage splash). Ammo types: bullets/shells/rockets/cells pickups. Muzzle flash lightens the screen briefly.

### Level (single level)
- Hand-authored tile map string (~48×48) — dungeon rooms, corridors, pillar halls, a locked door needing a **red keycard**, secret wall, ammo/health/armor pickups, exit switch → victory screen. Monster/item placement in the map legend.

### Controls (as per real Doom)
- `WASD`/arrows move & strafe, mouse turn (pointer lock) + click fire, `Ctrl`/`Space` fire, `Shift` run, `E`/`Enter` use (doors/switches), `1–5` weapon select, `Tab` automap overlay, `Esc` menu. In-game help panel on `F1`.

### Splash screen & menus
- Title splash: big pixel-logo "TRUMP DOOM", pulsing "PRESS ENTER", background render of the level with marching Trumps (demo camera).
- **Options menu**:
  - Sound: master/SFX/music volume sliders, mute.
  - Vision: brightness (fog distance), render resolution scale, FOV slider, head-bob toggle, crosshair toggle.
  - Settings persist via `localStorage` (wrapped in try/catch).
- Pause menu, death screen, victory screen, level stats (kills/items/secrets %, time — Doom-style tally).

### Sound (WebAudio, fully procedural — zero audio files)
- Pistol/shotgun/chaingun/rocket noise-burst synth, enemy alert "You're fired!" style garble (pitch-modulated oscillator blips), pain/death grunts, door open, pickup blip, player pain, explosion.
- Dungeon ambient drone + simple driving music loop (square-wave arpeggio, Doom E1M1-adjacent but original).

### HUD
- Doom-style status bar: HEALTH / ARMOR / AMMO / weapon number / keys, plus a pixel-art Trump-face mugshot that reacts to health and grimaces when hit. Damage red flash, item pickup yellow flash.

## File/section layout inside `index.html`
1. CSS + canvas setup
2. Config & settings (localStorage)
3. Input handling (keyboard/mouse/pointer lock)
4. Procedural texture & sprite atlas generation
5. Map data & world setup (walls, doors, things)
6. Player (movement, collision, weapon state machine)
7. Enemies (AI, combat) & projectiles
8. Combat (hitscan/splash, damage, gore particles)
9. Renderer (raycast walls, floor/ceil, sprite billboards, particles, automap)
10. WebAudio sound engine & music sequencer
11. HUD & UI (splash/menus/death/victory/stats)
12. Game loop & state machine (splash → game → pause → dead → won)

## Verification
- `node server.js`, open browser, play through: shoot both enemy types, grab key, open door, hit exit, check menus/options persist, verify sound on Chrome & Firefox.
- Sanity-check no console errors; run a quick syntax check with `node --check` on extracted JS if useful.