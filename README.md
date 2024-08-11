import java.util.Random;
import java.util.Scanner;

public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int score = 0;
        boolean playAgain;

        do {
            // Generate a random number between 1 and 100
            int numberToGuess = random.nextInt(100) + 1;
            int numberOfAttempts = 0;
            int maxAttempts = 10;
            boolean guessedCorrectly = false;

            System.out.println("Guess the number between 1 and 100. You have " + maxAttempts + " attempts.");

            // Loop for guessing attempts
            while (numberOfAttempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                numberOfAttempts++;

                // Check the user's guess
                if (userGuess == numberToGuess) {
                    guessedCorrectly = true;
                    score += maxAttempts - numberOfAttempts + 1; // Score based on remaining attempts
                    System.out.println("Congratulations! You've guessed the number correctly in " + numberOfAttempts + " attempts.");
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all your attempts. The correct number was " + numberToGuess);
            }

            System.out.println("Your current score is: " + score);

            // Ask if the user wants to play again
            System.out.print("Do you want to play again? (yes/no): ");
            playAgain = scanner.next().equalsIgnoreCase("yes");

        } while (playAgain);

        System.out.println("Thank you for playing! Your final score is: " + score);
        scanner.close();
    }
}
