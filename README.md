# my-project
Hangman is a classic word-guessing game that has been implemented using Python. In this game, the player must guess the word chosen by the computer by suggesting letters. The player has a limited number of incorrect guesses before the game is over.
Here's the simple code 
import random

def get_word():
    words = ['python', 'hangman', 'challenge', 'programming', 'github']
    return random.choice(words)

def display(word, guessed):
    display_word = ''
    for letter in word:
        if letter in guessed:
            display_word += letter + ' '
        else:
            display_word += '_ '
    return display_word.strip()

def hangman():
    word = get_word()
    guessed = []
    attempts = 6

    print("Welcome to Hangman!")
    print(display(word, guessed))

    while attempts > 0:
        guess = input("Guess a letter: ").lower()
        if guess in guessed:
            print(f"You already guessed {guess}. Try again.")
            continue

        guessed.append(guess)
        if guess in word:
            print(f"Good guess! {guess} is in the word.")
        else:
            attempts -= 1
            print(f"Wrong guess! {guess} is not in the word. You have {attempts} attempts left.")

        current_display = display(word, guessed)
        print(current_display)

        if "_" not in current_display:
            print("Congratulations! You guessed the word.")
            break
    else:
        print(f"Sorry, you ran out of attempts. The word was '{word}'.")

if __name__ == "__main__":
    hangman()
