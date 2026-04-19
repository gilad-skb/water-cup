https://gilad-skb.github.io/water-cup

# 2D Water Cup Simulation

A real-time 2D water cup simulation built with [planck.js](https://piqnt.com/planck.js) (a JavaScript port of Box2D) rendered on an HTML5 Canvas.

## How to Run

Open `index.html` directly in any modern browser — no build tools, no server, no dependencies to install.

```
open index.html   # macOS
start index.html  # Windows
xdg-open index.html  # Linux
```

## Controls

| Input | Effect |
|-------|--------|
| **← Left arrow** | Tilt cup to the left |
| **→ Right arrow** | Tilt cup to the right |
| **Click** on canvas | Add more water particles |

## How It Works

- **Physics engine** — [planck.js 1.0.5](https://cdn.jsdelivr.net/npm/planck@1.0.5/dist/planck.min.js) loaded via CDN handles rigid-body dynamics, gravity, and collision detection.
- **Cup** — a single static body with three `Edge` fixtures: a flat bottom and two slightly flared walls forming an open-top container.
- **Water** — ~110 small dynamic `Circle` bodies arranged in a hex-packed grid. Each particle has low restitution (0.15) and linear damping to mimic fluid behaviour.
- **Gravity** — `Vec2(0, -10)` (standard Earth-like downward gravity in world space).
- **Tilt** — pressing an arrow key increments the cup body's rotation angle via `setTransform`, causing water to slosh toward the lower side.
- **Add water** — clicking the canvas spawns a small cluster of new particles at the click position.
