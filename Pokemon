import random
import requests

#The following code creates a new function to select a random pokemon and return details about it:


def random_pokemon():
    # selects random integer (from the random module):
    pokemon_number = random.randint(1, 151)
    # uses the number chosen to find the relevant url
    url = f'https://pokeapi.co/api/v2/pokemon/{pokemon_number}/'
    # collects the contents of that url:
    response = requests.get(url)
    # puts it into a nicer format:
    pokemon = response.json()
    #returns selected information about the pokemon:
    return {
        'name': pokemon['name'],
        'id': pokemon['id'],
        'height': pokemon['height'],
        'weight': pokemon['weight'],
        'base experience': pokemon['base_experience']
    }


# The following code creates a new function to select a choice of 3 random pokemon for you, one for the opponent,
# shows you features of the pokemon, allows the user to select a feature, says who won based on that feature,
# and saves the final scores in a text file

def run():
    #Set round to 0 to start with, and add one each round
    round = 0
    my_score = 0
    opponent_score = 0

    # The game continue whilst either score is less than 5. 3 random pokemons are selected for the user to choose from:
    while my_score <= 2 and opponent_score <= 2:
        my_pokemon1 = random_pokemon()
        my_pokemon2 = random_pokemon()
        my_pokemon3 = random_pokemon()
        #Prints a row of stars and tells us what round we're in:
        print("*" * 100)
        round = round + 1
        print(f"Round {round} !!!!")
        #Prints information about our pokemon choices:
        print(f"Your pokemon's are : 1.{my_pokemon1['name'].upper()}, 2.{my_pokemon2['name'].upper()} , 3.{my_pokemon3['name'].upper()}")
        pokemon_choice = int(input('Which pokemon do you want to use? 1, 2 or 3 : '))
        if pokemon_choice == 1:
            chosen_pokemon = my_pokemon1
        elif pokemon_choice == 2:
            chosen_pokemon = my_pokemon2
        elif pokemon_choice == 3:
            chosen_pokemon = my_pokemon3
        else:
            print(input('You entered an incorrectly. Try again 1,2 or 3: '))

        print(f"Your chosen pokemon is {chosen_pokemon['name'].upper()} . It's stat's are :")
        print(f" a) id :{chosen_pokemon['id']} , b) height:{chosen_pokemon['height']}, c) weight: {chosen_pokemon['weight']}, d) base experience: {chosen_pokemon['base experience']} ")
        stat_choice = input('Which stat do you want to use? ')
        if stat_choice == 'a':
            chosen_stat = 'id'
        elif stat_choice == 'b':
            chosen_stat = 'height'
        elif stat_choice == 'c':
            chosen_stat = 'weight'
        elif stat_choice == 'd':
            chosen_stat = 'base experience'
        else:
            print(input('You entered incorrectly. Try again: '))

        #Selects a random pokemon for the opponent and tells us its features:
        opponent_pokemon = random_pokemon()
        print(
            f"The opponent chose {opponent_pokemon['name'].upper()} \n It's id: {opponent_pokemon['id']} , It's height:{opponent_pokemon['height']} ,"
            f" It's weight :{opponent_pokemon['weight']} , Base experience:{opponent_pokemon['base experience']}")
        #Comparing the chosen feature of the 2 pokemon and deciding the winner of that round:
        my_pokemons_stat = chosen_pokemon[chosen_stat]
        opponent_stat = opponent_pokemon[chosen_stat]
        print(f"Opponent's chosen stat is :{opponent_pokemon[chosen_stat]}")
        if my_pokemons_stat < opponent_stat:
            print('You lose')
            opponent_score += 1
            print(f" The opponent score is now {opponent_score}. Your score is now {my_score}")
        elif my_pokemons_stat > opponent_stat:
            print('You win')
            my_score += 1
            print(f" The opponent score is now {opponent_score}. Your score is now {my_score}")
        elif my_pokemons_stat == opponent_stat:
            print('It is a draw')
            print(f" The opponent score is now {opponent_score}. Your score is now {my_score}")


    # When someone's score reaches five the game ends:
    if my_score > opponent_score:
        print("The game has finished. You have won.")
        my_score == 2
    elif  my_score < opponent_score:
        print("The game has finished. The opponent won.")
        opponent_score ==  2
    elif  my_score == opponent_score:
        print("It is a draw! ")
    print("*" * 100)
    # Asks user if they wish to continue the game or not
    again = input('Do you want to play again? y/n  ')
    if again.lower() == 'n':
        print("Thanks for playing . Bye !")
    else:
        run()

    #The final score for the game is appended to the text file:

    with open('pokemon.txt', 'a') as text_file:
        text_file.write('\n')
        text_file.write(f" Your score: {my_score}    Opponent score: {opponent_score}")

run()
