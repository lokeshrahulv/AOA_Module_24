# AOA_Module_24
# EX 6A CHERRY PICK UP PROBLEM
## DATE:
## AIM:
To Create a python program for the following problem statement.
You are given an n x n grid representing a field of cherries, each cell is one of three possible integers.
0	means the cell is empty, so you can pass through,
1	means the cell contains a cherry that you can pick up and pass through, or
-1 means the cell contains a thorn that blocks your way.
Return the maximum number of cherries you can collect by following the rules below:
Starting at the position (0, 0) and reaching (n - 1, n - 1) by moving right or down through valid path cells (cells with value 0 or 1).
After reaching (n - 1, n - 1), returning to (0, 0) by moving left or up through valid path cells.
When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell 0. If there is no valid path between (0, 0) and (n - 1, n - 1), then no cherries can be collected.



## Algorithm
1. Use a 3D DP table dp[x1][y1][x2] to store the maximum cherries collected when two players move from (0,0) to (x1,y1) and (x2,y2), where y2 = x1 + y1 - x2 
2. If either player goes out of bounds or hits a thorn (-1), return -∞ (invalid path). If both are at (0,0), return grid[0][0].
3. Try all four possible moves (player1 and player2 each move either up or left), and take the max result.
4. Collect cherries from both positions (only once if both are at the same cell).
5. Start recursion from bottom-right corner (n-1,n-1) for both players and return max(0, result) to handle case where no valid path exists.

## Program:
```
/*
To implement the program for Cherry pickup problem.


Developed by:  LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
class Solution:
    def cherryPickup(self, grid):
        n = len(grid)
        dp=[[[-1]*n for _ in range(n)] for _ in range(n)]
        def f(x1,y1,x2):
            y2=x1+y1-x2
            if x1<0 or y1<0 or x2<0 or y2<0 or grid[x1][y1]==-1 or grid[x2][y2]==-1:
                return float('-inf')
            if x1==0 and y1==0 and x2==0 and y2==0:
                return grid[0][0]
            if dp[x1][y1][x2]!=-1:
                return dp[x1][y1][x2]
            cherries=grid[x1][y1]
            if x1!=x2 or y1!=y2:
                cherries+=grid[x2][y2]
            cherries+=max(
                          f(x1-1,y1,x2-1),
                           f(x1,y1-1,x2-1),
                           f(x1-1,y1,x2),
                           f(x1,y1-1,x2))
            dp[x1][y1][x2]=cherries
            return cherries
        result= max(0,f(n-1,n-1,n-1))
        return result
obj=Solution()
grid=[[0,1,-1],[1,0,-1],[1,1,1]]        
print(obj.cherryPickup(grid))
```

## Output:
![image](https://github.com/user-attachments/assets/ce1cf2d2-ba57-464c-a9d4-139ea9283192)




## Result:
Thus the above program was executed successfully for finding the maximum number of cherries from grid.
# EX 6B KNAPSACK PROBLEM
## DATE:
## AIM:
To demonstrate a python program using dynamic programming for 0/1 knapsack problem.



## Algorithm
1. Base case: If there are no items left or the capacity is 0, return 0.
2. Item exclusion: If the current item's weight is greater than the remaining capacity, skip it.
3. Item inclusion: Otherwise, choose between including the item or excluding it.
4. Recursive calls: Recursively solve the problem by either excluding or including the item.
5. Return maximum value: At each step, return the maximum value of including or excluding the current item. 

## Program:
```
/*
To implement the program for 0/1 knapsack problem.


Developed by: LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
def knapSack(W, wt, val, n):
	if n == 0 or W == 0 :
		return 0
	if (wt[n-1] > W):
		return knapSack(W, wt, val, n-1)
	else:
		return max(val[n-1] + knapSack(W-wt[n-1], wt, val, n-1), knapSack(W, wt, val, n-1))
	#End here
x=int(input())
y=int(input())
W=int(input())
val=[]
wt=[]
for i in range(x):
    val.append(int(input()))
for y in range(y):
    wt.append(int(input()))

n = len(val)
print('The maximum value that can be put in a knapsack of capacity W is: ',knapSack(W, wt, val, n))
```

## Output:
![image](https://github.com/user-attachments/assets/dfd9f27c-8fa2-487d-9aa8-229742f8883a)




## Result:
Thus the program was executed successfully for finding the maximum value that can be put in a knap sack of capacity .
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


Developed by: LOKESH RAHUL V V
Register Number: 212222100024
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
# EX 6D BRUTE FORCE ALGORITHM
## DATE:
## AIM:
To write a python program using brute force method of searching for the given substring in the main string.

## Algorithm
1.Start from index 0 in the main string and try to match the substring at every position.

2.Compare characters one by one from the current position in the main string to the substring.

3.If all characters match, return the current index as the starting point of the match.

4.If a mismatch is found, move to the next index in the main string and repeat.

5.If no match is found after checking all valid positions, return -1.
## Program:
```
/*
To implement the program using brute force method of searching for the given substring in the main string.

Developed by:LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
import re
def match(string,sub):
    pattern = re.compile(str2)
    r = pattern.search(str1)
    while r:
        print("Found at index {}".format(r.start()))
        r = pattern.search(str1,r.start()+1)    

str1=input()
str2=input()
```


## Output:
![image](https://github.com/user-attachments/assets/3d77b8ef-4088-47ad-ad26-e0a95a39b2e6)



## Result:
Thus the above program was executed successfully for searching the substring at respective index.
