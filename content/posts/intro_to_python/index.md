---
title: "Intro to Python"
date: 2022-09-15T21:44:59-07:00
draft: false
tags:
  - code
  - python
categories:
  - programming
---

# TalkPython: Python for Absolute Beginners

## A review by Claudia Althoen

I recently went through the talk python course and below is my review.


Python for Absolute Beginners is a succinct course that both aids as a
refresher and an easy way to get started with Python. Within the course,
there are guided lessons where you follow along in your own coding software,
(in the course, they use PyCharm), and practices you go through on your own
that you can then check with their solutions. All the code, practices,
and solutions for the course can be found on their GitHub site:
https://github.com/talkpython/python-for-absolute-beginners-course
And the URL for the course website is:
https://training.talkpython.fm/courses/details/python-for-absolute-beginners

There were times when I found myself stuck on code, despite following
along with every part in the videos, and if this happens to you, I suggest
checking out the “Code” in the GitHub before you spend too long being
frustrated with the code. It happens a few times when the code was incorrect
or not updated in the videos, but is updated in the GitHub files.
The videos aren’t perfect, but being able to go through bit by bit for
different examples is helpful. With this course, the videos go through
writing software and debugging fun little games that you create, such as
rock paper scissors and tic-tac-toe.

The course starts out with guiding the learner in the basics of why python
is both a powerful and useful language, as well as how to set up Python.
While not perfect in its execution (like most things), chapter two presents helpful guidance
in setting up and using PyCharm, an IDE for Python. I’ve had experiences
before where a course will just show you how to set up an IDE, but not
actually show you how to use each part in the IDE once you finally have
it open. I had that issue for using the debugger in PyCharm—the video in the
course didn’t show you how to make the debugger appear and so the
assumption was that it was already there for you when you click on it,
which was not the case for me. So, I did have to do a bit of googling
to figure out the solution to my issue. Nevertheless, the course has been very
useful just for seeing again and again how to open files, how to name
them, and so on in PyCharm. For an in-depth guide for every single part
of the PyCharm IDE, I suggest doing additional learning outside the course.

Not everything is explained in the course, but enough was so that I felt
like I walked away from the course having a good, basic understanding of python
and using PyCharm as an IDE. There were some things that were used in
the videos without a brief explanation as to why, but as you go along
in the course, your brain eventually has the ‘aha’ moment (or it is
explained in the video later on). If not, it was easy enough to search for it
on the internet.

There are three programs you will code in the course: an M&M guessing
game, rock paper scissors, and tic-tac-toe.

One of my favorites to code was the M&M guessing game mainly because of
how much fun it was to get creative with it when it said in the practice
to remake the guessing game. I printed
`print("  - - - - - - - - - -")`
in the shape of a jar, added sarcastic responses if the user did not guess
correctly, and different responses depending on how many guesses it took
to get right. For example, if the user responded with their nationality
as Canadian, I shrunk the range of possibility for the right guess to
help the user out by saying that Tim Hortons M&M-napped some M&Ms
for timbits and now the range they’re guessing from is ___.

```python
elif nationality == 2:
    print("The number of M&Ms lies between 400 to 700, eh...
           "Tim Hortons M&M-napped the others for timbits...they were delicious.")
```

Like with writing, a book, every author of their code does things and expresses things a
bit differently, but the underlying structure remains: sentences,
punctuation, a story arc or purpose, etc.

Looking back at my code compared to what I learned in further lessons of the
course, there is definitely a lot to change and improve on, but the fact that
I can see where I can improve in my code means that I learned more than I
thought I did. I was able to apply what I learned, and I left feeling a
desire to keep learning and exploring all the things code can do for us.

The ability for the user to interact efficiently with whatever program you’ve
written is important. In the course, changing the color of font is introduced
by using colorama, an external library.

```python
from colorama import Fore

while not find_winner(wins, wins.keys()):
    roll1 = get_roll(player_1, roll_names)
    roll2 = random.choice(roll_names)

    if not roll1:
        print(Fore.LIGHTRED_EX + "Try again!")
        print(Fore.WHITE)
        continue
```

In this code above, font colors from colorama is imported into the program.
The text for "Try again!" becomes light red and the text for "continue" is
white.

Being able to change the color of the font is important if you don’t want your user to
get frustrated or annoyed; you want them to be able to quickly understand what is going on.

The code below is an example of using an F string. So, in this code, the user
is asked to guess the number of M&Ms in the jar as long as their attempt
limit is under the max allowed.

