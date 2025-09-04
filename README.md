# 💎 CS50 — Match 3

[![LÖVE2D](https://img.shields.io/badge/Engine-L%C3%96VE2D-informational)](https://love2d.org/)
[![Language](https://img.shields.io/badge/Language-Lua-blue)](https://www.lua.org/)
[![Course](https://img.shields.io/badge/Course-CS50G-red)](https://cs50.harvard.edu/games/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

**Course:** [CS50's Introduction to Game Development](https://cs50.harvard.edu/games/)  
**Assignment:** Match 3  
**Engine / Language:** LÖVE2D (Lua)  

---

## 📋 Project Overview

This repository contains my implementation of the **Match 3** assignment from CS50's Introduction to Game Development.
📺 You can also watch my gameplay demo on [YouTube](https://youtu.be/KNoylyu6ESU?si=Ww6pjrrdy6sNmMmW).

---

### What I implemented

- ✔️ **Time bonus on matches** — Gain **+1 second per tile** in any match (e.g., a 4-match = +4s, 5-match = +5s).  
- ✔️ **Level 1 with simple flat tiles** — Only the first variety (flat blocks) appear at Level 1. Higher levels introduce patterned varieties (triangle, cross, etc.) with **higher point values**.  
- ✔️ **Shiny tiles** — Random special tiles that, when part of a match, **clear the entire row** and grant points for each cleared tile.  
- ✔️ **Swap validation** — Only swaps that **result in a match** are permitted; non-matching swaps are reverted. If **no matches are available**, the board is **reset**.  

---

## 🎬 Gameplay Preview

![Gameplay Preview](docs/gameplay.gif)

---

## 🚀 How to Run

1. Install [LÖVE2D](https://love2d.org/).  

2. Clone this repository:

   ```bash
   git clone https://github.com/huzaifa-gamedev/cs50-match3.git
   cd cs50-match3
   ```

3. Run the game:

   ```bash
   love .
   ```

---

## 🎯 Controls

- **Arrow Keys (↑ ↓ ← →)** — Move the tile selector around the board.  
- **Enter** — Select a tile, then select an adjacent tile to **swap** (only valid if it forms a match).  
- **E** — Instantly end the game (**Game Over**).  
- **R** — Randomize all tiles on the board (useful when no matches remain).  
- **Escape** — Quit game.  


---

## 🧠 Notes on Implementation

- **Timer Bonuses:** Added in `PlayState:calculateMatches` by extending the timer by `+1s` for each tile involved in matches.  
- **Level-Scaled Varieties:** Passed `level` into `Board` creation (from `PlayState:enter`) to **constrain `variety`** at low levels and **unlock patterns** at higher levels, assigning **higher scores** to patterned tiles.  
- **Shiny Tiles:** Extended `Tile` with a `shiny` flag. In `Board:calculateMatches`, if any matched tile is shiny, **convert the entire row** into a match and score each cleared tile.  
- **Valid-Only Swaps & Dead-Board Handling:** After a tentative swap, run `Board:calculateMatches`; revert immediately if no match. Periodically (or after cascades) **probe adjacent pretend-swaps** across the board to detect **available moves**; if none exist, **re-roll** the board (using a limited color palette to keep solvability high).  
- **Balance Tuning:** Limited the spawn palette to **~8 colors** to keep **match probability reasonable** and avoid unsolvable boards.

---

## ✨ Credits

- Original skeleton code & assets: CS50's Introduction to Game Development (Harvard). Licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).  

---

## 📄 License

- This implementation: © 2025 Muhammad Huzaifa Karim. Licensed under the [MIT License](LICENSE).  

For more details, see [ATTRIBUTION.md](ATTRIBUTION.md).  

---

## ✍️ Author

**Muhammad Huzaifa Karim**  
[GitHub Profile](https://github.com/huzaifakarim1)  

---

## 📬 Contact

For ideas, feedback, or collaboration, feel free to reach out via [GitHub](https://github.com/huzaifakarim1).  

---

© 2025 Muhammad Huzaifa Karim. All rights reserved.
