import java.util.Scanner;

interface GameMode {
    void startGame();
}
interface PlayerActions {
    void chooseMode();
}
interface GameMessages {
    void displayWelcome(String name);
}
public class GameApp implements GameMode, PlayerActions, GameMessages {
    private String playerName;
    private int selectedMode;
    @Override
    public void displayWelcome(String name) {
        System.out.println("Welcome, " + name + "!");
        System.out.println("Press 1 or 2 to select your game mode.");
        System.out.println("1 - Story");
        System.out.println("2 - Survival");
    }
    @Override
    public void chooseMode() {
        Scanner scanner = new Scanner(System.in);
        selectedMode = scanner.nextInt();
        switch (selectedMode) {
            case 1:
                System.out.println("You selected Story Mode.");
                break;
            case 2:
                System.out.println("You selected Survival Mode.");
                break;
            default:
                System.out.println("Invalid choice. Exiting game.");
                break;
        }
    }
    @Override
    public void startGame() {
        if (selectedMode == 1 || selectedMode == 2) {
            System.out.println("Press P to start playing, " + playerName + ".");
            Scanner scanner = new Scanner(System.in);
            char startCommand = scanner.next().charAt(0);
            if (startCommand == 'P' || startCommand == 'p') {
                System.out.println("Game started. Enjoy!");
            } else {
                System.out.println("Game not started. Exiting...");
            }
        }
    }
    public static void main(String[] args) {
        GameApp game = new GameApp();
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your name: ");
        game.playerName = scanner.nextLine();
        game.displayWelcome(game.playerName);
        game.chooseMode();
        game.startGame();
    }
}
