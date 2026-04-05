# Checkbox Automata

A browser-based visual cellular automaton implemented with SVG rectangles.

## What It Does

Renders a 49x49 grid of SVG rectangles. When a cell is clicked, all cells at a Manhattan distance equal to a Fibonacci number from the clicked cell are incremented by one state (cycling through 10 states, 0–9). Each state maps to a grayscale color from black to white.

## Running

Open `index.html` directly in a browser, or serve with a local HTTP server:

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Project Structure

- `index.html` — entire application (HTML, CSS, JS in one file)

## Tech Stack

- Vanilla JavaScript (ES6+), no dependencies, no build step

## Core Algorithm

1. Pre-compute Fibonacci numbers up to `field_width + field_height` (98).
2. On cell click, compute Manhattan distance `|dx| + |dy|` from the clicked cell to every other cell.
3. Increment (mod 10) cells whose distance is a Fibonacci number; update their fill color from a 10-step grayscale palette.

## Controls

- **Grid** checkbox — toggles a visible border around each cell.
- **HS** (Horizontal Symmetry) checkbox — mirrors every click across the vertical center line (x=24).
- **VS** (Vertical Symmetry) checkbox — mirrors every click across the horizontal center line (y=24).
- HS and VS can be combined for 4-way symmetry.
- **Cycle** button — increments every cell's state by one (global step, no distance filtering).
- **PNG** button — downloads the current grid as a 49x49 PNG image.
- **Palette** dropdown — switches between grayscale, lime, and pink color palettes.
