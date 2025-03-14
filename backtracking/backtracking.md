### **Backtracking**
---
Backtracking is an algorithmic technique used to solve problems recursively by exploring all possible solutions. It is particularly useful for problems with constraints, where you want to generate all feasible solutions or find an optimal one. Here's how it works:
   - You build a solution incrementally, step by step.
   - At each step, you test whether the current solution is valid.
   - If it is valid, you continue to the next step; if not, you backtrack, undoing the previous step and trying an alternative path.

   **Example**: The N-Queens problem.
---

```java
public class NQueens {
    static void solveNQueens(int n) {
        char[][] board = new char[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                board[i][j] = '.';
            }
        }
        backtrack(board, 0);
    }

    static void backtrack(char[][] board, int row) {
        if (row == board.length) {
            printBoard(board);
            return;
        }
        for (int col = 0; col < board.length; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 'Q'; // Place queen
                backtrack(board, row + 1); // Recurse
                board[row][col] = '.'; // Backtrack
            }
        }
    }

    static boolean isSafe(char[][] board, int row, int col) {
        for (int i = 0; i < row; i++) {
            if (board[i][col] == 'Q') return false;
        }
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j] == 'Q') return false;
        }
        for (int i = row - 1, j = col + 1; i >= 0 && j < board.length; i--, j++) {
            if (board[i][j] == 'Q') return false;
        }
        return true;
    }

    static void printBoard(char[][] board) {
        for (char[] row : board) {
            System.out.println(new String(row));
        }
        System.out.println();
    }

    public static void main(String[] args) {
        solveNQueens(4);
    }
}
```
