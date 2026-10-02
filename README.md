# TRUMP DOOM

A retro, software-rendered Doom-style FPS where the demon horde is an angry army of
fat yellow-haired Donald Trumps — joined by angry JD Vance and Pete Hegseth lookalikes.
Pure JavaScript in one `index.html` — zero dependencies, zero asset files. Everything
(textures, sprites, sounds, music) is generated procedurally at startup.

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

## The enemy

- **Angry Trumps** — the classic: some fire golden bolts of anger, the rest charge with fists.
- **Angry Vances** — slimmer, bearded, tougher (more health).
- **Angry Hegseths** — crew cut, fast, extra-aggressive chargers.

Every level mixes all three.

## The levels

1. **THE DUNGEON** — the original scary indoor dungeon: start chamber → armory → great
   pillar hall → prison cells → locked exit chamber. Find the red keycard in the key
   vault, flip the exit switch. There is a secret wall hiding the rocket launcher.
2. **HAUNTED WOODS** — spooky outdoors at night under a full moon: woods, a graveyard,
   abandoned wooden cabins, wells, a lake with an island (the keycard is on it). Secret
   shed hides the rocket launcher; the big cabin is locked.
3. **TOWER OF POWER** — a glossy, modern open-floor office with city-and-sea views
   through its window walls: reception, open office, canteen, and an executive suite
   on floor 2. Take the elevator pads between floors; find the server-room secret.
4. **SEA OF TRANQUILITY** — the surface of the moon: craters, hills, crashed spaceships
   and a landing base. Grab the keycard from the west crater, reach the lander, and
   fly home. A crashed ship holds a secret chaingun.

End-of-level tally shows kills / items / secrets % and time, Doom-style — then the
next level loads. Clear all four to win.

## Options

Splash screen → `O`: master/music/SFX volume, mute, brightness, render resolution
(320×200 / 480×300 / 640×400), FOV, head-bob, crosshair, FPS counter.
Settings persist in `localStorage`.

## Dev hooks

- `?autostart` — skip the splash
- `?level=N` — start on level N (1–4); combine with `&autostart` or `&walk`
- `?pos=x,y` / `?ang=R` — dev hooks: force spawn position / facing (radians)
- `?walk` — auto-walk smoke test (head-bob verification)
- `?sprites` — enemy-skin sheet overlay (trump/vance/hegseth)
- `?selftest` — in-engine assertions (per-level layout, reachability, combat, doors)
- `?menu=options` / `?menu=help` — open menus for screenshot checks