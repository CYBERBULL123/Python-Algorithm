## N-Queens Problem

The N-Queens problem is a classic combinatorial problem in which the objective is to place N queens on an \( N \times N \) chessboard such that no two queens threaten each other. In chess, a queen can move horizontally, vertically, or diagonally, so the solution to the N-Queens problem requires that no two queens share the same row, column, or diagonal.

Here's an approach to solve the N-Queens problem using backtracking:

1. **Initialize**: Start with an empty \( N \times N \) chessboard.

2. **Place Queens**: Recursively place queens on the chessboard, one row at a time.

3. **Check Constraints**: At each step, ensure that the queen being placed does not threaten any other queens already on the board. This involves checking that no two queens share the same row, column, or diagonal.

4. **Backtrack**: If placing a queen violates any constraints, backtrack and try a different position for the queen.

5. **Base Case**: If all N queens are successfully placed on the board, return the solution.

6. **Repeat**: Continue the process until all possible solutions are found.

Here's a Python implementation of the N-Queens problem using backtracking:

```python
def is_safe(board, row, col):
    # Check if there is any queen in the same column
    for i in range(row):
        if board[i][col] == 1:
            return False

    # Check upper left diagonal
    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    # Check upper right diagonal
    for i, j in zip(range(row, -1, -1), range(col, len(board))):
        if board[i][j] == 1:
            return False

    return True

def solve_n_queens_util(board, row):
    if row == len(board):
        return True

    for col in range(len(board)):
        if is_safe(board, row, col):
            board[row][col] = 1
            if solve_n_queens_util(board, row + 1):
                return True
            board[row][col] = 0

    return False

def solve_n_queens(n):
    board = [[0] * n for _ in range(n)]
    if solve_n_queens_util(board, 0):
        return board
    else:
        return None

def print_board(board):
    for row in board:
        print(" ".join("Q" if cell == 1 else "." for cell in row))

n = 8  # Change the value of n for different board sizes
solution = solve_n_queens(n)
if solution:
    print_board(solution)
else:
    print("No solution exists.")
```

This code will print one of the possible solutions to the N-Queens problem for a given board size. You can change the value of `n` to solve the problem for different board sizes.
