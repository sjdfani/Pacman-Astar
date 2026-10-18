# Pacman A* Project

A small Python visualization in which Pacman collects every piece of food in a maze. It decides which food to visit next, uses the **A\* search algorithm** to find a path there, and animates the walk with `turtle`.

## How it works

1. **Choose a maze.** At startup you enter how many foods you want (1–4). Each choice loads a predefined 40×21 maze from `grids.py`.
2. **Build the graph.** Every open cell becomes a node, and neighbouring open cells (up, down, left, right) are connected by edges.
3. **Order the foods.** Starting from Pacman's position, the program repeatedly picks the closest remaining food by straight-line (Euclidean) distance. This gives a greedy visiting order.
4. **Find each path with A\*.** For every food in that order, A\* searches the maze graph from Pacman's current cell to the food, using Manhattan distance as the heuristic.
5. **Animate.** Pacman follows each path in turn until all the food is eaten.

## Project structure

| File | Purpose |
| --- | --- |
| `pacman.py` | Entry point. Draws the maze, builds the graph, orders the foods and moves Pacman. |
| `search.py` | A\* implementation (`aStar`) and path reconstruction (`traverse_back`). |
| `heuristic.py` | Euclidean and Manhattan distance functions. |
| `grids.py` | The four mazes and `get_grid()`, which picks one by food count. |
| `images/` | GIF sprites for walls, food and Pacman (24×24 px cells). |

### Maze format

Each maze in `grids.py` is a list of strings, one per row:

| Character | Meaning |
| --- | --- |
| `+` | Wall |
| `s` | Pacman's starting position |
| `f` | Food |
| space | Open path |

To add your own maze, write a new 40×21 grid in the same format and add it to the list in `get_grid()`.

## Requirements

- Python 3
- `tkinter` (bundled with the standard Python installer on Windows)
- **Windows.** `pacman.py` reads the screen resolution with `ctypes.windll`, which only exists on Windows. It will not start on macOS or Linux unless that call is replaced.

No third-party packages are needed.

## Usage

Run the program from the project root so the `images/` folder can be found:

```bash
python pacman.py
```

When prompted, enter the number of foods (1, 2, 3 or 4):

```
Enter count of food? (1, 2, 3, 4)? 3
```

A window opens showing the maze, and Pacman walks to each food. Close the window to exit.

## Contact

If you have any questions or comments, feel free to reach out at [faniam321@gmail.com](mailto:faniam321@gmail.com).
