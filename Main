import java.util.*;

public class ConnectFour {

    public static boolean putDisk(char[][] GameBoard, int column, char color) {
        if (GameBoard[0][column] != ' ')
            return false;
        for (int row = 0; row < 6; ++row) {
            if (GameBoard[row][column] != ' ') {
                GameBoard[row-1][column] = color;
                return true;
            }
        }
        GameBoard[6][column] = color;
        return true;
    }



    private static char getWinnerInRows(char[][] GameBoard) {
        for (int row = 0; row < 6; ++row) {
            int count = 0;
            for (int column = 1; column < 7; ++column) {
                if (GameBoard[row][column] != ' ' &&
                    GameBoard[row][column] == GameBoard[row][column-1])
                    ++count;
                else
                    count = 1;
                if (count >= 4) {
                    return GameBoard[row][column];
                }
            }
        }
        return ' ';
    }


    private static char getWinnerInColumns(char[][] GameBoard) {
        for (int column = 0; column < 7; ++column) {
            int count = 0;
            for (int row = 1; row < 6; ++row) {
                if (GameBoard[row][column] != ' ' &&
                    GameBoard[row][column] == GameBoard[row-1][column])
                    ++count;
                else
                    count = 1;

 
                if (count >= 4) {
 
                    return GameBoard[row][column];
                }
            }
        }

        return ' ';
    }


    private static char getWinnerInDiagonals(char[][] GameBoard) {
        for (int column = 0; column < 7; ++column) {
            int count = 0;
            for (int row = 1; row < 6; ++row) {
                if (column + row >= 6) break;
                if (GameBoard[row][column+row] != ' ' &&
                    GameBoard[row-1][column + row - 1] == GameBoard[row][column+row])
                    ++count;
                else
                    count = 1;
                if (count >= 4) return GameBoard[row][column+row];
            }
        }

        for (int row = 0; row < 6; ++row) {
            int count = 0;
            for (int column = 1; column < 7; ++column) {

                if (column + row >= 6) break;
                if (GameBoard[row + column][column] != ' ' &&
                    GameBoard[row+column - 1][column - 1] == GameBoard[row + column][column])
                    ++count;
                else
                    count = 1;
                if (count >= 4) return GameBoard[row + column][column];
            }
        }

        for (int column = 0; column < 7; ++column) {
            int count = 0;
            for (int row = 1; row < 6; ++row) {
                if (column - row < 0) break;
                if (GameBoard[row][column-row] != ' ' &&
                    GameBoard[row - 1][column - row + 1] == GameBoard[row][column-row])
                    ++count;
                else
                    count = 1;
                if (count >= 4) return GameBoard[row][column-row];
            }
        }

        for (int row = 0; row < 6; ++row) {
            int count = 0;
            for (int column = 5; column >= 0; --column) {
                if (column - row < 0) break;
                if (GameBoard[column - row][column] != ' ' &&
                    GameBoard[column - row - 1][column + 1] == GameBoard[column - row][column])
                    ++count;
                else
                    count = 1;
                if (count >= 4) return GameBoard[column - row][column];
            }
        }

        return ' ';
    }

    public static char getWinner(char[][] GameBoard) {
        char winner = getWinnerInRows(GameBoard);
        if (winner != ' ') return winner;
        winner = getWinnerInColumns(GameBoard);
        if (winner != ' ') return winner;
        winner = getWinnerInDiagonals(GameBoard);
        if (winner != ' ') return winner;

        for (int i = 0; i < GameBoard.length; ++i)
            for (int j = 0; j < GameBoard[i].length; ++j)
                if (GameBoard[i][j] == ' ') return ' ';

        return 'D';
    }

    public static void printGameBoard(char[][] GameBoard) {
        for (int row = 0; row < 6; ++row) {
            System.out.print("| ");
            for (int col = 0; col < 7; ++col)
                System.out.print(GameBoard[row][col] + "| ");
            System.out.println();
        }

        for (int col = 0; col < 7; ++col)
            System.out.print("---");
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        char[][] GameBoard = new char[6][7];

        for (int i = 0; i < 6; ++i)
            for (int j = 0; j < 7; ++j)
                GameBoard[i][j] = ' ';
        
        printGameBoard(GameBoard);

        boolean isRed = true;
        while (true) {
            if (isRed)
                System.out.println("Red's turn!");            
            else 
                System.out.println("Yellow's turn!");
            System.out.print("Choose column (1-7) for a disk:");
            int column = input.nextInt();
            if (column < 1 || column > 7) {
                System.out.println("Column should be from 1 to 7");
                continue;
            }

            if (!putDisk(GameBoard, column - 1, isRed ? 'R' : 'Y')) {
                System.out.println("This column is filled! Choose another one.");
                continue;
            }

            printGameBoard(GameBoard);

            char result = getWinner(GameBoard);
            if (result == 'D') {
                System.out.println("It is a draw!");
                break;
            }
            else if (result == 'R') {
                System.out.println("Red win!");
                break;
            }
            else if (result == 'Y') {
                System.out.println("Yellow win!");
                break;
            }

            isRed = !isRed;
        }
    }
}