```python
while attempts < attempt_limit:
    guess_text = input("How many M&Ms are in the jar?")
    guess = int( guess_text)
    attempts += 1

    if mm_count == guess:
        print(f"You got a free lunch! It was {guess}.")
        #attempts = attempt_limit
        break
````

If they guessed correctly, the program would tell them that they got a
free lunch and what the guess was.

One of the practice exercises afterwards was to remake the m&m guessing game,
but in your own way, so I changed the above code to:

```python
while attempts < attempt_limit:
    guess_question = input("How many M&Ms are there?")
    guess = int(guess_question)
    attempts += 1
    if guess == mm_count:
        if attempts <= 2:
            print(f"It only took you {attempts} attempt(s)! Hot diggity damn ☜（ﾟ∀ﾟ☜) ")
            break
        if 3 <= attempts <= 6:
            print(f"It took you {attempts} attempts. Here's a participation medal🏅.
                  f"Ride that high for as long as you need.")
            break
        if attempts >= 7:
            print(f"You're right, but oof, {attempts} attempts." )
            break
    if attempts == 10:
        print("That's rough, buddy. Better luck next time.")
        break
```

I wanted to play around with segmenting the successful attempts and to have fun
with the responses to however many it took the user to guess correctly. I had 10 as the
max attempt limit.

In making the rock paper scissors game, I got a lot of practice with defining functions:

```python
def show_leaderboard():
    leaders = load_leaders()

    sorted_leaders = list(leaders.items())
    sorted_leaders.sort(key=lambda l: l[1], reverse=True)

    print()
    print("---------------------------")
    print("LEADERS:")
    for name, wins in sorted_leaders[0:5]:
        print(f"{wins:,} -- {name}")
    print("---------------------------")
    print()
```

And another example:

```python
def check_for_winning_throw(player_1, player_2, roll1, roll2):
    winner = None
    if roll1 == roll2:
        print("The play was tied!")

    outcome = rolls.get(roll1, {})
    if roll2 in outcome.get('defeats'):
        return player_1
    elif roll2 in outcome.get('defeated_by'):
        return player_2

    return winner
```
The course also spent time teaching about dictionaries and creating virtual
environments. For the rock paper scissor game, there was a task of importing and
using JSON, which is very similar to dictionaries in Python.

Instead of having all of this as part of the program code

```python
{
    "rock": {
        "defeats": ["fire", "scissors", "sponge"],
        "defeated_by": ["paper", "air", "water"]
    },
    "paper": {
        "defeats": ["rock", "water", "air"],
        "defeated_by": ["scissors", "fire", "sponge"]
    },
    "scissors": {
        "defeats": ["paper", "sponge", "air"],
        "defeated_by": ["fire", "rock","water"]
    },
    "fire": {
        "defeats": ["scissors", "sponge", "paper"],
        "defeated_by": ["rock", "water", "air"]
    },
    "sponge": {
        "defeats": ["paper", "air", "water"],
        "defeated_by": ["rock", "fire", "scissors"]
    },
    "air": {
        "defeats": ["water", "rock", "fire"],
        "defeated_by": ["paper", "sponge", "scissors"]
    },
    "water": {
        "defeats": ["rock", "fire", "scissors"],
        "defeated_by": ["air", "paper", "sponge"]
    }
}
```

I was able to make this as a json file called 'rolls.json'. In the Pyscript,
I simply have to call it.

```python
rolls = {}
```

Another subject that the course covered was error handling. Now, whenever I
write code, I think about "how can this code 'break' and what can I do to
prevent it?"

For example, when making the Connect 4 game (similar code to tictactoe), there
was an issue when telling the program what location you choose.
When it asked "Choose which column: ", it was very simple to break it just by
putting in extra numbers or mistyping.

```python
def choose_location(board, symbol, is_computer):
    if not is_computer:
        column = int(input(Fore.YELLOW + "Choose which column: " + Fore.WHITE))
    else:
        column = random.randint(1, len(board[0]))
        print(Fore.YELLOW + f"Computer chooses column {column}" + Fore.WHITE)

    column -= 1
    if column < 0 or column >= len(board[0]):
        return False

    row = find_bottom_row(board, column)
    if row is None:
        return False

    cell = board[row][column]
    if cell is not None:
        return False

    board[row][column] = symbol
    return True
```

Therefore, in order to mitigate this issue, this was the solution:

```python
def choose_location(board, symbol): #game would crash hard if you put wrong location
    try:
        row = int(input("Choose which row: "))

        row -= 1
        if row < 0 or row >= len(board):
            return False

        column = int(input("Choose which column: "))
        column -= 1
        if column < 0 or column >= len(board[0]):
            return False

        cell = board[row][column]
        if cell is not None:
            return False

        board[row][column] = symbol
        return True
    except ValueError as ve:
        print(f"Error: Cannot convert input to a number.")
        return False
```

With this solution to the error, now the game won't break and quit out of the
program.

This course alone isn't an 'ends all' way to being an expert in Python, of course,
but the hands-on approach and the ease to which I was able to follow along,
has made it easy to use what I learn from this course and apply it to
further learning, so I recommend giving the course a try!
