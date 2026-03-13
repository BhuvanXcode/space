# VOID BLASTER

A retro-futuristic space shooter game built entirely in a single HTML file using vanilla JavaScript and the HTML5 Canvas API.

## How to Play

Open `index.html` in any modern web browser — no build step or server required.

### Controls

| Action | Input |
|--------|-------|
| Move left / right | `←` `→` or `A` `D` |
| Move up / down | `↑` `↓` or `W` `S` |
| Fire | `Space` or **click** on the canvas |
| Start / restart | `Enter` or click the on-screen button |

### Objective

Survive waves of increasingly difficult enemies, destroy them all to advance to the next wave, and rack up the highest score possible. You start with **3 lives**.

## Game Mechanics

- **Waves** – enemies spawn in rows; count scales with the wave number (up to 20 per wave).
- **Boss enemies** – appear from wave 3 onward with multi-shot attacks and a large health pool.
- **Combo system** – consecutive kills within a short window multiply into a combo counter displayed on screen.
- **Power-ups** – destroyed enemies have a 12% chance of dropping a power-up:
  - 🛡 **Shield** – absorbs one hit.
- **Triple shot** – from wave 4 onward the player automatically fires three bullets per shot.
- **High score** – persisted in `localStorage` (`vb_hs` key).

## Code Structure

Everything lives in a single **`index.html`** file:

| Section | Lines | Description |
|---------|-------|-------------|
| **CSS** | 7–239 | Neon-themed styling, HUD, overlay screens, CRT scanline effect, custom crosshair cursor |
| **HTML** | 241–287 | Starfield canvas, game canvas, HUD elements, start & game-over overlay screens |
| **Starfield** | 289–311 | Parallax background star animation on a full-viewport canvas |
| **Cursor** | 313–318 | Custom crosshair that follows the mouse |
| **Game state & controls** | 320–355 | Canvas setup, state variables, keyboard/mouse listeners, player object, `resetGame()` |
| **HUD** | 357–369 | `updateHUD()` – syncs score, wave, and lives display |
| **Wave spawning** | 371–407 | `spawnWave()` – generates enemy formations with boss logic |
| **Firing** | 409–419 | `fireBullet()` – rate-limited; adds triple shot at wave 4+ |
| **Particles** | 421–435 | `spawnExplosion()` – burst of colored particles on hit/death |
| **Draw helpers** | 437–487 | `drawShip()` – wireframe ship renderer; `drawHealthBar()` – per-enemy HP bar |
| **Game loop** | 489–689 | `gameLoop()` – movement, AI shooting, collision detection, rendering, combo display |
| **End / Start** | 692–714 | `endGame()` / `startGame()` – screen transitions, high-score check |

## Visual Effects

- **Starfield** – 200 drifting, twinkling stars on a separate full-screen canvas.
- **CRT scanlines** – a CSS overlay for retro monitor aesthetics.
- **Neon glow** – `box-shadow` and `text-shadow` in cyan, pink, yellow, and green.
- **Particle explosions** – physics-based particles with gravity and decay on every hit and kill.
- **Engine glow** – randomized orange circle beneath the player ship.

## Technologies

- HTML5 Canvas (`2d` context)
- Vanilla JavaScript (no frameworks or dependencies)
- CSS custom properties, `backdrop-filter`, Google Fonts (Orbitron, Share Tech Mono)
