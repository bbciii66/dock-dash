# Dock Dash

**Dock Dash** is a tactical warehouse logistics puzzle game built with vanilla HTML, CSS, inline SVG artwork, and JavaScript.

Navigate an autonomous warehouse forklift across a **6×8 grid**, collect all **5 priority cargo packages** around **8 steel shelving racks**, and reach the **Loading Dock (`F1`)** in the fewest moves and fastest time possible.

Play directly in your browser or install it as an offline Progressive Web App on iPhone, Android, Mac, or Windows.

---

## Live Play

🎮 **[Play Dock Dash Live](https://bbciii66.github.io/dock-dash/)**

---

## Features

- **Zero External Dependencies, Single File**: Everything—HTML layout, CSS styling, custom SVG sprites, deterministic board generation, state-space BFS solver, and touch drag controls—lives inside [`index.html`](./index.html).
- **Mobile & Touch-Optimized**:
  - **Fluid Touch Drag Steering**: Touch anywhere on the warehouse floor and drag to steer the forklift in cardinal directions, supporting continuous drags across multiple cells.
  - **Responsive Portrait Layout**: Prioritizes the warehouse floor with compact telemetry, primary action buttons, and collapsible reference sections.
  - **Multi-Touch & Collision Protection**: Ignores secondary fingers, checks all shelf and boundary collisions without teleporting or skipping, and avoids triggering tile click actions when dragging.
- **Installable Progressive Web App (PWA)**:
  - Web App Manifest (`manifest.json`), service worker (`sw.js`), and custom app icons (`icon-192.png`, `icon-512.png`, `icon.svg`) for instant offline play.
- **Deterministic Seeded Board Generator**:
  - Play the classic **`SECTOR-07`** layout (Par 26) or click **New Board** to generate a new verified 6×8 warehouse layout.
  - Share or replay any layout using the editable **Board Seed** input and **Load Seed** button (powered by a deterministic 32-bit FNV-1a hash + `mulberry32` PRNG).
- **Exact Shortest-Route Solver (Par Calculator)**:
  - Every generated board is verified via a Breadth-First Search over the `(col, row, collectedBitmask)` state space (`6 × 8 × 32 = 1,536` states) to guarantee all 5 packages and the loading dock are reachable and to calculate the exact minimum move count (**Par**).
- **Multi-Step Undo System**:
  - Undo moves at any time with the **Undo (`U`)** button or the `U` key—even after winning—to experiment with optimal routing while the shift clock continues monotonically.
- **Multi-Modal Controls**:
  - **Mobile Touch**: Drag anywhere on the grid, or tap adjacent highlighted step tiles, or use the on-screen D-pad.
  - **Keyboard**: `W` `A` `S` `D` or `Arrow Keys` to move, `U` to undo, `R` to restart the current board.

---

## Install on Phone Home Screen (Offline Play)

### iPhone / iPad (Safari)
1. Open [https://bbciii66.github.io/dock-dash/](https://bbciii66.github.io/dock-dash/) in **Safari**.
2. Tap the **Share** button (box with an arrow pointing up) in the bottom toolbar.
3. Scroll down and tap **Add to Home Screen**.
4. Tap **Add**. Dock Dash will appear as a standalone app icon on your home screen.

### Android (Chrome / Edge / Firefox)
1. Open [https://bbciii66.github.io/dock-dash/](https://bbciii66.github.io/dock-dash/) in **Chrome**.
2. Tap the **⋮** menu in the top-right corner.
3. Tap **Install app** (or **Add to Home Screen**).
4. Tap **Install**. Dock Dash will launch in full-screen standalone mode and can be played completely offline.

### Mac & Windows PC
- **Safari (Mac)**: **File → Add to Dock…**
- **Chrome / Edge (Mac & PC)**: Click the install icon in the address bar (or Menu → **Install page as app…**).

---

## Run Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/bbciii66/dock-dash.git
   ```
2. Double-click [`index.html`](./index.html) to open it directly in any modern browser.

---

## License

Released under the [MIT License](./LICENSE) — free and open source for anyone to play, modify, and improve.
