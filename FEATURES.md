# Nightfall Farm — Feature List

## 1. Core Gameplay

### Player Character
- 3D humanoid model: "Cute King Fisherman" with head, eyes, blush, body, arms, legs, boots, and a golden crown
- Staff weapon held in the left hand with a glowing magic gem on top
- Fishing rod appears in the left hand when fishing mode is active
- Smooth walking animation via W/S keys, rotation via A/D keys
- Player dies when HP reaches 0, triggering a death screen with restart option

### Camera System
- **Third-Person Mode** (default): Camera orbits around the player
  - Arrow Up/Down: Raise/lower camera height (100–900 range)
  - Arrow Left/Right: Rotate camera around the player
- **First-Person Mode**: Camera at player's head, looking forward
  - Toggle with `V` key
  - Interior of the healing hut is visible when walking inside

---

## 2. World & Environment

### Map Layout
- Large open world (1600×1600 units) with green grass ground
- Central crossroads splitting the map into quadrants
- Boundary walls prevent the player from walking off the map edge

### Day-Night Cycle
- 24-hour in-game clock advancing in real time
- **Daytime (8:00–18:00)**: Bright sky, full visibility
- **Dusk (18:00–20:00)**: Sky gradually darkens, lighting dims
- **Night (20:00–6:00)**: Dark sky, stars visible, enemies spawn
- **Dawn (6:00–8:00)**: Sky gradually brightens
- Sun and moon orbit across the sky based on the time of day

### Sky & Atmosphere
- Dynamic skybox (5-face box) follows the player, color shifts with time
- 300 pre-computed star positions visible only at night
- 30 drifting clouds that change color between day and night

### Weather System
- **Clear**: Default state, no particles
- **Rain**: 300 rain streak particles falling across the entire map, following the player
- **Storm**: 500 rain streaks + periodic white lightning flashes (full-screen quad overlay)
- Weather transitions randomly between clear and rain states

### Pond
- Circular pond at position (250, 0, 250) with 150-unit radius
- Three concentric layers:
  - **Outer bank**: Brown dirt ring
  - **Deep blue water**: Outer water ring
  - **Light blue water**: Inner shallow center
- 5 animated fish swimming in circles inside the pond
- **Player submersion**: Walking into the deep blue area sinks the player to Y=-6; walking into the light blue center sinks to Y=-12; smooth interpolation back to Y=0 when exiting

### Healing Hut
- Located at (-350, 350) in the bottom-left quadrant
- Fully walkable interior with:
  - Wooden floor
  - 4 walls with a door opening on the front (+Z) face
  - Interior walls (slightly darker) for visibility from inside
  - Pyramid roof perfectly aligned with wall edges
  - Glowing green healing orb floating inside
- **Wall collision**: Player cannot walk through the back, left, or right walls; can only enter through the front door
- **Passive healing**: Player regenerates HP slowly when near the hut

### Scenery
- 80 randomly placed edge trees (brown trunk + green foliage sphere)
- Bushes scattered around the map edges
- 50 rocks of varying sizes
- 150 grass tufts in open areas
- All scenery uses a fixed random seed (42) for consistency across frames

---

## 3. Farming

### Main Farm (Right side of map)
- 12×12 grid of plots offset to (250, -250)
- Starting plots (center 4×4) are pre-owned with random crops
- **Owned plots**: Brown farmland with fence posts at corners
- **Unowned plots**: Green grass matching the ground color

### Crops
- **Three crop types**: Wheat (golden), Corn (orange), Berry (pink/magenta)
- **Growth stages** (0–3):
  - Stage 0: Small seedling
  - Stage 1: Taller stalk
  - Stage 2: Near-mature plant
  - Stage 3: Fully grown, harvestable
- Crops grow over time automatically
- Harvest with `E` key when standing near a fully grown crop

### Carrot Farm (Left side of map)
- Separate 3×3 decorative farm at (-350, -350)
- Orange carrot crops on brown soil
- Carrots respawn on a timer after being harvested

---

## 4. Combat

### Enemies
- **Two enemy types**:
  - **Phantom** (brown): Faster speed (0.5), basic humanoid
  - **Shade** (purple): Slower speed (0.25), has red horn rings on head
- Enemies only spawn at night, from random map edges
- Spawn every 300 ticks during nighttime
- Walk toward the player; deal damage on contact (every 60 ticks)
- All enemies are cleared at dawn
- Each enemy has a 3D health bar floating above its head

### Weapons & Bullets
- **Left-click**: Fire a yellow bullet in the direction the player faces
- Bullets travel at speed 15 with a time-to-live of 100 ticks
- **Weapon levels** (3 tiers):
  - Level 1: 5 damage (2 hits to kill)
  - Level 2: 5 damage (costs 15 currency to upgrade)
  - Level 3: 10 damage (costs 30 currency + 1 fire_stone + 1 water_crystal)
- **Auto-fire mode** (`Q` key): Automatically aims and fires at the nearest enemy within 300 units every 15 ticks

### Enemy Drops
- Killing an enemy awards +1 currency

---

## 5. Fishing

