# EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.



## Algorithm
1. Start by assigning the first color to the first vertex.
2. Move to the next vertex and try all available colors.
3. For each color, check if it’s safe 
4. If safe, assign the color and move to the next vertex recursively.
5. If no color works, backtrack to the previous vertex and try a different color. 

## Program:
```
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: RAJAMANIKANDAN R
Register Number:  212223220082
*/
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0] * vertices for _ in range(vertices)]

    def is_safe(self, v, color, c):
        for i in range(self.V):
            if self.graph[v][i] == 1 and color[i] == c:
                return False
        return True

    def graph_coloring_util(self, m, color, v):
        if v == self.V:
            return True

        for c in range(1, m + 1):
            if self.is_safe(v, color, c):
                color[v] = c 
                
                if self.graph_coloring_util(m, color, v + 1):
                    return True
                
                color[v] = 0

        return False

    def graphColouring(self, m):
       
        color = [0] * self.V 

        if not self.graph_coloring_util(m, color, 0):
            print("Solution does not exist")
            return None

        print("Solution exist and Following are the assigned colours:")
        print(" ".join(map(str, color)))

```

## Output:
![image](https://github.com/user-attachments/assets/58aad0c5-fc14-4ce6-9dbe-16b37842b2c4)

## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
