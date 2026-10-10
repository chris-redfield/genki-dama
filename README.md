# World Orb

Two-phase browser minigame prototype: gather energy from the whole planet while surviving the enemy's attacks, then read his body and land the orb on him.

## Run it

Open it through a web server, not by double-clicking `index.html`. Browsers block the pixel reads the game needs (sprite slicing, green keying, disintegration) on `file://` pages.

```
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Assets

Everything lives in `assets/`. The page loads these by exact file name:

| File | What it is |
| --- | --- |
| `hero-front.png` | Hero 3x3 sheet, transparent background. Rows: eye level, camera below, camera above. Columns: neutral, looking up, strained. Used for hit close-ups and overhead cutaways. |
| `hero-back.png` | Hero back view, 3 poses in a row: steady, straining, hit. Green or transparent background (green is keyed out in the browser). Used in phase 1. |
| `enemy-0.webp` to `enemy-5.webp` | Enemy poses: idle, lean right, lean left, crouch, charging ki, shielding from light. |
| `bg-gathering.jpg` | Phase 1 landscape. |
| `bg-aftermath.jpg` | Crater scene for the miss ending and result screens. |
| `ground.jpg` | Tileable ground texture under the aiming grid. |
| `planet.jpg` | Planet seen from orbit, cropped to the globe. Effects target Brazil. |

If a hero file is missing, the game falls back to a placeholder hero and says so in Test toggles.

## Test toggles

The panel at the top left switches mechanics and camera options: defense mode, grid shape, aiming view, throw camera, hit effect, miss ending, opening shot. It also has shortcuts to jump straight to phase 2 with a small, cross or full orb.
