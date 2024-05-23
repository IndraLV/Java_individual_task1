# Java_individual_task1
## Medium level
### I chose medium level this time. It was challanging. I understand logics very well, but sintax etc is a problem so I needed to search for right way HOW to write. I will try to implement my code when there will be more time for that - hard level and how to lock cells in order to not be possible to overwrite.
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[][] game = new int[3][3]; 
        int player = 1;

        while (true) {
            System.out.println("Player " + player + " Enter row and column of your guess (0-2):");
            int row = scanner.nextInt();
            int column = scanner.nextInt();

            game[row][column] = player;
            printGame(game);

            if (isRowFull(game, row, player)) {
                System.out.println(player +" wins!");
                break;
            }
                
            if (isColumnFull(game, column, player)) {
                System.out.println(player +" wins!");
                break;
            }

            if (isFull(game)) {
              System.out.println("It's a draw!");
              break;
            }

            player = (player == 1) ? 2 : 1;
        }
        scanner.close();
    }

    private static void printGame(int[][] game) {
        for (int[] row : game) {
            for (int guess : row) {
                System.out.print(guess + " ");
            }
            System.out.println();
        }
    }

    private static boolean isRowFull(int[][] game, int row, int player) {
        for (int guess : game[row]) {
            if (guess != player) {
                return false;
            }
        }
        return true;
      
    }
        
    private static boolean isColumnFull(int[][] game, int column, int player) {
        for (int row = 0; row < game.length; row++) {
            if (game[row][column] != player) {
                return false;
            }
        }
        return true;
    }
    private static boolean isFull(int[][] game) {
        for (int[] row : game) {
          for (int cell : row) {
              if (cell == 0) {
                  return false;
              }
          }
        }
        return true;
    }
}
```
