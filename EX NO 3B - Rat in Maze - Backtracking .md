# EX 3B Rat in Maze- Backtracking 
## DATE: 25-10-2025
## AIM:
To write a Java program to for given constraints.  
There is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1).  
The ball can move through empty spaces by rolling up, down, left, or right, but it **won't stop rolling until it hits a wall**.  
When the ball stops, it can choose the next direction.

Given the **m × n maze**, the ball's **start position** and **destination**, return **true** if the ball can stop at the destination, otherwise return **false**.

You may assume that the borders of the maze are all walls.

Example:  
Input:  
maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]]  
start = [0,4], destination = [4,4]  
Output: true  

Explanation: One possible way is:  
left → down → left → down → right → down → right.

<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />

## Algorithm
1. Use DFS to explore all possible stopping points where the ball rolls until hitting a wall.  
2. From the start position, roll the ball in all four directions until it reaches a wall.  
3. Once the ball stops, recursively explore from that new stopping point.  
4. Maintain a visited matrix to avoid revisiting the same stop point.  
5. If the destination is reached, return true; if all possibilities are exhausted, return false.

## Developed by: Abdur Rahman Basil A H
## Register Number: 212223040002

## Program:
```java
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        int[] start = new int[]{sc.nextInt(), sc.nextInt()};
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    private final int[][] dirs = {{1,0},{-1,0},{0,1},{0,-1}};
    
    public boolean hasPath(int[][] maze,int[] start,int[] dest){
        int m=maze.length,n=maze[0].length;
        boolean[][] visited = new boolean[m][n];
        return dfs(m,n,maze,start,dest,visited);
    }
    
    public boolean isvalid(int x,int y,int[][] maze){
        return x>=0 && x<maze.length && y>=0 && y<maze[0].length && maze[x][y]==0;
    }

    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] dest, boolean[][] visited) {
        if(visited[curr[0]][curr[1]]) return false;
        if(curr[0] == dest[0] && curr[1] == dest[1]) return true;
        
        visited[curr[0]][curr[1]] = true;
        
        for(int[] d : dirs){
            int x = curr[0], y = curr[1];
            
            while(isvalid(x + d[0], y + d[1], maze)){
                x += d[0];
                y += d[1];
            }
            
            if(dfs(m, n, maze, new int[]{x, y}, dest, visited)) return true;
        }
        
        return false;
    }
}
```

## Output:

<img width="404" height="546" alt="image" src="https://github.com/user-attachments/assets/f31c973f-d871-48fe-9cab-47d045543780" />


## Result:
The program successfully implemented and the expected output is verified.
