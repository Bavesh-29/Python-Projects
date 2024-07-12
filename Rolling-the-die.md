import random

def roll():
    min_value=1
    max_value=6
    roll=random.randint(min_value, max_value)
    
    return roll

while True:
    players=input("Enter the number of players(2-4): ")
    if players.isdigit():
        players=int(players)
        if 2<= players <=4:
            break
        else:
            print("Players must be in between (2-4)")
    else:
        print("Enter valid number for players")
        
max_score = 50
players_scores = [0 for i in range(players)]

while max(players_scores) < max_score:
    for players_number in range(players):
        print("Player number", players_number + 1,"turn has just started\n")
        print("Your total score is:", players_scores[players_number])
        current_score = 0
        
        while True:
            should_score = input("Would you like to roll (y) ?")
            if should_score.lower() != 'y':
                break
            
            value = roll()
            if value == 1:
                print("You rolled 1, Turn over")
                current_score = 0
                break
            else:
                current_score = current_score + value
                print("You rolled",value)
                
            print("Your current score is", current_score)
        players_scores[players_number] += current_score
        print("Your total score is: ", players_scores[players_number])
        
max_score=max(players_scores)
winning_idx = players_scores.index(max_score)
print("Player number", winning_idx+1,\
      "is the winner with score of :", max_score)
