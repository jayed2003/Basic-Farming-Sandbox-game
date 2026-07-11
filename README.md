# 🌾 Nightfall Farm — A 3D OpenGL Farming Sandbox Game

A fully-featured 3D farming sandbox game built entirely with **Python** and **PyOpenGL**. Explore an open world, grow crops, fight enemies at night, fish, trade with villagers, craft items, and survive!

> Built as a course project for **CSE 423 — Computer Graphics**

---

## 🎮 Game Overview

Nightfall Farm drops you into a vibrant open world where you play as the **Cute King Fisherman** — a crowned adventurer wielding a magic staff. Your days are spent farming, fishing, and trading. But when night falls, enemies emerge from the edges of the map, and survival becomes the priority.

### Key Features

- **Open World Exploration** — 1600×1600 unit map with grasslands, crossroads, ponds, and a healing hut
- **Day-Night Cycle** — Dynamic 24-hour cycle with sunrise, sunset, stars, and moonlight
- **Farming System** — 12×12 farm grid with wheat, corn, and berry crops across 4 growth stages
- **Combat** — Fire magic bullets at Phantom and Shade enemies that spawn at night
- **Fishing** — Cast your line at the pond and catch fish
- **Trading** — 3 NPC villagers (Mira, Bram, Lena) with unique trade offers
- **Crafting** — Combine raw materials into Bread and Stew for healing
- **Inventory System** — Quick-access Tab overlay + full inventory screen
- **Weather System** — Clear, rain, and storm conditions with lightning effects
- **Particle Effects** — Harvest sparkles and enemy death bursts

---

## 🕹️ Controls

| Key | Action |
|-----|--------|
| `W` / `S` | Move forward / backward |
| `A` / `D` | Turn left / right |
| `V` | Toggle first/third person camera |
| `E` | Interact (harvest crops, pick carrots) |
| `F` | Toggle fishing (near pond) |
| `T` | Open/close trading (near villager) |
| `C` | Open/close crafting menu |
| `Q` | Toggle auto-fire mode |
| `H` | Quick-eat best food available |
| `Tab` | Toggle quick inventory overlay |
| `ESC` | Pause menu / close UI |
| `Enter` | Confirm selection in menus |
| `Left Click` | Fire bullet / reel in fish |
| `Arrow Keys` | Camera control / menu navigation |

---

## 📦 Installation & Running

### Prerequisites

- **Python 3.7+** (Python 3.8+ recommended)
- **PyOpenGL** library

### Option 1: Using the bundled OpenGL (Recommended)

The repository includes the PyOpenGL library in the `OpenGL/` directory, so you can run the game directly without installing anything extra:

```bash
# Clone the repository
git clone https://github.com/jayed2003/Basic-Farming-Sandbox-game.git
cd Basic-Farming-Sandbox-game

# Run the game
python3 Nightfall_Farm.py
```

### Option 2: Installing PyOpenGL via pip

If you prefer to install PyOpenGL system-wide:

```bash
# Install PyOpenGL
pip install PyOpenGL PyOpenGL_accelerate

# Clone and run
git clone https://github.com/jayed2003/Basic-Farming-Sandbox-game.git
cd Basic-Farming-Sandbox-game
python3 Nightfall_Farm.py
```

### macOS Note

On macOS, GLUT is available natively. If you encounter issues, ensure you have the Xcode command line tools installed:

```bash
xcode-select --install
```

### Windows Note

On Windows, you may need to install `freeglut`. Download the freeglut binaries and place `freeglut.dll` in your Python's DLLs directory, or install via:

```bash
pip install PyOpenGL PyOpenGL_accelerate
```

---

## 🌍 World Map

```
        +Z (North)
         |
  Healing Hut    |    Pond
  (-350, 350)    |    (250, 250)
         |
-X ------+------- +X (East)
         |
  Carrot Farm    |    Main Farm
  (-350, -350)   |    (250, -250)
         |
        -Z (South)
```

**Villager Locations:**
- 🟤 **Mira** (-300, -200) — Trades wheat for corn
- 🟤 **Bram** (150, -200) — Trades corn for fire stones
- 🟤 **Lena** (-150, 100) — Trades berries for water crystals

---

## ⚔️ Gameplay Tips

1. **Start by farming** — Harvest your initial crops to build up resources
2. **Trade with villagers** — Chain trades: Wheat → Corn → Fire Stone (for weapon upgrades)
3. **Craft food before nightfall** — Bread (3 wheat = +20 HP) and Stew (2 corn + 1 berry = +35 HP)
4. **Visit the Healing Hut** — Stand near it to passively regenerate HP
5. **Use auto-fire at night** — Press `Q` to automatically target and shoot the nearest enemy
6. **Upgrade your weapon** — Level 2 costs 15 gold, Level 3 costs 30 gold + fire stone + water crystal
7. **Press Tab** to quickly check your inventory without pausing the game

---

## 🛠️ Technical Details

| Detail | Value |
|--------|-------|
| **Engine** | PyOpenGL (GL, GLUT, GLU) |
| **Language** | Python 3 |
| **Rendering** | Single-file script (~2500 lines) |
| **3D Primitives** | `GL_QUADS`, `gluSphere`, `gluCylinder`, `glutSolidCube` |
| **Resolution** | 1000×800 window |
| **Camera** | 60° FOV, perspective projection |
| **Particle System** | Array-based with physics (gravity, decay) |

---

## 📂 Project Structure

```
├── Nightfall_Farm.py    # Main game file (single-file architecture)
├── FEATURES.md          # Detailed feature list
├── README.md            # This file
└── OpenGL/              # Bundled PyOpenGL library
```

---

## 👤 Author

**Jayed** — CSE 423 Computer Graphics Project

---

## 📄 License

This project is for educational purposes as part of a university course project.
