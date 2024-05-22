# TODO-1: - Update the word list to use the 'word_list' from hangman_words.py
# Delete this line: word_list = ["ardvark", "baboon", "camel"]
from hangman_words import word_list

chosen_word = random.choice(word_list)
word_length = len(chosen_word)

end_of_game = False
lives = 6

# TODO-3: - Import the logo from hangman_art.py and print it at the start of the game.
from hangman_art import logo

print(logo)

# Testing code
print(f'Pssst, the solution is {chosen_word}.')

# Create blanks
display = []
for _ in range(word_length):
    display += "_"

while not end_of_game:
    guess = input("Guess a letter: ").lower()

    # TODO-4: - If the user has entered a letter they've already guessed, print the letter and let them know.
    if guess in display:
        print(f"You've already guessed {guess}")

    # Check guessed letter
    for position in range(word_length):
        letter = chosen_word[position]
        # print(f"Current position: {position}\n Current letter: {letter}\n Guessed letter: {guess}")
        if letter == guess:
            display[position] = letter

    # Check if user is wrong.
    if guess not in chosen_word:
        # TODO-5: - If the letter is not in the chosen_word, print out the letter and let them know it's not in the word.
        print(f"You guessed {guess}, that's not in the word. You lose a life.")

        lives -= 1
        if lives == 0:
            end_of_game = True
            print("You lose.")

    # Join all the elements in the list and turn it into a String.
    print(f"{' '.join(display)}")

    # Check if user has got all letters.
    if "_" not in display:
        end_of_game = True
        print("You win.")

    # TODO-2: - Import the stages from hangman_art.py and make this error go away.
    from hangman_art import stages

    print(stages[lives])
ChatGPT
markdown
Copiar código
# Hangman Game

A simple hangman game implemented in Python.

## Instructions

1. Update the word list to use the 'word_list' from `hangman_words.py`.
2. Import the logo from `hangman_art.py` and print it at the start of the game.
3. If the user has entered a letter they've already guessed, print the letter and let them know.
4. If the letter is not in the chosen word, print out the letter and let them know it's not in the word.
5. Import the stages from `hangman_art.py` and make the error go away.

## How to Play

1. A random word is chosen from the word list.
2. The player has 6 lives initially.
3. Guess a letter for the word.
4. If the guessed letter is correct, it will be revealed in the word.
5. If the guessed letter is incorrect, the player loses a life.
6. Keep guessing letters until the word is completely revealed or all lives are lost.

## Usage

Run the script and follow the on-screen instructions.

```python
python hangman.py
Dependencies
Python 3.x
hangman_words.py
hangman_art.py
Credits
This project is based on the Python Hangman project from the "100 Days of Code - The Complete Python Pro Bootcamp for 2021" by Dr. Angela Yu.
