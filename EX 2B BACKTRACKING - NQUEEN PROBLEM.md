# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm
1. Start placing queens from the first row.
2. For each row, try placing a queen in each column one by one.
3. Check if placing a queen in the current column is safe (no other queen in same column, or diagonals).
4. If safe, place the queen and move to the next row recursively.
5. If no column is safe, backtrack to the previous row and try a new position.

## Program:
```
/*
Program to implement N-Queen problem using backtracking.
Developed by: RAJAMANIKANDAN R
Register Number:  212223220082
*/
global N
N = int(input())

def printSolution(board):
    for i in range(N):
        for j in range(N):
            print(board[i][j], end=" ")
        print()

def isSafe(board, row, col):
    for i in range(col):
        if board[row][i] == 1:
            return False

    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    for i, j in zip(range(row, N, 1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    return True

def solveNQUtil(board, col):
    if col >= N:
        return True

    for i in range(N):
        if isSafe(board, i, col):
            board[i][col] = 1
            if solveNQUtil(board, col + 1):
                return True
            board[i][col] = 0

    return False

def solveNQ():
    board = [[0 for _ in range(N)] for _ in range(N)]
    
    if not solveNQUtil(board, 0):
        print("Solution does not exist")
        return False

    printSolution(board)
    return True

solveNQ()

```

## Output:
![image](https://github.com/user-attachments/assets/bb68b255-6b65-49b4-b3d6-cc9ee97e9d73)



## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
