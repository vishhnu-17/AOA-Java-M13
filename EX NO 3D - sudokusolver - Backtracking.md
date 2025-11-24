
# EX 3D Sudoku solver - Backtracking.
## DATE: 25-10-2005
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Check if placing a digit is valid by verifying row, column, and 3×3 subgrid constraints.
2. Move to the next row when reaching the end of a column.
3. Skip filled cells and recursively solve the next column.
4. Try numbers 1–9 in empty cells and continue only if placement is safe.
5. Backtrack by resetting the cell to 0 when no valid number leads to a solution.


### Developed by: Abdur Rahman Basil A H 
### Register Number: 212223040002

## Program:
```java
import java.util.Scanner;

public class SudokuSolver {

    // Check if it's safe to place the number
    static boolean isSafe(int[][] board, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        // Check 3x3 subgrid
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    // Recursive backtracking solver
    static boolean solveSudoku(int[][] board, int row, int col) {
        //Type your code here
        
        if(row==9)return true;
        
        if(col==9)return solveSudoku(board,row+1,0);
        
        if(board[row][col]!=0)return solveSudoku(board,row,col+1);
        
        for(int i=1;i<=9;i++){
            if(isSafe(board,row,col,i)){
                board[row][col]=i;
                
                if(solveSudoku(board,row,col+1)) return true;
                
                board[row][col]=0;
            }
        }
        return false;
    }

    // Utility to print the board
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

      //  System.out.println("\nSolving...\n");

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```

## Output:

<img width="675" height="619" alt="image" src="https://github.com/user-attachments/assets/d4e9f641-c877-4c5a-b2cd-c5bae78db7cf" />


## Result:
The program successfully implemented and the expected output is verified.
