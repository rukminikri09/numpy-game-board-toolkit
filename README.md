# Game Board & Pattern Generator Toolkit

A small NumPy project that builds game boards and grid patterns without any loops for the patterns themselves.

## Problem
I wanted to get comfortable with NumPy array creation, slicing and indexing, so I used game boards as the practice material: a Tic-Tac-Toe board, an 8x8 chessboard, diagonal patterns, and a win checker.

## Approach
- Tic-Tac-Toe board made with `np.zeros((3, 3), dtype=int)` and also from a nested list
- Chessboard made with stepped slicing: `board[::2, ::2] = 1` and `board[1::2, 1::2] = 1`
- Diagonal and anti-diagonal patterns with `np.eye()` and `np.fliplr()`
- Other grids with `np.ones`, `np.full`, `np.arange` and an identity grid
- Placing and moving pieces with fancy indexing (row and column index arrays)
- `check_winner()` that checks rows, columns and both diagonals using slicing and `np.diag`
- Boards displayed with `plt.imshow`

## Win checker (rows, columns and diagonals with slicing)
```python
def check_winner(b):
    n = b.shape[0]
    for player in (1, 2):
        for i in range(n):
            if np.all(b[i, :] == player) or np.all(b[:, i] == player):
                return player
        if np.all(np.diag(b) == player) or np.all(np.diag(b[:, ::-1]) == player):
            return player
    return 0
```
The board is then displayed with `plt.imshow(board)`.

## Screenshots
**Chessboard**

![chessboard](screenshots/1_chessboard.png)

**Diagonal patterns**

![diagonal patterns](screenshots/2_diagonal_patterns.png)

**Win checker: O wins on the anti-diagonal**

![anti-diagonal win](screenshots/3_anti_diagonal_win.png)

**Demo game: final board (X wins)**

![final board](screenshots/4_final_game_board.png)

**Step 5: win checker output with plt.imshow (X wins on the diagonal)**

![step 5 win checker](screenshots/5_win_checker_imshow.png)

## NumPy topics used
`np.zeros`, `np.ones`, `np.full`, `np.eye`, `np.arange`, `np.fliplr`, `np.diag`, nested-list arrays, slicing with steps, fancy indexing

## How to run
1. Open `game_board_pattern_toolkit.ipynb` in Google Colab (or Jupyter)
2. Run all cells from top to bottom (only NumPy and matplotlib are needed)
