# AGENTS.md

## Overview
Vanilla HTML5 Canvas Asteroids clone. **No dependencies, no bundler, no build/test/lint/typecheck tooling** — do not add any or assume it exists.

- `index.html` — page shell, defines the `<canvas id="canvas" width="800" height="600">` and loads `game.js`.
- `game.js` — entire game in one file: classes `Bullet`, `Asteroid`, `Ship`, `Particle`; global game state; `update(dt)` / `draw()`; `requestAnimationFrame` loop.
- `favicon.svg` — icon.
- `README.md` — user-facing docs (Spanish).

## Run
Open `index.html` directly, or `npx serve .` then visit `http://localhost:3000`. There is no test command; verify changes by playing in a browser.

## Conventions & gotchas
- Plain scripts sharing globals (no `import`/`export`, no modules). `game.js` runs `document.getElementById('canvas')` at top level, so it must stay loaded at the end of `<body>`.
- Canvas size `800x600` is hardcoded both in `index.html` and as `W`/`H` in `game.js`; keep them in sync.
- UI text, HUD labels, and README are in Spanish; code comments use `// ── Section ──` separators.
- Space wraps toroidally via `wrap()`. Note: collision `dist()` does **not** account for wrap-around (objects near opposite edges won't collide) — preserve unless intentionally fixing.
- `pressed(code)` consumes the `justPressed` flag; call it once per frame (currently only `Space`).
- No comments are added in code by convention except section headers.

## Known README drift
`README.md` claims power-ups and a "estrella fugaz" asteroid type; neither exists in `game.js`. Trust the code, and update or correct the README if you implement them.
