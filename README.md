# Number Guessing Game

This project is based on the roadmap from [roadmap.sh](https://roadmap.sh/projects/number-guessing-game).
You can find the project details [here](https://roadmap.sh/projects/number-guessing-game).


import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        boolean playAgain = true;

        System.out.println("Hello Welcome to the Number Guessing Game!");
        System.out.println("I'm thinking of a number between 1 and 100.");

        while (playAgain) {
            System.out.println("\nPlease select the difficulty level:");
            System.out.println("1. Easy (10 chances)");
            System.out.println("2. Medium (5 chances)");
            System.out.println("3. Hard (3 chances)");
            System.out.print("Enter your choice: ");
            int difficulty = scanner.nextInt();
            int chances;
            
            switch (difficulty) {
                case 1:
                    chances = 10;
                    System.out.println("Great! You have selected the Easy difficulty level.");
                    break;
                case 2:
                    chances = 5;
                    System.out.println("Great! You have selected the Medium difficulty level.");
                    break;
                case 3:
                    chances = 3;
                    System.out.println("Great! You have selected the Hard difficulty level.");
                    break;
                default:
                    System.out.println("Invalid choice! Defaulting to Medium difficulty level.");
                    chances = 5;
            }

            System.out.println("Let's start the game!");
            int numberToGuess = random.nextInt(100) + 1;
            boolean guessedCorrectly = false;

            for (int attempt = 1; attempt <= chances; attempt++) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You guessed the correct number in " + attempt + " attempts.");
                    guessedCorrectly = true;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Incorrect! The number is greater than " + userGuess + ".");
                } else {
                    System.out.println("Incorrect! The number is less than " + userGuess + ".");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've run out of chances. The correct number was: " + numberToGuess);
            }

            // Ask if the user wants to play again
            System.out.print("\nDo you want to play again? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("Thank you for playing! Goodbye!");
        scanner.close();
    }
}
