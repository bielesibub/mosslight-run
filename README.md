# Mosslight Run

A self-contained HTML5 platformer with eight stages across two worlds, generated pixel art, and original synthesized music. Play straight from a single HTML file—no installation, build step, downloads, or external assets required.

## Play

**[▶ Play](https://html-preview.github.io/?url=https://github.com/bielesibub/mosslight-run/main/mosslight-run.html)**

Download [mosslight-run.html](mosslight-run.html) and open it in a modern browser. Click the game or press **Enter** to start. Choose any stage using **Jump to level → Play level**.

You can also serve the folder locally:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/mosslight-run.html>. Sound starts after a click or keypress; use **SOUND ON/OFF** to toggle it.

## Controls

- **Left / Right** or **A / D** — move.
- **Space**, **Z**, or **Up** — jump; hold for more height. Tap to swim underwater.
- **Shift** — run.
- **Down** or **S** — crouch when powered up; enter a connected pipe while standing on it. Move right into side exits.
- **Left / Right while crouching** — crawl slowly. You stay crouched beneath low ceilings until there is room to stand.
- **X** or **F** — throw fireballs after collecting a fire flower; at most two can be active.
- **P** — pause or resume.
- **R** — restart the current stage.
- **M** — toggle sound.
- **Enter** — start or resume.

Touch controls appear on narrow screens. A first growth pickup makes the player larger; a second becomes a fire flower. Taking damage removes the upgrade.

## Stages

1. **1-1 · Fernway Fields** — ground-level obstacles, coins, enemies, and pipes.
2. **1-2 · Lantern Hollow** — underground passages, bonus rooms, and moving lifts.
3. **1-3 · Treetop Crossing** — elevated platforms and long jumps.
4. **1-4 · Ember Keep** — lava, rotating firebars, and an axe-operated bridge.
5. **2-1 · Sunshell Coast** — a coastal palette and springboard jumps.
6. **2-2 · Coral Current** — swimming, squid hazards, and an exit pipe.
7. **2-3 · Skipper Bridges** — bridge crossings and leaping fish.
8. **2-4 · Cinder Citadel** — lifts, lava jumpers, firebars, and the final keep.

The original underground tune, **“Lanterns Below,”** plays in subterranean areas. Use **♫ CAVE TUNE** to preview it; previewing pauses gameplay.

## Implementation

Everything lives in `mosslight-run.html`: page styles, Canvas 2D rendering, JavaScript game logic, generated tile artwork, embedded level records, and Web Audio synthesis. The simulation uses a fixed timestep, scrolling camera, axis-separated collision steps, moving-platform support, and overlap recovery. Crouching preserves foot position and checks ceiling clearance before standing up.

This is an independent, approximate implementation inspired by classic NES platforming. Worlds 1–2 terrain and enemy records were decoded from a supplied Super Mario Bros. disassembly (`smb.asm`); it is not a 6502 emulator or an exact recreation. The JavaScript implementation, generated artwork, and melodies were created for this project. Level layouts and source-derived records should not be mistaken for original game content. The original disassembly and development reference images are not required to run the game and are not included here. This project is not affiliated with or endorsed by Nintendo.

## Validation

Development checks were run in headless Chrome for stage loading, power-ups, fireballs, swimming, pipes, stage progression, lift alignment and riding, escaping narrow gaps, crouching, and ceiling clearance. The latest crouch update passed 11 focused checks plus 42 gameplay regression checks. Those development scripts are not bundled in this repository.
