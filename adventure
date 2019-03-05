import random
import sys
class PC(object): 
  def __init__(self, health, strength, magic, ranged, damage, name):
    self.health = health
    self.strength = strength 
    self.magic = magic
    self.ranged = ranged
    self.name = name
    self.max_damage = damage
  def get_damage(self,attack):
    if attack == "strength":
      self.max_damage = self.strength
      return random.randint(1, self.max_damage)
    elif attack == "ranged":
      self.max_damage = self.ranged
      return random.randint(1, self.max_damage)
    else:
      self.max_damage = self.magic
      return random.randint(1, self.max_damage)
inventory = ["sword", "bow and arrow", "staff"]
def checkinventory():
  print(', '.join(inventory))
def inputter(question, chartype, minvalue, maxvalue):
  while True:
    print(question)
    x = input("\t> ")
    try:
      x = int(x)
      if x >= minvalue and x <= maxvalue:
        break
      elif minvalue == maxvalue:
        print("sorry your answer can't be a number")
      elif x < minvalue:
        print("sorry that number is too low")
      elif x > maxvalue:
        print("sorry that number is too big")
    except:
      if chartype == "int":
        print("sorry it needs to be a number.")
      if x == "check inventory":
        checkinventory()
      elif chartype == "string":
          break
  return x
def playerturn(question, enemy):
  while True:
    attack = inputter(question, "string", 0, 0)
    if attack in inventory:
      if "sword" in attack:
        damage = player_character.get_damage("strength")
        enemy.health -= damage
        print("You swing your sword and deal", damage, "damage to the", enemy.name)
        break
      elif "bow" in attack:
        damage = player_character.get_damage("ranged")
        enemy.health -= damage
        print("You shoot an arrow and deal", damage, "damage to the", enemy.name)
        break
      elif "staff" in attack:
        damage = player_character.get_damage("magic")
        enemy.health -= damage
        print("You cast a spell and deal", damage, "damage to the", enemy.name)
        break
      elif "torch" in attack:
        damage = player_character.get_damage("strength") + 2
        enemy.health -= damage
        print("You swing the torch and deal", damage, "damage to the", enemy.name)
    else:
      print("sorry I don't understand, please try again.")
def enemyturn(enemy, strengthmin, magicmin, rangedmin):
  possible_numbers = []
  if enemy.strength > strengthmin:
    possible_numbers.append(1)
  if enemy.magic > magicmin:
    possible_numbers.append(2)
  if enemy.ranged > rangedmin:
    possible_numbers.append(3)
  while True:
    attack = random.randint(1, 3)
    if attack in possible_numbers:
      if attack == 1:
        damage = enemy.get_damage("strength")
        player_character.health -= damage
        print("the enemy uses a strength attack and deals", damage, "damage to you")
        break
      if attack == 2:
        damage = enemy.get_damage("magic")
        player_character.health -= damage
        print("the enemy uses a magic attack and deals", damage, "damage to you")
        break
      if attack == 3:
        damage = enemy.get_damage("ranged")
        player_character.health -= damage
        print("the enemy uses a ranged attack and deals", damage, "damage to you")
        break
def start(): #gives player their stats
  player_character.name = inputter("First, what is your name?", "string", 0,0)
  print("""You begin your journey at dawn.
  You have 11 points to spend between your four stats:
  health, magic, strength, and ranged.""")
  x = inputter("""How many points would you like to put into health?""", "int", 1, 8)
  points_used = x
  player_character.health += x
  print(points_used, "points used")
  x = inputter("""How many points would you like to put into strength?""", "int", 1, 9 - points_used)
  points_used += x
  player_character.strength += x
  print(points_used, "points used")
  x = inputter("""How many points would you like to put into magic?""", "int", 1, 10 - points_used)
  points_used += x
  player_character.magic += x
  print(points_used, "points used")
  x = inputter("""How many points would you like to put into ranged?""", "int", 1, 11 - points_used)
  points_used += x
  player_character.ranged += x
  print(points_used, "points used")
def tutorialfight():
  spider = PC(3,2,1,1,1,"spider")
  print("""You are entering your first fight. Its against a simple spider.""")
  while True:
    playerturn("""Your weapons are a sword, bow and arrow, and a staff; which would you like to use?""", spider)
    if spider.health < 0:
      spider.health = 0
    if spider.health < 1:
      print("""You have killed the spider. Congratulations. You will now enter the main game, if you run out of health now you will die and have to retry, good luck!""")
      break
    else:
      enemyturn(spider, 1, 1, 1)
  print("Use the command 'help' to see available commands whenever not sure.")
def genericfight(attacker, defender):
  if attacker == player_character:
    while True:
      playerturn(f"You have {', '.join(inventory)} what would you like to use?", defender)
      if defender.health < 0:
        defender.health = 0
      if defender.health < 1:
        print("You have killed the", defender.name, "!")
        break
      else:
        enemyturn(defender, 1, 1, 1)
        if attacker.health < 0:
          attacker.health = 0
        if attacker.health < 1:
          print("""You fought a valiant battle, but everyone's battle must come to an end.
          Please try again some time.""")
          sys.exit()
  else:
    while True:
      enemyturn(attacker, 1, 1, 1)
      if defender.health < 0:
        defender.health = 0
      if defender.health < 1:
        print("""You fought a valiant battle, but everyone's battle must come to an end.
        Please try again some time.""")
        sys.exit()
      else:
        playerturn(f"You have {', '.join(inventory)} what would you like to use?", defender)
        if attacker.health < 0:
          attacker.health = 0
        if attacker.health < 1:
          print("You have killed the", defender.name, "!")
          break
def cave():
  print("You have found yourself in a large cave with torches lighting the path deeper in.")
  while True:
    x = inputter("Would you like to go further in?", "string", 0, 0)
    if "torch" in x:
      inventory.append("torch")
      print("you take the torch and head deeper into the cavern.")
      cavefight1()
      break
    elif "no" in x:
      print("""You leave the cave, never knowing what kind of adventure was ahead of you.
      What a shame""")
      sys.exit()
    elif "yes" in x:
      print("You head down into the dark cave")
      cavefight1()
      break
    else:
      print("I'm not sure what that means")
  print("You find yourself on the other side of the cave. good job.")
def cavefight1():
  dragon = PC(4,2,2,2,1,"dragon")
  if "torch" in inventory:
    print("the torch helps you see a sleeping dragon ahead.")
    while True:
      x = inputter("Do you want to fight it?", "string", 0, 0)
      if "yes" in x:
        genericfight(player_character, dragon)
        break
      elif "no" in x:
        print("You creep around the dragon and find a pile of coins and a shield.")
        x = inputter("Do you go for the coins or the shield?", "string", 0, 0)
        if "coins" in x:
          print("you reach for the coins but the dragon swings its tail and attacks you")
          genericfight(dragon, player_character)
          break
        elif "shield" in x:
          print("You reach for the shield and sneak past the dragon.")
          player_character.health += 2
          break
      else:
        print("im not sure what that means.")
  else:
    print("from the dark a dragon swings its tail at you and hits you.")
    genericfight(dragon, player_character)
player_character = PC(1,1,1,1,1,"player_character")
start()
tutorialfight()
cave()
