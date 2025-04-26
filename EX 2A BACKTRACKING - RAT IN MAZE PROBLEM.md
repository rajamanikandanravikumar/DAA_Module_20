# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE: 
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1. Start from the top-left corner of the maze (0,0).
2. If the current cell is valid (not blocked), proceed.
3. Mark the cell as part of the solution path.
4. Recursively try moving in allowed directions (e.g., right and down).
5. If no move leads to the destination, backtrack and unmark the cell.

## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: RAJAMANIKANDAN R
Register Number:  212223220082
*/
def is_safe(maze, x, y, n):
    return 0 <= x < n and 0 <= y < n and maze[x][y] == 1

def solve_maze(maze, x, y, sol, n):
    if x == n-1 and y == n-1:
        sol[x][y] = 1
        return True

    if is_safe(maze, x, y, n):
        sol[x][y] = 1

        if solve_maze(maze, x, y + 1, sol, n):
            return True
        if solve_maze(maze, x + 1, y, sol, n):
            return True

        sol[x][y] = 0
        return False

    return False

def rat_in_maze(maze, n):
    sol = [[0 for _ in range(n)] for _ in range(n)]

    if not solve_maze(maze, 0, 0, sol, n):
        print("No solution exists")
    else:
        for row in sol:
            print(" ".join(map(str, row)))

n = 4
maze = [
    [1, 0, 0, 0],
    [1, 1, 0, 1],
    [0, 1, 0, 0],
    [1, 1, 1, 1]
]

rat_in_maze(maze, n)
```

## Output:
![image](https://github.com/user-attachments/assets/de0343f7-4e86-4810-b301-c4eed7847512)





## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
