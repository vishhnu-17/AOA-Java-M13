# EX 3A N Queens Problem - Backtracking Approach.
## DATE: 25-10-2025
## AIM:
To Write a Java program for N queens using backtracking approach.  
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.  
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens.  
You have to print one such configuration.

Chess Board  
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />

Note:
- Get the input from the user for N. The value of N must be from 1 to 4.  
- If solution exists, print a binary matrix as output that has **1s** for the cells where queens are placed.  
- If there is no solution, print **"Solution does not exist"**.

## Algorithm
1. Start with an empty NxN board and try to place queens column by column.  
2. For each column, try placing a queen in every row and check if the position is safe.  
3. A position is safe if there is no queen in the same row, upper-left diagonal, or lower-left diagonal.  
4. If placing a queen is valid, place it and recursively attempt to place queens in the next column.  
5. If no safe position is found in a column, backtrack and try the next possibility.

### Developed by: Abdur Rahman Basil A H 
### Register Number: 212223040002

## Program:
```java
import java.util.Scanner;

public class NQueens {
    static int N;

    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    static boolean isSafe(int[][] board, int row, int col) {
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    static boolean solveNQUtil(int[][] board, int col) {
        if (col >= N) return true;

        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1;

                if (solveNQUtil(board, col + 1)) return true;

                board[i][col] = 0;
            }
        }
        return false;
    }

    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt();
        solveNQ();
    }
}
```

## Output:

<img width="638" height="275" alt="image" src="https://github.com/user-attachments/assets/d3e32f51-c91e-4663-9007-b58c34fc3787" />


## Result:
The program successfully implemented and the output is verified.
