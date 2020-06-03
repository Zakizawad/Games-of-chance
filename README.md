# Games-of-chance
This is a test project i made from codecademy using python
The code is written below

import random

money = 100

#Write your game of chance functions here
def coins(guess,bet):
  #money=100
  if bet>100 or bet<=0:
    return print("Invalid bet")
  print(">>>Playing Coins")
  result=random.randint(0,1)
  if result==0:
    res="Heads"
  else:
    res="Tails"
  print("Result is",res)
  if guess=="Heads" or guess=="heads" or guess=="Heads!" or guess=="HEADS":
    guess="Heads"
  elif guess=="Tails" or guess=="tails" or guess=="Tails!" or guess=="TAILS":
    guess="Tails"
  if res==guess:
    #money+=bet
    print("You Won!")
    print("You won", bet, "money")
    print(">>>the game has ended")
    return bet
  else:
    #money-=bet
    print("you lost!")
    print("you lost", bet , "money" )
    print(">>>the game has ended")
    return -bet

def Cho_Han(guess,bet):
  if bet>money or bet<=0:
    return print("Invalid bet")
  print(">>>Playing Cho-Han")
  num=random.randint(2,12)
  if num%2==0:
    res="Even"
    print("The number is Even")
  else: 
    res="Odd"
    print("The number is Odd")
  if res==guess:
    print("You guessed Right!")
    print("You won",bet, "money")
    print(">>>the game has ended")
    return bet
  else:
    print("You guessed Wrong!")
    print("you lost",bet,"money")
    print(">>the game has ended")
    return -bet

def Decks(bet):
  if bet>money or bet<=0:
    return print("Invalid bet")
  print(">>>playing Decks")
  play1=random.randint(1,10)
  play2=random.randint(1,10)
  if play1>play2:
    print("You have the greater number, You Won!")
    print("you won",bet,"money")
    print(">>>The game has ended")
    return +bet
  elif play1==play2:
    print("Its a TIE!")
    print("No money earned or lost")
    print(">>>the game has ended")
    return 0
  else:
    print("You lost!")
    print("you lost",bet,"money")
    print(">>>the game has ended")
    return -bet

def Deck(bet):
  if bet>money or bet<=0:
    return print("Invalid bet")
  print(">>>playing Deck")
  deck=list(range(1,11))
  #print(deck)
  play1=random.choice(deck)
  deck.remove(play1)
  play2=random.choice(deck)
  if play1>play2:
    print("You have the greater number, You Won!")
    print("you won",bet,"money")
    print(">>>The game has ended")
    return +bet
  elif play1==play2:#this wont be used
    print("Its a TIE!")
    print("No money earned or lost")
    print(">>the game has ended")
    return 0
  else:
    print("You lost!")
    print("you lost",bet,"money")
    print(">>the game has ended")
    return -bet


def roulette(guess,bet):
  if bet>money or bet<=0:
    return print("Invalid bet")
  print(">>>playing roulette")
  if guess=="Odd" or guess=="Even":
    board=["00"]+list(range(37))
    num=random.choice(board)
    if num=="00" or num==0:
      print("The result is", num, "You lost!")
      print("You lost", bet, "money")
      return -bet
    else:
      result=(num%2)
      if result==0 and (guess=="Even" or guess=="even" or guess=="EVEN"):
        print("you won the bet!")
        print("you got", bet , " money")
        return +bet
      elif result==1 and (guess=="Odd" or guess=="ODD" or guess=="odd"):
        print("you won the bet!")
        print("you got", bet, "money")
        return +bet
      else:
        print("you lost the bet!")
        print("you lost", bet , "money")
        return -bet
      
  elif guess=="High" or guess=="Low":
    board=["00"]+list(range(37))
    num=random.choice(board)
    if num=="00" or num==0:
      print("The result is", num, "You lost!")
      print("You lost", bet, "money")
      return -bet
    else:
      #result=(num%2)
      if num>=19 and (guess=="High" or guess=="high" or guess=="HIGH"):
        print("you won the bet!")
        print("you got", bet , " money")
        return +bet
      elif num<19 and (guess=="Low" or guess=="LOW" or guess=="low"):
        print("you won the bet!")
        print("you got", bet, "money")
        return +bet
      else:
        print("you lost the bet!")
        print("you got", bet, "money")
        return -bet

  else:
    board=["00"]+list(range(37))
    num=random.choice(board)
    if guess==num:
      print("lottery number",num)
      print("you won the bet!")
      print("you got", bet, "money")
      return +bet
    else:
      print("lottery number",num)
      print("you lost the bet!")
      print("you got", bet, "money")
      return -bet



#experiment function
def s(w):
  deck=list(range(6))
  o=random.choice(deck)
  deck.remove(o)
  p=random.choice(deck)
  print(deck)
  print(o)
  print(p)




#Call your game of chance functions here
try:
  money+=coins("Heads",110)
  print("$$$Current money",money)
except TypeError:
  print("The game is terminated")
try:
  money+=Cho_Han("Odd",30)
  print("$$$Current money",money)
except TypeError:
  print("The game is terminated")
try:
  money+=Decks(20)
  print("$$$Current money",money)
except TypeError:
  print("The game is terminated")
try:
  money+=Deck(20)
  print("$$$Current money",money)
except TypeError:
  print("The game is terminated")
try:
  money+=roulette("odd",20)
  print("$$$Current money",money)
except TypeError:
  print("The game is terminated")

print("Total money after the game", money)
