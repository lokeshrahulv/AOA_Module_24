# EX 6C TRAVELLING SALES MAN PROBLEM
## DATE:
## AIM:
To Solve Travelling Sales man Problem for the following graph.

![image](https://github.com/user-attachments/assets/653921a4-3d7b-4691-9b41-735e80f7af0b)

## Algorithm
1. List vertices: Exclude the start vertex and create a list of other vertices.
2. Generate all routes: Find all possible ways to visit the vertices.
3. Calculate path cost: For each route, calculate the total travel cost (including returning to the start).
4. Track minimum cost: Keep track of the lowest cost found.
5. Return result: Return the minimum cost after checking all routes.  

## Program:
```
/*
To implement the program for TSP.


Developed by: ASHWIN KUMAR S
Register Number: 212222240013
*/
```
```
from sys import maxsize
from itertools import permutations
V = 4
def travellingSalesmanProblem(graph, s):
    vertex = []
    for i in range(V):
        if i != s:
            vertex.append(i)
    min_path = maxsize
    next_permutation=permutations(vertex)
    
    for i in next_permutation:
        current_pathweight = 0
        k = s
        for j in i:
            current_pathweight += graph[k][j]
            k = j
        current_pathweight += graph[k][s]
        min_path = min(min_path, current_pathweight)
        return min_path
  if __name__ == "__main__":
    graph = [[0, 10, 15, 20], [10, 0, 35, 25],
        [15, 35, 0, 30], [20, 25, 30, 0]]
    s=0
    print(travellingSalesmanProblem(graph, s))
```

## Output:
![Screenshot 2025-04-29 154615](https://github.com/user-attachments/assets/bd8d3101-9812-444a-abd6-4cf5648fc7d1)





## Result:
Thus the program was executed successfully for finding the minimum cost to vist all cities.
