# Text_Adventure_Game_python
Designing a Text-Based Adventure Game in Python
Author: BurcuDogru   
    
"""
DocString:
    
    A) Introduction:
    This game is created to be a part of a music exhibition for Children's 
    Curiosity Museum. The user will play this game at the end of THE BEATLES 
    EXHIBITION. It consist of three stages and the winner will get a ticket to
    a VR party to have an amazing experience as though all The Beatles team 
    members are reuniting in a YELLOW SUBMARINE!
    
    Round 1: Land Of Lyrics
    Round 2: Rock Paper Scissors with Paul McCartney
    Round 3: Guess The Member
    
    B) Known Bugs and/or Errors:
    None.
    
""" 
#importing necessary functions for our code
import random
from random import randint
from sys import exit

#defining the start of the game
#Kids will be asked to complete the lyrics of Yellow Submarine

def welcome():
#creating global variables to use in several functions further in the game

    global kid_name
    global color
    global gender
    
    
    input('<Press any key to start rolling!>\n')
    
    print("""Welcome To The YELLOW SUBMARINE Game!!\n""")
    
    input('<Press any key to begin the Yellow Submarine Game>\n')
    
    print("""
    
    In this game, you'll be challenged to remember all the details you've seen about The Beatles 
    during the exhibition. 
    
    If you have a good memory and a tiny bit of luck, you will win a ticket to a Virtual Reality 
    Party as though all The Beatles members joining you, in a Submarine!\n
            """)
    
    input('<Press Enter to give us some info about yourself>\n')
    
#defining global variables to use in several functions
    kid_name = input(prompt = "Firstly, please fill in your name here: \n")
    
#when I run the game, after entering the user name, a sort of "windows" shows up, I couldn't fix that
    color = input(prompt = "Please fill in your favorite color here: \n")
    gender = input(prompt = "Please fill in your gender here: \n")
    
    print(f"""
    
    Hello {kid_name},your first challenge is to remember the lyrics of the most 
    famous song of The Beatles: YELLOW SUBMARINE! 
    
    We hope you realize it, but Yellow Submarine was the background sound of 
    your tour during the exhibition. Let's see if you paid attention to the lyrics.\n
    """)
    
    input('<Press any key to approach The First Round: LAND OF LYRICS>!\n')
    
#calling first room
    land_of_lyrics() 
    
#creating room 1
def land_of_lyrics():
    
    print("""***LAND OF LYRICS-YELLOW SUBMARINE***""")
    
    print("""
    In the town where I was born...Lived a man who sailed to sea...
    And he told us of his life...In the land of submarines...
    So we sailed up to ____? 
    
        1)The moon 
        2)The sun  
        3)The ocean 
        """)
    
#this is the first set of options for player to choose from
    choice = input(prompt = "Please Fill in: 1, 2, 3.\n")
    
#Choice.lower is defined to handle uppercase inputs
    if "1" in choice or "moon" in choice or "the moon" in choice or choice.lower() == "the moon" or choice.lower() == "moon": 
        print("Oooppsss. That's incorrect")   
        fail()

    elif "2" in choice or "sun" in choice or "the sun" in choice or choice.lower() == "the sun" or choice.lower() == "sun":
        print("That's correct! Please proceed to play Rock, Paper, Scissors with Paul McCartney2!")
        input('<Press any key to continue>\n')
        rock_paper_scissors()
        
    elif "3" in choice or "ocean" in choice or "the ocean" in choice or choice.lower() == "the ocean" or choice.lower() == "ocean": 
        print("Oooppsss. That's incorrect")   
        fail()   
    
    else:
        print(f"Invalid entry {kid_name}. Let me take you out to start over again")
        input('<Press any key to continue>\n')
        land_of_lyrics()
    
#defining room 2 
def rock_paper_scissors():
    
    print(f"""
    Welcome {kid_name}. I'm PAUL McCARTNEY! 
    
    Have you heard my reputation for being lucky among all The Beatles members? 
    In this part of the game, you'll be challenged to be luckier than me!
        """)
    
    input('<Press any key to continue>\n')
    
    print("""Set Yourself for- ROCK, PAPER, SCISSORS with Paul McCartney!!""")
    
    input('<Press any key to approach The Second Round: ROCK, PAPER, SCISSORS>!\n')
    
#create a list of options
    RPS = ["Rock", "Paper", "Scissors"]
    
#assigning random play to computer
    computer = RPS[randint(0,2)]
#    print(f""" Computer chose: {computer}""")                                  # Checking computer choise por debug                              
#set game to true, whenever there's an 
    game = True 
    
#looping while the user attempts to play
    while game == True :
    
        player = input(prompt = """
        Please fill in letters: 
        
        R-for Rock, P-for Paper, S-for Scissors or enter F-Finish to end the game\n
        """)
# Convert player answer into an option in the list RPS                         # Without this, code will compare letter vs words        
        if player == "Rock":
            player = RPS[0]
        elif player == "Paper":
            player = RPS[1]
        elif player == "Scissors":
            player = RPS[2]
        
#        print (f""" After conversion, you chose: {player}""")                 # checking player answer
        
