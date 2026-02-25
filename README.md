# tic-tac-toe_game
import java.util.*;

public class Main {

    static char[][] board = {
        {' ', ' ', ' '},
        {' ', ' ', ' '},
        {' ', ' ', ' '}
    };

    static char currentPlayer = 'X';

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        boolean gameOver = false;

        while (!gameOver) {
            printBoard();
            System.out.println("Player " + currentPlayer + " enter row and column (0-2):");

            int row = sc.nextInt();
            int col = sc.nextInt();

            
            if (row >= 0 && row < 3 && col >= 0 && col < 3 && board[row][col] == ' ') {
                board[row][col] = currentPlayer;

                if (checkWin()) {
                    printBoard();
                    System.out.println("Player " + currentPlayer + " wins!");
                    gameOver = true;
                } 
                else if (isBoardFull()) {
                    printBoard();
                    System.out.println("It's a draw!");
                    gameOver = true;
                } 
                else {
                    
                    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
                }
            } else {
                System.out.println("Invalid move! Try again.");
            }
        }
        sc.close();
    }


    static void printBoard() {
        System.out.println("\n-------------");
        for (int i = 0; i < 3; i++) {
            System.out.print("| ");
            for (int j = 0; j < 3; j++) {
                System.out.print(board[i][j] + " | ");
            }
            System.out.println();
            System.out.println("-------------");
        }
    }

    
    static boolean checkWin() {
    
        for (int i = 0; i < 3; i++) {
            if (board[i][0] == currentPlayer &&
                board[i][1] == currentPlayer &&
                board[i][2] == currentPlayer)
                return true;

            if (board[0][i] == currentPlayer &&
                board[1][i] == currentPlayer &&
                board[2][i] == currentPlayer)
                return true;
        }

        
        if (board[0][0] == currentPlayer &&
            board[1][1] == currentPlayer &&
            board[2][2] == currentPlayer)
            return true;

        if (board[0][2] == currentPlayer &&
            board[1][1] == currentPlayer &&
            board[2][0] == currentPlayer)
            return true;

        return false;
    }

    static boolean isBoardFull() {
        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[i][j] == ' ')
                    return false;
        return true;
    }
}
output:

-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
Player X enter row and column (0-2):
0 1

-------------
|   | X |   | 
-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
Player O enter row and column (0-2):
1 - 0

-------------
|   | X |   | 
-------------
| O |   |   | 
-------------
|   |   |   | 
-------------
Player X enter row and column (0-2):
0 0

-------------
| X | X |   | 
-------------
| O |   |   | 
-------------
|   |   |   | 
-------------
Player O enter row and column (0-2):
0 2

-------------
| X | X | O | 
-------------
| O |   |   | 
-------------
|   |   |   | 
-------------
Player X enter row and column (0-2):
1 1

-------------
| X | X | O | 
-------------
| O | X |   | 
-------------
|   |   |   | 
-------------
Player O enter row and column (0-2):
2 2

-------------
| X | X | O | 
-------------
| O | X |   | 
-------------
|   |   | O | 
-------------
Player X enter row and column (0-2):
1 2

-------------
| X | X | O | 
-------------
| O | X | X | 
-------------
|   |   | O | 
-------------
Player O enter row and column (0-2):
2 1

-------------
| X | X | O | 
-------------
| O | X | X | 
-------------
|   | O | O | 
-------------
Player X enter row and column (0-2):
2 0

-------------
| X | X | O | 
-------------
| O | X | X | 
-------------
| X | O | O | 
-------------
It's a draw!
