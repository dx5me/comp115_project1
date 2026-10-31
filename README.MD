# Train Project: Night Train vs. Broken Bridge

**COMP 115 – Learn to Code | Project 1: Original Turtle Drawing**
Capilano University · Fall 2026 · Deepak Singh

A night scene drawn entirely with Python's `turtle` module: a steam train races along the tracks toward a bridge with a missing section over a foggy canyon, its headlight cutting through the dark. A red warning lamp glows right before the gap, and debris is already falling into the fog below.

![Train Project screenshot](screenshot.png)

---

## How to Run

1. Make sure Python 3 is installed (`turtle` comes with Python, so there is nothing else to install).
2. Download or clone this repository.
3. Run the script:

```bash
python train_project.py
```

An 800 × 600 window opens and the full scene appears. Close the window to end the program.

> **Want to watch it draw?** In `setup_screen()`, change `zx.tracer(0)` to `zx.tracer(1)`. The turtle will then draw the scene piece by piece instead of all at once.

---

## What's in the Scene

The scene is drawn **back to front**, so closer objects cover the ones behind them:

| Layer | Functions |
|---|---|
| Sky | `draw_stars`, `draw_moon`, `draw_mountains` |
| Canyon | `draw_canyon_back`, `draw_river` |
| Light | `draw_headlight_beam` |
| Bridge structure | `draw_bridge_supports`, `draw_broken_rails` |
| Fog and falling debris | `draw_fog_row` (back and front rows), `draw_debris` |
| Ground | `draw_cliffs`, `draw_rock_layers`, `draw_grass` |
| Bridge and track | `draw_bridge_deck`, `draw_tracks`, `draw_signal_lamp` |
| Train | `draw_smoke`, `draw_speed_lines`, `draw_passenger_car`, `draw_locomotive` |

---

## How the Code Is Organized

**Reusable shape helpers.** Every object in the scene is built from a few basic helpers:

- `draw_polygon(points, color)` draws a filled shape from a list of `(x, y)` points
- `draw_rectangle(x, y, width, height, color)` draws a rectangle from its top-left corner
- `draw_circle(x, y, radius, color, outline_color=None)` draws a circle from its **centre**, with an optional outline
- `draw_line(...)` draws a straight line with a set colour and thickness

**Scene functions.** Each part of the picture (moon, cliffs, locomotive, and so on) has its own function that uses the helpers above.

**`draw_scene()`** calls the scene functions in back-to-front order, and **`main()`** sets up the screen and draws the scene.

**Shared constants.** `HALF_W`, `HALF_H`, and `RAIL_Y` are stored once at the top, so the edges of the window and the rail height stay consistent everywhere. For example, every wheel sits exactly on the rail because its centre is calculated from `RAIL_Y`.

---

## Python Concepts Used

- **Turtle graphics:** `goto`, `penup` / `pendown`, `begin_fill` / `end_fill`, `circle`, `setheading`, `tracer` / `update`
- **Functions** with parameters and default values (`outline_color=None`)
- **Lists and tuples** for shape points and repeated objects (smoke puffs, windows, wheels)
- **`for` loops**, including `range()` with a step to space the railway ties evenly
- **Selection (`if` / `else`)** to choose between an outlined and a plain circle
- **Modules:** `turtle`, `random`, `math`
- **`random.seed(7)`** so the stars, fog, and debris are placed the same way every time the program runs

---

## Files

| File | Description |
|---|---|
| `train_project.py` | The full program |
| `screenshot.png` | The finished scene |
| `README.md` | This file |