#when player's input and computer's random choice is the same       
        if player == computer:
            print(f"""
            It's a TIE! Paul picked {computer} as well!
            
            You wouldn't expect to beat PAUL that easily!Yet, it's quite enough to see the last round...
            """)
            guess_game()

#when player picks Rock [ and computer randomly selects Paper ] remove last part because you check paper and scissors                       
        elif player =="Rock":
            if computer =="Paper":
                print(f"""Alright{kid_name}! Paul picked {computer}, he covers you...""")
                fail()
                
            else:
                print(f"""
                Good job {kid_name}! Paul picked {computer}, so you beated him! 
                
                Are you ready to see the last round? 
                Only if you complete the last round, you can sail away and have your party with the team!
                """)
                guess_game()
                
#when player picks Paper[, and computer randomly selects Scissors] remove last part because you check rock and scissors  
        elif player =="Paper":
            if computer =="Scissors":
                print(f"""Alright{kid_name}! Paul picked {computer}, he cuts you""")
                fail()
                
            else:
                print(f"""
                Good job {kid_name}! Paul picked {computer}, so you beated him! 
                
                Are you ready to see the last round? 
                Only if you complete the last round, you can sail away and have your party with the team!""")
                guess_game()
                
#when player picks Scissor[, and computer randomly selects Rock]  remove last part because you check paper and rocks                 
        elif player =="Scissors":
            if computer =="Rock":
                print(f"""Alright{kid_name}! Paul picked {computer}, he covers you""")
                fail()
            else: 
                print(f"""
                Good job {kid_name}! Paul picked {computer} so you beated him! 
                
                Are you ready to see the last round? 
                Only if you complete the last round, you can sail away and have your party with the team!""")
                guess_game()
                
        elif player =="Finish":
            fail()
                         
        else:
            print("""That's not even an option!Check your spelling!""")
            


#creating the last room                        
def guess_game():
    
    print(f"""
    
    Well {kid_name}, I see you have a good memory...
    And you are also lucky...!

    Do you know what's the best way to learn? Let's challenge you one last time!
    """)
    
    input('<Press any key to The Last Round: GUESS THE MEMBER!>\n')   
    
#creating the list of questions 
    question_list = ['Which band member grew up near a place called Strawberry Fields in Liverpool?',
                 'Which team member was an accomplished painter',
                 'Which team member has never had pizza, curry or onions?',
                 'Which team member was the first Beatle to release a solo album?']
                 
#creating the list of choices
#member_list is in the correct answer order for the questions
    member_list = ['J','P','R','G']
    
#assigning number of attempts

    attempts = 4
    
#questions will be asked in random order
    question = random.choice(question_list)
    
    print("""
    Please answer only in following letters : 
    Type (J) for John Lennon, (P) for Paul McCartney, (G) for George Harrison, (R) for Ringo Starr\n
    """)
    
    while attempts > 0:
        input(prompt= """Press enter to see the question\n""")
        print(question)
        print("")
        choice = input(prompt= "Please refer your answer as one the following letters J,P,G,R)\n")
        
#I wanted to include "John, Paul, George, Ringo" as possible inputs, 
#but I wasn't sure if I can use "and" & "or" together in one loop, leaving that to be solved later
        choice = choice.lower()
        attempts -= 1
        
#if randomly selected question is the 1st question, and the correct answer to that is the 1st member from member list
        if question == question_list[0] and choice == member_list[0]:
            print(f"""Correct {kid_name}!Almost there\n""")  
#if randomly selected question is the 2nd question, and the correct answer to that is the 2nd member from member list          
        elif question == question_list[1] and choice == member_list[1]:
            print(f"""Correct {kid_name}!Almost there\n""")   
#if randomly selected question is the 3rd question, and the correct answer to that is the 3rd member from member list          
        elif question == question_list[2] and choice == member_list[2]:
            print(f"""Correct {kid_name}!Almost there\n""") 
#if randomly selected question is the 4th question, and the correct answer to that is the 4th member from member list            
        elif question == question_list[3] and choice == member_list[3]:
            print(f"""Correct!! Now, it's time to have {color} Submarine party 
                  with all the Beatles Members!!""")
           
            input('<Press any key to start the SUBMARINE PARTY!!>\n')
#calling the winning function after completing the last round
            submarine_party()
            
        else:
            print("Oooppsss. That's incorrect") 
            fail()
            
#defining fail function
def fail():
    print(f"""
    You have failed {kid_name}!
    Please start again if you do not want to miss the {color} Submarine Party!\n
    """)
#creating restart option    
    restart = input(prompt = '''Do you want to play again?(Yes, No)
    
    ''')
    
    if restart.lower() == "yes":
        land_of_lyrics()
        
    else:
        print(f"""Thanks for playing {kid_name}!\n""")
        
#defining winning function
def submarine_party():
    
    print(f"""
    Ohhh {gender}...! 
    That was a tough, but a good job. Congrats! 
    Let me take you to your own, personally designed {color} Submarine Party!!!\n
    """)
    
    input('<PARTY TIME CHAMPION!WE ALL LIVE IN A YELLOW SUBMARINE>\n')
    

welcome()
