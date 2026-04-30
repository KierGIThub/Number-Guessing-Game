import random

# Function to play a level of the game
def play_level(max_number, level_name):
    best = None

    while True:
        print(f"\nWelcome to {level_name} (1-{max_number})")
        number_to_guess = random.randint(1, max_number)
        attempts = 0

        while True:
            try:
                guess = int(input(f"Enter your guess (1-{max_number}): "))

                if guess < 1 or guess > max_number:
                    print("Out of range.")
                    continue

                attempts += 1

                if guess == number_to_guess:
                    print(f"Correct! Attempts: {attempts}")
                    if best is None or attempts < best:
                        best = attempts
                        print(f" New best score: {best} attempts!")

                    print(f"Best score so far: {best}")
                    break

                elif guess < number_to_guess:
                    print("Too low!")
                else:
                    print("Too high!")

            except ValueError:
                print("Invalid input.")

        play_again = input("Play again? (yes/no): ").strip().lower()
        if play_again not in ("yes", "y"):
            break

#Main menu to select difficulty level and start the game
def main():
    print("========== Welcome to the Number Guessing Game! ==========\n")

    while True:
        print("\nChoose a level:")
        print("1. Easy (1-10)")
        print("2. Medium (1-50)")
        print("3. Hard (1-100)")
        print("4. Exit")

        choice = input("Enter your choice (1/2/3/4): ").strip()

        if choice == '1':
            play_level(10, "Easy")
        elif choice == '2':
            play_level(50, "Medium")
        elif choice == '3':
            play_level(100, "Hard")
        elif choice == '4':
            print("Thanks for playing!")
            break
        else:
            print("Invalid choice.")


if __name__ == "__main__":
    main()
