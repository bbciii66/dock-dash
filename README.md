# Dock Dash

**Dock Dash** is a single-file, zero-dependency tactical warehouse puzzle game built with vanilla HTML, CSS, inline SVG artwork, and JavaScript.

Navigate an autonomous warehouse forklift across a **6×8 grid**, collect all **5 priority cargo packages** around **8 steel shelving racks**, and reach the **Loading Dock (`F1`)** in the fewest moves and fastest time possible.

---

## Features

- **Zero Dependencies, Single File**: Everything—HTML layout, CSS styling, custom SVG sprites, deterministic board generation, and state-space BFS solver—lives inside [`index.html`](./index.html). No build step, package manager, or network connection required.
- **Deterministic Seeded Board Generator**:
  - Play the classic **`SECTOR-07`** layout (Par 26) or click **New Board** to generate a new verified 6×8 warehouse layout.
  - Share or replay any layout using the editable **Board Seed** input and **Load Seed** button (powered by a deterministic 32-bit FNV-1a hash + `mulberry32` PRNG).
- **Exact Shortest-Route Solver (Par Calculator)**:
  - Every generated board is verified via a Breadth-First Search over the `(col, row, collectedBitmask)` state space (`6 × 8 × 32 = 1,536` states) to guarantee all 5 packages and the loading dock are reachable and to calculate the exact minimum move count (**Par**).
- **Multi-Step Undo System**:
  - Undo moves at any time with the **Undo (`U`)** button or the `U` key—even after winning—to experiment with optimal routing while the shift clock continues monotonically.
- **Multi-Modal Controls**:
  - **Keyboard**: `W` `A` `S` `D` or `Arrow Keys` to move, `U` to undo, `R` to restart the current board.
  - **Mouse / Touch**: On-screen D-pad buttons or click/tap any highlighted adjacent floor tile.

---

## How to Play (Mac, Windows, Linux)

### 1. Run Locally (Offline)
1. Clone or download this repository:
   ```bash
   git clone https://github.com/bbciii66/dock-dash.git
   ```
2. Double-click [`index.html`](./index.html) to open it directly in any modern browser (Chrome, Safari, Edge, Firefox).

### 2. Install as a Desktop Web App
- **macOS (Safari)**: Open `index.html` in Safari and select **File → Add to Dock…**
- **macOS / Windows (Chrome or Edge)**: Open the game over `http://localhost` or GitHub Pages, click the browser menu (**⋮** / **⋯**), and select **Cast, save, and share → Install page as app…** (Chrome) or **Apps → Install this site as an app** (Edge).

---

## Contributing & Customizing

Because the entire project is contained in [`index.html`](./index.html), it is easy to fork, customize, and extend:
- **Grid Size & Obstacle Count**: Adjust `COLS`, `ROWS`, `SHELF_COUNT`, and `TOTAL_PACKAGES` in the `<script>` section.
- **Custom SVG Artwork**: Edit `getShelfSVG()`, `getPackageSVG()`, `getDockSVG()`, and `getForkliftSVG()` to customize the visual theme.
- **New Mechanics**: Fork the repo and experiment with one-way conveyor belts, battery limits, hazard tiles, or multi-level shifts!

---

## License

Released under the [MIT License](./LICENSE) — free and open source for anyone to play, modify, and improve.
