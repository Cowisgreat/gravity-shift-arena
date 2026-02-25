# Gravity Shift Arena

A fast-paced arena survival shooter built in **Godot 4.3** demonstrating proficiency across multiple engine systems.

## How to Play

| Control | Action |
|---------|--------|
| WASD / Arrow Keys | Move |
| Mouse | Aim |
| Left Click / Space | Shoot |
| Right Click / Shift | Dash (invincible frames) |
| E | Shift Gravity (cycles Down → Right → Up → Left) |
| R | Restart after Game Over |

Survive waves of enemies, build combos for score multipliers, and manipulate gravity to fling enemies around the arena.

## Features & Proficiency Demonstrated

### Architecture & Design Patterns
- **Autoload Singleton** (`GameManager`) for global state, signals, and cross-scene communication
- **Signal-driven architecture** — decoupled components communicate via signals (score, wave, combo, gravity, death)
- **Scene composition** — player, enemy, bullet as reusable `.tscn` scenes with attached scripts
- **Group system** for entity lookups (`"player"`, `"enemies"`, `"bullets"`)

### Gameplay Systems
- **Wave spawner** with progressive difficulty scaling (enemy count, type variety, spawn rate)
- **4 enemy AI types** with distinct behaviors:
  - **Chaser** — direct pursuit
  - **Shooter** — maintains distance, fires projectiles
  - **Drifter** — sinusoidal movement with gravity susceptibility
  - **Bomber** — fast, low HP, explodes on contact
- **Combo system** — chaining kills multiplies score; resets on timer expiry or taking damage
- **Gravity manipulation** — press E to cycle gravity direction; affects all enemies differently
- **Dash** with i-frames and cooldown

### Physics & Collision
- **5 collision layers** (player, enemies, bullets, walls, pickups) with proper masking
- `CharacterBody2D` with `move_and_slide()` for player and enemies
- `Area2D` projectiles with body-entered detection
- Screen wrapping for enemies, clamping for player

### Visual Polish
- **Screen shake** with intensity decay
- **Slow motion** (bullet time) on gravity shift and player hit
- **Animated HUD** — score punch, wave announcement scale, combo color flash
- **Trail rendering** via `Line2D` with gradient fade on player and bullets
- **GPU particles** for dash effect and enemy death bursts
- **Scrolling background grid** that responds to gravity direction
- **Invincibility flash** (alpha modulation)
- **Tween animations** throughout UI

### Code Quality
- Typed GDScript with `@export`, `@onready`, type hints throughout
- Doc comments on every class
- Clean separation of concerns (input, physics, visuals, state)
- Proper `delta`-based timing
- `process_mode` awareness for pause compatibility

## Setup

1. Open Godot 4.3+
2. Import the project folder
3. Press Play (F5)

No external assets required — all visuals are procedural (polygons, particles, lines).