- Press `F` near the pond to enter fishing mode
- Fishing rod appears; line is cast into the pond
- Fish are caught automatically after a randomized timer
- Each catch adds +1 to fish count and +1 wheat to inventory
- Left-click to reel in when a fish bites (bobber bounces)
- Press `F` again to exit fishing mode
- Fishing rod rendered as a 3D cylinder with a thin quad fishing line and a red bobber

---

## 6. Trading

### Villagers
- **3 NPC villagers** placed around the map:
  - **Mira** (-300, -200): 5 wheat → 3 corn
  - **Bram** (150, -200): 3 corn → 1 fire_stone
  - **Lena** (-150, 100): 5 berry → 1 water_crystal
- Each villager has a humanoid model with torso, head, hat with brim, arms, and legs
- A golden ring appears on the ground when the player is within trade range (60 units)
- Villager name displayed above when in range

### Trading Interface
- Press `T` near an active villager to open the trade UI
- Shows required items and current inventory count
- Green text if you have enough, red if insufficient
- Press Enter to confirm trade, `T` to close

---

## 7. Crafting

### Recipes
| Recipe | Ingredients | Food Value |
|--------|------------|------------|
| Bread  | 3 Wheat    | +20 HP     |
| Stew   | 2 Corn + 1 Berry | +35 HP |

### Crafting Interface
- Press `C` to open crafting menu (or select from ESC menu)
- Shows all recipes with ingredient counts (have/need)
- Green = craftable, Yellow = selected, Grey = insufficient materials
- Arrow keys to navigate, Enter to craft, `C` to close

---

## 8. Inventory & Food

### Items
- **Raw materials**: Wheat, Corn, Berry, Wood, Water Crystal, Fire Stone, Plank, Bow
- **Cooked food**: Bread, Stew

### Inventory Screen (Full)
- Access via ESC menu → Inventory
- Bordered panel with dark background and gold trim
- Lists all items with quantities in item-colored text (items with 0 count hidden)
- Cooked food items marked with [EAT] prefix and HP restoration value
- Selection highlight bar on currently selected item
- Shows gold currency at top
- Select food and press Enter to eat → restores HP
- Arrow keys to navigate, ESC to close

### Quick Inventory (Tab)
- Press `Tab` to toggle a quick-access inventory overlay on the right side
- Categorized display: Raw Materials and Cooked Food sections
- Color-coded item dots matching each item type
- Shows gold count and weapon level at top
- Food items display HP restoration values
- Non-intrusive: game continues running behind the overlay
- Close with `Tab` or `ESC`

---

## 9. User Interface

### HUD (Always Visible)
- **Top-left**: HP bar with gradient color (green→yellow→red based on health), framed with gold border
- **Below HP**: Gold currency counter and weapon level indicator (color-coded by tier)
- **Top-center**: Day counter with 24h clock (HH:MM format) + [NIGHT] indicator in blue
- **Top-right**: Crop count, weather status, fish caught, enemy count — bordered panel
- **Bottom bar**: Control hints including Tab key, with gold top border
- **Auto-fire indicator**: Red pulsing dot and "AUTO-ON" label when active
- **Center**: HUD messages with fade-out animation
- **Low HP warning**: Pulsing red text when HP ≤ 25

### Particle Effects
- **Harvest particles**: Color-matched sparkles burst when crops/carrots are harvested
- **Enemy death**: Colored burst (brown for phantoms, purple for shades) on kill
- Particles have gravity, size decay, and alpha fade-out

### Pause Menu (ESC)
- Full-screen background dimming overlay
- Bordered dark panel with gold trim and title divider
- Options: Farm, Inventory, Crafting, Quit with navigation hints
- Arrow keys to navigate, Enter to select

### Death Screen
- Full-screen dark red tint overlay
- Bordered central panel with red trim
- Options: "Yes" (restart) or "No (Quit)"
- Restart resets HP to 100, returns player to spawn, clears enemies

---

## 10. Controls

| Key | Action |
|-----|--------|
| `W` | Move forward |
| `S` | Move backward |
| `A` | Turn left |
| `D` | Turn right |
| `Shift` | Sprint (Hold while moving to move at 2x speed) |
| `V` | Toggle first/third person camera |
| `E` | Interact (harvest crops, pick carrots) |
| `F` | Toggle fishing (near pond) |
| `T` | Open/close trading (near villager) |
| `C` | Open/close crafting |
| `Q` | Toggle auto-fire |
| `Tab` | Toggle quick inventory overlay |
| `H` | Quick-eat best food available |
| `ESC` | Pause menu / close UI |
| `Enter` | Confirm selection in menus |
| `Left Click` | Fire bullet / reel in fish |
| `Arrow Keys` | Camera control / menu navigation |

---

## 11. Technical Details

- **Engine**: PyOpenGL (GL, GLUT, GLU)
- **Rendering**: Single-file Python script, ~2500 lines
- **Primitives used**: `GL_QUADS`, `GL_POINTS`, `GL_LINES`, `GL_LINE_LOOP`, `gluSphere`, `gluCylinder`, `glutSolidCube`
- **Font**: `GLUT_BITMAP_HELVETICA_18` (single font throughout)
- **Resolution**: 1000×800 window
- **Camera**: `gluPerspective` with 60° FOV, near plane 1.0, far plane 3000
- **Depth buffer**: `GL_DEPTH_TEST` with `GL_LESS`
- **Particle system**: Array-based with position, velocity, color, life, and size properties
