# Guessing-a-number-game
import random
from art import logo

EASY_LEVEL_GUESS = 10
HARD_LEVEL_GUESS = 5

def guess_number():
  number = random.choice(range(1,100))
  return number

def compare(user_guess, computer_guess):  
  if user_guess > computer_guess:
    print("Too high")
    print("Guess again")
  elif user_guess < computer_guess:
    print("Too low")
    print("Guess again")
    
def play_game():  
  print(logo)
  print("Welcome to the number guessing game! ")
  print("I am thinking of a number between 1 and 100 ")    
  computer_guess = guess_number()
  print(f"the correct answer : {computer_guess}")
 
  
  difficulty = input("Choose a difficulty. Type 'easy' or 'hard': ")
  if difficulty == 'hard':
    turns = HARD_LEVEL_GUESS
    print(f"You have {turns} attemps remeaning to guess the number. ")   
    user_guess = int(input("Make a guess: "))
    while not user_guess == computer_guess:   
      compare(user_guess, computer_guess)
      turns -=1
      print(f"You have {turns} attemps remeaning to guess the number. ")
      user_guess = int(input("Make a guess: "))
      if user_guess == computer_guess:        
        print(f"You got it. The answer was: {computer_guess}")
      elif turns == 1:
        print("You've run out of guesses. You lose! ")
        return
  elif difficulty == 'easy':    
    turns = EASY_LEVEL_GUESS    
    print(f"You have {EASY_LEVEL_GUESS} attemps remeaning to guess the number. ")  
    user_guess = int(input("Make a guess: "))
    while not user_guess == computer_guess:
      compare(user_guess, computer_guess)
      turns -= 1
      print(f"You have {turns} attemps remeaning to guess the number. ")
      user_guess = int(input("Make a guess: "))      
      if user_guess == computer_guess:
        print(f"You got it. The answer was: {computer_guess}")
      elif turns == 1:
        print("You've run out of guesses. You lose! ")
        return
play_game()  
