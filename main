def is_valid(board, row, col, num):
    # Check if the number is not in the current row, column, or 3x3 subgrid
    for i in range(9):
        if board[row][i] == num or board[i][col] == num:
            return False
    #Find starting row and col in subgrid
    start_row, start_col = 3 * (row // 3), 3 * (col // 3)
    for i in range(3):
        for j in range(3):
            #Check subgrid to make sure number does not exist
            if board[start_row + i][start_col + j] == num:
                return False
    #Return True if validations don't fail
    return True

def solve_sudoku(board):
    #Get empty position
    empty_pos = find_empty(board)
    if not empty_pos:
         # If no empty position, the board is solved
        return [board]
    #Assign empty position to a row and col  
    row, col = empty_pos
    solutions = []
    for num in range(1, 10):
        #Checks if placing num is valid 
        if is_valid(board, row, col, num):
            board[row][col] = num
            #Recursively solve 
            for solution in solve_sudoku(board):
                #If solution is found, append it
                solutions.append([row[:] for row in solution])
            board[row][col] = 0  # Reset the cell
    return solutions

def find_empty(board):
    for i in range(9):
        for j in range(9):
            if board[i][j] == 0:
                return (i, j)
    return None

# Example usage
sudoku_board = [
    [5, 3, 0, 0, 7, 0, 0, 0, 0],
    [6, 0, 0, 1, 9, 5, 0, 0, 0],
    [0, 9, 8, 0, 0, 0, 0, 6, 0],
    [8, 0, 0, 0, 6, 0, 0, 0, 3],
    [4, 0, 0, 8, 0, 3, 0, 0, 1],
    [7, 0, 0, 0, 0, 0, 0, 0, 6],
    [0, 6, 0, 0, 0, 0, 2, 8, 0],
    [0, 0, 0, 4, 1, 9, 0, 0, 5],
    [0, 0, 0, 0, 8, 0, 0, 7, 0]
]

solutions = solve_sudoku(sudoku_board)
print(f"Total solutions found: {len(solutions)}")
for solution in solutions:
    for row in solution:
        print(row)
    print()
