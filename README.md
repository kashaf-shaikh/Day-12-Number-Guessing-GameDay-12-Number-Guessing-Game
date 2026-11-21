# Day 12 – Number Guessing Game

## Project Overview

This project is a command-line Number Guessing Game built using Python.

In this game, the computer randomly selects a number between 1 and 100, and the player has to guess that number within a limited number of attempts.

The game provides hints after each guess:
- "Too high" if the guessed number is greater than the actual number.
- "Too low" if the guessed number is smaller than the actual number.

The player can choose between two difficulty levels:

- **Easy:** 10 attempts.
- **Hard:** 5 attempts.

The game continues until the player guesses the correct number or runs out of attempts.

This project is part of my **100 Days of Python** learning journey.

## Features

- **Random Number Generation:** Selects a random number between 1 and 100.
- **Two Difficulty Levels:** Choose between Easy and Hard modes.
- **Limited Attempts:** Each difficulty level provides a different number of guesses.
- **Guess Feedback:** Displays whether the guess is too high or too low.
- **Attempts Counter:** Shows how many attempts are remaining.
- **Win Condition:** Announces when the player guesses the correct number.
- **Lose Condition:** Displays a message when all attempts are used.

## How the Program Works

### 1. Importing Modules

The project imports `randint` from Python's `random` module and the game logo from `art.py`.

```python
from random import randint
from art import logo
```

- `randint()` generates a random integer within a specified range.
- `logo` displays the game logo.

### 2. Defining Difficulty Levels

Two constants are created to store the number of attempts for each difficulty level.

```python
EASY_LEVEL_TURNS = 10
HARD_LEVEL_TURNS = 5
```

- Easy mode provides 10 attempts.
- Hard mode provides 5 attempts.

### 3. Creating the check_answer() Function

This function compares the user's guess with the actual answer.

```python
def check_answer(user_guess, actual_answer, turns):
    if user_guess > actual_answer:
        print("Too high.")
        return turns - 1

    elif user_guess < actual_answer:
        print("Too low.")
        return turns - 1

    else:
        print(f"You got it! The answer was {actual_answer}")
```

**How it works:**

- If the guess is greater than the answer, it displays "Too high."
- If the guess is smaller than the answer, it displays "Too low."
- If both numbers match, it displays a winning message.
- For an incorrect guess, the function reduces the remaining attempts by one.

### 4. Creating the set_difficulty() Function

This function asks the player to select a difficulty level.

```python
def set_difficulty():
    level = input("Choose a difficulty. Type 'easy' or 'hard': ")

    if level == "easy":
        return EASY_LEVEL_TURNS
    else:
        return HARD_LEVEL_TURNS
```

The function returns the number of attempts based on the selected difficulty.

### 5. Creating the game() Function

This is the main function responsible for running the game.

It performs the following tasks:

1. Displays the game logo.
2. Welcomes the player.
3. Generates a random number between 1 and 100.
4. Asks the player to select a difficulty.
5. Initializes the guessing loop.
6. Displays the remaining attempts.
7. Takes a guess from the player.
8. Calls `check_answer()` to check the guess.
9. Continues the game until the player wins or runs out of attempts.

### 6. Controlling the Game with a While Loop

The game uses a `while` loop to keep asking for guesses until the guessed number matches the answer.

```python
while guess != answer:
    print(f"You have {turns} attempts remaining to guess the number.")

    guess = int(input("Make a guess: "))

    turns = check_answer(guess, answer, turns)

    if turns == 0:
        print("You've run out of guesses, you lose.")
        return

    elif guess != answer:
        print("Guess again.")
```

The loop continues while the player's guess is different from the actual answer.

If the remaining attempts become zero, the game ends.

### 7. Starting the Game

Finally, the `game()` function is called to start the program.

```python
game()
```

## Example Output

The following is an illustrative example. The actual answer is generated randomly each time.

```text
Welcome to the Number Guessing Game!
I'm thinking of a number between 1 and 100.

Choose a difficulty. Type 'easy' or 'hard': easy

You have 10 attempts remaining to guess the number.
Make a guess: 70
Too high.
Guess again.

You have 9 attempts remaining to guess the number.
Make a guess: 40
Too low.
Guess again.

You have 8 attempts remaining to guess the number.
Make a guess: 55
You got it! The answer was 55
```

## Python Concepts Used

| Concept | How It Is Used |
|---|---|
| Functions | Dividing the game into smaller tasks |
| Parameters | Passing guesses, answers and attempts to functions |
| Return Statement | Returning the remaining attempts |
| Random Module | Generating a random number |
| `randint()` | Selecting a number between 1 and 100 |
| Constants | Storing difficulty-level attempts |
| Global Constants | Sharing difficulty values across functions |
| If-Elif-Else | Comparing guesses and checking conditions |
| While Loop | Repeating the guessing process |
| User Input | Taking difficulty and number guesses |
| Type Conversion | Converting user input into an integer |
| Boolean Comparisons | Checking whether the guess matches the answer |
| Modules | Importing the logo from another Python file |

## Project Structure

```text
Day-12-Number-Guessing-Game/
│
├── main.py       # Main game logic
├── art.py        # Game logo and ASCII art
└── README.md     # Project documentation
```

## How to Run the Project

### Prerequisites

- Python 3 installed on your system.
- VS Code, PyCharm or another Python code editor.

### Steps

**1. Clone the repository**

```bash
git clone YOUR_REPOSITORY_URL
```

**2. Navigate to the project folder**

```bash
cd Day-12-Number-Guessing-Game
```

**3. Run the program**

```bash
python main.py
```

## Current Project Limitations

- The program does not validate invalid difficulty inputs.
- The program does not validate non-numeric guesses.
- The correct answer is currently printed in the terminal for testing.
- The game runs once and does not provide a replay option.

## What I Learned

Through this project, I practised:

- Generating random numbers using Python.
- Creating functions to organize program logic.
- Passing information between functions using parameters.
- Returning updated values from functions.
- Using constants to manage game settings.
- Applying conditional statements to compare numbers.
- Using while loops to repeat a guessing process.
- Managing game attempts and implementing win and lose conditions.

## Learning Journey

**100 Days of Python – Day 12**

This project helped me understand how functions, loops, conditions and random number generation can work together to create an interactive game.