# Copilot Instructions

## Project overview
This is a 2D water cup simulation rendered on an HTML5 Canvas using planck.js (a JavaScript port of Box2D) for rigid-body physics.

## Architecture
- **Single-file app**: all HTML, CSS, and JavaScript live in `index.html` with inline `<style>` and `<script>` blocks.
- No build tools, bundlers, or npm packages — the only external dependency is planck.js loaded via CDN.

## Physics
- **Engine**: [planck.js 1.0.5](https://cdn.jsdelivr.net/npm/planck@1.0.5/dist/planck.min.js)
- **Timestep**: fixed at 60 fps (`FIXED_DT = 1/60`)
- **Gravity**: `Vec2(0, -10)` (world Y-axis points up)
- **Cup**: a single `static` body with three `Edge` fixtures (flat bottom + two slightly flared walls)
- **Water particles**: small `dynamic` `Circle` bodies with low restitution and linear damping to approximate fluid behaviour

## Coordinate system
- `SCALE = 80` px/m — multiply world metres by this to get screen pixels
- `OX = W * 0.5`, `OY = H * 0.62` — screen origin for world `(0, 0)`
- Y-axis is **flipped**: `screenY = OY - worldY * SCALE`
- Helper functions: `ws(x, y)` converts world → screen; `sw(cx, cy)` converts screen → world

## Controls
- **← / → arrow keys** or **horizontal swipe** on the canvas to tilt the cup
- **Click / tap** on the canvas to spawn a small cluster of new water particles at that position
