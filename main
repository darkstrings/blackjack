import random
game_on = "y"
cards = [11, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]

dealer = {
    "hand" : [],
    "hand_total": 0,
}

player = {
    "hand" : [],
    "hand_total" : 0,
}

def hit(x):
    new_card = random.choice(cards)
    if new_card == 11 and x["hand_total"] >= 12:
        new_card = 1
    x["hand"].append(new_card)
    x["hand_total"] += new_card

def calculate_score():
    if dealer["hand_total"] > player["hand_total"]:
        print(f"Dealer's total is {dealer['hand_total']}\nYour total is {player['hand_total']}\nYou lose")
    elif dealer["hand_total"] < player["hand_total"]:
        print(f"Dealer's total is {dealer['hand_total']}\nYour total is {player['hand_total']}\nYou win!")

def stand():
    if dealer["hand_total"] == 21:
        print("Dealer has blackjack, you lose!")

    while dealer["hand_total"] < 17:
        hit(dealer)
        print(f"Dealer lays a {dealer['hand'][-1]}")
        print(dealer["hand_total"])

        if dealer["hand_total"] > 21:
            print("Dealer busts, you win!")
            return
        elif dealer["hand_total"] == 21:
            print("Dealer has blackjack, you lose!")
            return
        elif dealer["hand_total"] == player["hand_total"]:
            print("draw!")
            return
    if dealer["hand_total"] > 17:
        calculate_score()


def init_players():
    player["hand"] = []
    dealer["hand"] = []
    player["hand_total"] = 0
    dealer["hand_total"] = 0
    for person in range(2):
        hit(player)
        hit(dealer)

def blackjack():
    global game_on
    game_on = input("Do you want to play a game of blackjack? (y/n)\n").lower()
    init_players()
    while game_on == "y":
        print(f"The dealer's hand is {dealer["hand"][0]} and [?]\n"
              f"your hand is {player["hand"]}")
        print(f"Your total is {player["hand_total"]}")
        if player["hand_total"] == 21:
            print("You have blackjack! You win!")
            game_on = input("Play again? (y/n)").lower()
            if game_on == "y":
                init_players()
        else:
            hit_or_stand = input("Would you like to stand or hit? (s/h)").lower()

            if hit_or_stand == "h":
                hit(player)
                if player["hand_total"] > 21:
                    print(f"New total is {player["hand_total"]}\nBust! You lose!")
                    game_on = input("Play again?\n").lower()
                    if game_on == "y":
                        init_players()
            elif hit_or_stand == "s":
                stand()
                game_on = input("Play again?\n").lower()
                if game_on == "y":
                    init_players()

blackjack()
