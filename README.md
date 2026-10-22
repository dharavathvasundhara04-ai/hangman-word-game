
import random

words = ["python", "apple", "school", "coding", "tiger"]
secret_word = random.choice(words)
guessed_letters = set()
wrong_guesses = 0
max_attempts = 6

print("🎮 Welcome to Hangman!")

while wrong_guesses < max_attempts:
    display = " ".join(
        letter if letter in guessed_letters else "_"
        for letter in secret_word
    )

    print("\nWord:", display)
    print("Wrong guesses:", wrong_guesses, "/", max_attempts)

    if all(letter in guessed_letters for letter in secret_word):
        print("🎉 You won!")
        break

    guess = input("Guess one letter: ").lower().strip()

    if len(guess) != 1 or not guess.isalpha():
        print("Enter only one letter.")
        continue

    if guess in guessed_letters:
        print("Already guessed!")
        continue

    guessed_letters.add(guess)

    if guess in secret_word:
        print("Correct guess!")
    else:
        wrong_guesses += 1
        print("Wrong guess!")

else:
    print("Game over! Word:", secret_word)
    
