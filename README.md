Hangman Game README
Overview
This is a simple Hangman game implemented in Python. The player needs to guess the letters of a randomly chosen word. The player has a limited number of incorrect guesses (lives). The game ends when the player either guesses the word correctly or runs out of lives.

Files
Main Script
The main game logic is contained in this script.

hangman_words.py
This file contains a list of words (word_list) that the game will randomly choose from.

hangman_art.py
This file contains the ASCII art for the game logo and the different stages of the hangman.

How to Play
Start the Game: Run the main script to start the game.
Game Display: The game will display the hangman logo at the start.
Word to Guess: The game will randomly choose a word from word_list. This word will not be shown to the player.
Guessing: The player will guess letters one at a time.
Feedback:
If the player guesses a letter correctly, it will be revealed in the word.
If the player guesses a letter that has already been guessed, a message will be displayed.
If the player guesses incorrectly, a message will be displayed and the player will lose a life.
End of Game:
The game will continue until the player either guesses the word or loses all their lives.
If the player loses all their lives, a "You lose" message will be displayed along with the hangman at its final stage.
If the player guesses the word, a "You win" message will be displayed.
Code Walkthrough
python
Copiar código
import random
from hangman_words import word_list
from hangman_art import logo, stages

# Randomly choose a word from the word list
chosen_word = random.choice(word_list)
word_length = len(chosen_word)

end_of_game = False
lives = 6

# Display the game logo
print(logo)

# Debugging: Show the chosen word (can be removed for actual gameplay)
print(f'Pssst, the solution is {chosen_word}.')

# Create blanks for the chosen word
display = ["_" for _ in range(word_length)]

while not end_of_game:
    guess = input("Guess a letter: ").lower()

    # Check if the player has already guessed the letter
    if guess in display:
        print(f"You've already guessed {guess}")

    # Check if the guessed letter is in the chosen word
    for position in range(word_length):
        letter = chosen_word[position]
        if letter == guess:
            display[position] = letter

    # If the guessed letter is not in the chosen word, decrement the lives
    if guess not in chosen_word:
        print(f"You guessed {guess}, that's not in the word. You lose a life.")
        lives -= 1
        if lives == 0:
            end_of_game = True
            print("You lose.")

    # Display the current state of the guessed word
    print(f"{' '.join(display)}")

    # Check if the player has guessed the entire word
    if "_" not in display:
        end_of_game = True
        print("You win.")

    # Display the current stage of the hangman
    print(stages[lives])
TODOs
Update Word List:

The word list should be imported from hangman_words.py instead of being defined in the main script.
Import Stages:

Import the stages from hangman_art.py at the start of the script.
Display Logo:

Import and display the logo from hangman_art.py at the start of the game.
Repeated Guesses:

Implement a check to notify the player if they have already guessed a letter.
Incorrect Guesses:

Notify the player if the guessed letter is not in the word.
Additional Notes
The debugging print statement showing the solution (print(f'Pssst, the solution is {chosen_word}.')) should be removed or commented out in the final version of the game.
Ensure that hangman_words.py and hangman_art.py are in the same directory as the main script or update the import statements accordingly.
Conclusion
This Hangman game is a fun way to practice Python programming and understand basic game logic. The TODOs listed in the code are simple enhancements that can be made to improve the game experience. Enjoy playing and coding!
