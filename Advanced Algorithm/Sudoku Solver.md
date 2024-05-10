Python implementation of a Sudoku solver using backtracking:

```python
def is_valid(board, row, col, num):
    # Check if the number already exists in the current row
    if num in board[row]:
        return False
    
    # Check if the number already exists in the current column
    for i in range(9):
        if board[i][col] == num:
            return False
    
    # Check if the number already exists in the current 3x3 subgrid
    start_row, start_col = 3 * (row // 3), 3 * (col // 3)
    for i in range(start_row, start_row + 3):
        for j in range(start_col, start_col + 3):
            if board[i][j] == num:
                return False
    
    return True

def find_empty_location(board):
    # Find the first empty location in the board
    for i in range(9):
        for j in range(9):
            if board[i][j] == 0:
                return i, j
    return None, None

def solve_sudoku(board):
    row, col = find_empty_location(board)
    if row is None and col is None:
        # If there are no empty locations, the board is solved
        return True
    
    for num in range(1, 10):
        if is_valid(board, row, col, num):
            board[row][col] = num
            if solve_sudoku(board):
                return True
            board[row][col] = 0
    
    # Backtrack if no valid number can be placed
    return False

def print_board(board):
    for row in board:
        print(" ".join(map(str, row)))

# Example Sudoku board (0 represents empty cells)
board = [
    [5, 3, 0, 0, 7, 0, 0, 0, 0],
    [6, 0, 0, 1, 9, 5, 0, 0, 0],
    [0, 9, 8, 0, 0, 0, 0, 6, 0],
    [8, 0, 0, 0, 6, 0, 0, 0, 3],
    [4, 0, 0, 8, 0, 3, 0, 0, 1],
    [7, 0, 0, 0, 2, 0, 0, 0, 6],
    [0, 6, 0, 0, 0, 0, 2, 8, 0],
    [0, 0, 0, 4, 1, 9, 0, 0, 5],
    [0, 0, 0, 0, 8, 0, 0, 7, 9]
]

if solve_sudoku(board):
    print("Sudoku Solved:")
    print_board(board)
else:
    print("No solution exists.")
```

This code solves the Sudoku puzzle using backtracking. It iterates through each empty cell, attempts to place a number (1-9), and recursively tries to solve the puzzle. If no valid number can be placed, it backtracks and tries a different number. Once a solution is found, it prints the solved Sudoku board.
