# TRUMP DOOM

A single-level, retro, software-rendered Doom-style FPS where the demon horde is an
angry army of fat yellow-haired Donald Trumps in suits. Pure JavaScript in one
`index.html` — zero dependencies, zero asset files. Everything (textures, sprites,
sounds, music) is generated procedurally at startup.

A silly parody. Not affiliated with or endorsed by any real person.

## Run it

```bash
node server.js          # then open http://localhost:8080
```

(or just open `index.html` directly in a browser — `PORT=9000 node server.js` to change the port)

## Controls (classic Doom)

| Action | Keys |
|---|---|
| Move / strafe | `W A S D` or arrow keys |
| Turn | ← → |
| Fire | `Ctrl` / `Space` |
| Run | `Shift` |
| Use doors & switches | `E` or `Enter` |
| Weapons | `1`–`5` (fist, pistol, shotgun, chaingun, rocket launcher) |
| Automap | `Tab` |
| Pause / menu | `Esc` |

## The level

One scary indoor dungeon: start chamber → armory → great pillar hall → prison cells →
locked exit chamber. Find the **red keycard** in the key vault, open the locked door,
flip the **exit switch**. There is a secret wall hiding the rocket launcher. Some Trumps
fire back golden bolts of anger; the rest charge with fists. End-of-level tally shows
kills / items / secrets % and time, Doom-style.

## Options

Splash screen → `O`: master/music/SFX volume, mute, brightness, render resolution
(320×200 / 480×300 / 640×400), FOV, head-bob, crosshair, FPS counter.
Settings persist in `localStorage`.