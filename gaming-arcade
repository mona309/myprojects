import pickle,mysql.connector,random,string

def mainmenu():
    while True:
        print()
        print('   -----------------------')
        print('   --------MAIN MENU------')
        print('   -----------------------')
        print("  | 1. Play               |")
        print("  | 2. Wheel of luck      |")
        print("  | 3. Leaderboard        |")
        print("  | 4. Socials            |")
        print("  | 5. Settings           |")
        print("  | 6. Log Out            |")
        print('   -----------------------')
        print()
        r=int(input("Enter response: "))
        
        if r in range(1,7):
            if r==1:#games                                                                  
                option1()
                continue
            elif r==2:
                option2()
                continue
            elif r==3:
                option3()
                continue
            elif r==4:
                option4()
                continue
            elif r==5:
                option5()
                continue
            elif r==6:
                print('Goodbye!\nYou have achieved a total of ',{d[u][2]},' coins over the course of your time with us !\nHope to see you ')
                print("\nYou are being logged out....\nLogged out")
                break
        else:
            print('Wrong input try again!!\n\n')
            continue


        
def option1():
    while True:
        print('_'*30)
        print('\nTO GO BACK TO MAIN MENU INPUT 0\n')
        print('\nEasy: ')
        print("1. Tic Tac Toe")
        print("2. Rock, Paper, Scissor")
        print("3. Adventure Story")
        print('\nMedium: ')
        print("4. Hack It")
        print("5. Hangman")
        print("6. Book Quotes Trivia")
        print('\nHard: ',end=' ')
        if d[u][2]<150:
            print('Hard levels currently locked')
        else:
            print('')
        print("7. Guess the Word ")
        print("8. Coding encoding")
        print("9. Guess the Number\n")
        print('_'*30,'\n')
        chc=int(input('Enter you choice(number): '))
        print('\n')
        if chc==1:                                                    
            game1()
            continue
        elif chc==2:
            game2()
            continue
        elif chc==3:
            game3()
            continue
        elif chc==4:
            game4()
            continue
        elif chc==5:
            game5()
            continue
        elif chc==6:
            game6()
            continue
        elif chc in (7,8,9):
            if d[u][2]>=150:
                if chc==7:#word
                    game7()
                    continue
                elif chc==8:#coding encoding
                    game8()
                    continue
                elif chc==9:#Guess number
                    game9()
                    continue                     
            else:
                print('Hard levels unlock after minimum 150 coins')                                      
        elif chc==0:
            print('Total coins earned till now: ',d[u][2])
            cursor.execute('update global set points=%s where username=%s',(d[u][2],u))
            cursor.execute('update country set points=%s where username=%s',(d[u][2],u))
            cursor.execute('update friends set points=%s where username=%s',(d[u][2],u))
            break



def option2():
    if d[u][3]<3:
        print('\nWELCOME TO THE WHEEL OF LUCK!')
        print('\nHow to play?')
        print("1. A dice generates a number(1-6) and rotates the numbers of the wheel that many times")
        print("2. Whatever you get as the first number after the spin is your reward")
        print("3. You can only spin the wheel max 3 times on one account")
        wheellist=[30,10,0,50,40,20]
        print('\nCurrent wheel: ',wheellist)
        print()
        while d[u][3]<3:
            print('Spins remaining:',(3-(d[u][3])))
            n=input("Do you want to roll the dice? - yes or no : ")
            print()
            if n=='yes':
                d[u][3]+=1
                drn=random.randint(1,6)
                for j in range(drn):
                    x=wheellist.pop(len(wheellist)-1)
                    wheellist.insert(0,x)
                print('Wheel after spin: ',wheellist)
                print("Number obtained on dice:",drn)
                bonus=wheellist[0]
                d[u][2]+=bonus
                if bonus==0:
                    print("Sorry you didn't win any coins. Better luck next time!")
                    print()
                else:
                    cursor.execute('update global set points=%s where username=%s',(d[u][2],u))
                    cursor.execute('update country set points=%s where username=%s',(d[u][2],u))
                    cursor.execute('update friends set points=%s where username=%s',(d[u][2],u))
                    print("Congrats you won",bonus,"coins")
                    print()
                    continue
                
            elif n=='no':
                print('\nGoing back to main menu...')
                break
        else:
            print()
            print("All spins exhausted.\nGoing back to main menu...")
    else:
        print("All spins exhausted.\nGoing back to main menu...")



def option3():
    while True:
        print()
        print('   ------------------------')
        print('   ------LEADERBOARDS------')
        print('   ------------------------')
        print("  | 1. Global Leaderboard  |")
        print("  | 2. Country Leaderboard |")
        print("  | 3. Friends Leaderboard |")
        print("  | 4. Back                |")
        print('   ------------------------')
        print()
        cc=int(input('Enter your choice: '))
        

        if cc==1:
            cursor.execute('select Username,Points,CountryCode, rank() over(order by points desc) as Ranking from global')
            print('\t\tGLOBAL LEADERBOARD\n')
            print('username\t','points\t\t','country\t','rank')
            for row in cursor:
                for rr in row:
                    print(rr,end='\t\t')
                print()


        elif cc==2:
            cursor.execute('select Username,Points,CountryCode, rank() over(order by points desc) as Ranking from country')
            print('\t\tCOUNTRY LEADERBOARD\n')
            print('username\t','points\t\t','country\t','rank')
            for row in cursor:
                for rr in row:
                    print(rr,end='\t\t')
                print()

                
        elif cc==3:
            cursor.execute('select Username,Points,CountryCode, rank() over(order by points desc) as Ranking from friends')
            print('\t\tFRIEND LEADERBOARD\n')
            print('username\t','points\t\t','country\t','rank')
            for row in cursor:
                for rr in row:
                    print(rr,end='\t\t')
                print()

        elif cc==4:
            break
            
        else:
            print('Wrong innput try again!')
            continue
    


def option4():
    while True:
        print()
        print('   ------------------------------')
        print('   ------------SOCIALS-----------')
        print('   ------------------------------')
        print("  | 1. Search/Add Friend         |")
        print("  | 2. Remove Friend             |")
        print("  | 3. Friend List               |")
        print("  | 4. Check Inbox               |")
        print("  | 5. Send Mail                 |")
        print("  | 6. Back                      |")
        print('   ------------------------------')
        print()
        c=0
        scc=int(input('Enter choice: '))
        
        if scc==1:
            while True:
                srch=input('Enter username for search: ')
                xyz=srch.strip().lower()
                if xyz in d:
                    print('\nUsername: ',xyz,'\tPoints: ',d[xyz][1],'\tCountryCode: ',d[xyz][2])
                    print()
                frd=input('Add friends? (yes/no)')
                if frd.strip().lower()=='yes':
                    d[u][4].append(xyz)
                    d[xyz][4].append(u)
                    break
                elif frd.strip().lower()=='no':
                    print('Friend not added')
                    break
                else:
                    print('Invalid input!')
                    continue
            else:
                print('Username doesn\t exist in our database! Try again.')
                continue
        
        elif scc==2:
            while True:
                srch=input('Enter username for search: ')
                xyz=srch.strip().lower()
                if xyz in d:
                    print('\nUsername: ',xyz,'\tPoints: ',d[xyz][1],'\tCountryCode: ',d[xyz][2])
                    print()
                frd=input('Remove friend? (yes/no)')
                if frd.strip().lower()=='yes':
                    d[u][4].remove(xyz)
                    d[xyz][4].remove(u)
                    break
                elif frd.strip().lower()=='no':
                    print('Friend not removed')
                    break
                else:
                    print('Invalid input!')
                    continue
            else:
                print('Username doesn\t exist in our database! Try again.')
                continue

        elif scc==3:
                print('\nCurrent Friend list: ')
                for i in d[u][4]:
                    for j in d:
                        if i==j:
                            c+=1
                            print(c,j,d[j][2],sep='\t')

                        
        elif scc==4:
            print('           INBOX           \n')
            file=open('ArcadeCloud.pkl','rb')
            for i in (pickle.load(file)):
                print(i[0].lower(),u)
                if i[0].lower()==u:
                    print('ok')
                    for j in i[1]:
                        print('ok1')
                        print(j[0],':')
                        print("'",j[1],"'",sep='')
                        print()
            file.close()


        elif scc==5:
                while True:
                    global lst
                    c=input('Do you wish to send message? yes or no: ')
                    
                    if c.lower()=='yes':
                            nm=input('Enter name of recipient: ')
                            msg=input('Enter message to be sent: ')
                            sl=[u,msg]
                            if nm in d[u][4]:
                                file1=open('ArcadeCloud.pkl','rb')
                                global inbx
                                inbx=pickle.load(file1)
                                for i in inbx:
                                    if i[0].lower()==nm:
                                        i[1].insert(0,sl)
                                        print('Message sent!')
                                        break
                                file1.close()

                            else:
                                print('User not in friends list. Message not sent')
                                opt=input('Do you wish to try again? yes or no: ')
                                if opt.lower()=='yes':
                                    continue
                                elif opt.lower()=='no':
                                    print('Exiting out of menu...')
                                    break
                    elif c.lower()=='no':
                            print('Exiting out of menu...')
                            file=open('ArcadeCloud.pkl','wb')
                            pickle.dump(lst,file)
                            file.close()
                            break
                        
                        
        elif scc==6:
                break
        elif scc==7:
            print(inbx)
                    
        else:
                print('Wrong input')
                continue
                

def option5():
    while True:
        print()
        print("SETTINGS")
        print("1. Change username")
        print("2. Change password")
        print("3. Change Country")
        print("4. Back")
        print()
        st=int(input("Enter response: "))
        
        if st==1:
            nu=input("Enter new username: ")
            global u
            old=u
            d[nu]=d.pop(u)
            u=nu
            d[u]=d.pop(nu)
            print('Username updated to ',u)
            cursor.execute('update global set username=%s where username=%s',(u,old))
            continue


        elif st==2:
            np=input("Enter new password: ")
            d[u][0]=np
            print("Password updated to",np)
            continue


        elif st==3:
            print('Current Country Code is:', d[u][1])
            oldc=d[u][1]
            ncc=input('Enter Country Code: ')
            d[u][1]=ncc  
            print('Country Code updated to ',ncc)
            cursor.execute('update global set countrycode=%s where countrycode=%s and username=%s',(ncc,oldc,u))
            continue  


        elif st==4:
            break


def game1():
        print("Welcome to Tic Tac Toe")
        print()
        print("How to play?")
        print()
        print("1. You are 'X' and the computer is 'O'")
        print("2. You need to complete a row colum or diagonal before the computer")
        print("3. You get 50 coins if you win, 20 coins for a tie and 0 coins if you lose")
        dr={1:[[1,1],[1,2],[1,3]],
            2:[[2,1],[2,2],[2,3]],
            3:[[3,1],[3,2],[3,3]]}
        done=[]
        g1=0
        print()
        
        for i in dr:
                for j in dr[i]:
                        print('*',end='  ')
                print()
                
        print('\nCoordinates are as follows [row number, column number]')
        
        for i in dr:
                for j in dr[i]:
                        print(j,end='  ')
                print()
        print()
        
        while ((len(done))<10):
            
            while True:
                r=int(input('Enter row number(1/2/3): '))
                c=int(input('Enter column number(1/2/3): '))
                cd=[r,c]
                
                if cd in done:
                    print('That place is already taken! Try again')
                    continue
                
                else:
                    break

            for a in dr:
                for b in range(3):
                    if dr[a][b]==cd:
                        dr[a][b]='X'
                        done.append(cd)
            print()
            
            for i in dr:
                for j in dr[i]:
                    if j=='X'or j=='O':
                        print(j,end='  ')
                    else:
                        print('*',end='  ')
                print()
            print()
            
            if (dr[1][0]==dr[2][0]==dr[3][0]=='X' or dr[1][1]==dr[2][1]==dr[3][1]=='X' or dr[1][2]==dr[2][2]==dr[3][2]=='X' or dr[1][0]==dr[1][1]==dr[1][2]=='X' or dr[2][0]==dr[2][1]==dr[2][2]=='X' or dr[3][0]==dr[3][1]==dr[3][2]=='X' or dr[1][0]==dr[2][1]==dr[3][2]=='X' or dr[1][2]==dr[2][1]==dr[3][0]):
                print("YOU WIN! : 50 COINS ")
                d[u][2]+=50
                break
            
            else:
                if len(done)==9:
                    print("TIE! : 20 COINS")
                    print("GAME OVER!")
                    d[u][2]+=20
                    break
                
            while True:
                cr=random.randint(1,3)
                cc=random.randint(1,3)
                ccd=[cr,cc]
                if ccd not in done:
                    break
            done.append(ccd)
            
            for c in dr:
                for e in range(3):
                    if dr[c][e]==ccd:
                        dr[c][e]='O'
            print('\nOpponent entered:',ccd,'\n')
            print()
            
            for i in dr:
                for j in dr[i]:
                    if j=='X'or j=='O':
                        print(j,end='  ')
                    else:
                        print('*',end='  ')
                print()
            print()
            
            if (dr[1][0]==dr[2][0]==dr[3][0]=='O' or dr[1][1]==dr[2][1]==dr[3][1]=='O' or dr[1][2]==dr[2][2]==dr[3][2]=='O' or dr[1][0]==dr[1][1]==dr[1][2]=='O' or dr[2][0]==dr[2][1]==dr[2][2]=='O' or dr[3][0]==dr[3][1]==dr[3][2]=='O' or dr[1][0]==dr[2][1]==dr[3][2]=='O' or dr[1][2]==dr[2][1]==dr[3][0]):
                print("YOU LOSE! : 0 COINS")
                print("GAME OVER!")
                break
def game2():
    print("Welcome to Rock Paper & Scissors")
    print()
    print("""Rules :\n\t\tRock smashes scissors\n\t\tPaper covers Rock\n\t\tScissors cuts Paper""")
    tr=1
    g2=0
    while tr<=3:
        print('\n\n')
        useraction = input("Enter a choice (rock, paper, scissors): ")
        possible_actions = ["rock", "paper", "scissors"]
        computer_action = random.choice(possible_actions)
        print(f"\nYou chose {useraction}, computer chose {computer_action}.\n")
        if useraction.lower()==computer_action:
            print(f"Both players selected {useraction.title()}. It's a tie!")
            print(f"Current Total: {g2}")
            tr+=1
        elif (useraction.lower()=="rock" and computer_action == "scissors") or(useraction.lower()=="paper"and computer_action == "rock") or(useraction.lower()=="scissor"and computer_action == "paper"):
            print(f"{useraction.title()} wins over {computer_action.title()}\nYou WIN! +10 PCOINS.")
            g2+=10
            print(f"Current Total: {g2}")
            tr+=1
        elif (useraction.lower()=="scissors" and computer_action == "rock") or(useraction.lower()=="rock"and computer_action == "paper") or(useraction.lower()=="paper"and computer_action == "scissors"):
            print(f"{computer_action.title()} wins over {useraction.title()}\nYou LOSE! -10 COINS.")
            g2-=10
            print(f"Current Total: {g2}")
            tr+=1
        else:
            print('Invalid input')
    print("\nYour total score is ",g2,'\n\nGAME OVER')
    d[u][2]+=g2


def game3():
    print("\t\t\tWelcome To The Adventure Game\n")
    print("\t\t\t SURVIVAL OF THE FITTEST !")
    print()
    print("Rules:\n1. You will be given hints and choices on how you want the story to go about.\n2. If you manage to save your character from the villian you get 50 Points.\nAll The Best!\n\n")
    name=input("Enter a name for your main character: ")
    obj=input("Enter a magical object wich helps you in the story: ")
    place=input("Enter the place where the drama of your story will take place: ")
    villian=input("Enter the villian to be used in your story (eg monster,ghost): ")
    print()
    answer_yes='stay'
    answer_no='evaluate'
    print(name,"woke up in their bedroom in the middle of the night.There was a loud BANG outside the house.\nNow your character has two choices either to stay in the room or check what the sound might be about.\n")
    c1=input('Type your choice(STAY or EVALUATE?): ')
    c1=c1.lower()
    ans = 'incorrect'
    while(ans=='incorrect'):
        if c1=='stay':
            print()
            print(name,"decides to stay in the room and ends up staying inside forever as no one seems to come to help them.")
            print("Then a mysterious force drags her into the" ,place,".")
            ans = 'correct'
        elif c1=='evaluate':
            print("\n",name,"exits the room silently and reaches the",place,"." )
            ans='correct'

        else:
            print("\nENTER THE CORRECT CHOICE TO SAVE",name,'!',end=' ')
            c1 = input("STAY OR EVALUATE?: ")

    print("In the ",place,name, " finds a strange but a cute",obj,"on the ground.",name," wanted to pick the",obj,".But is it right? It doesn't belong to them.\n")
    c2=input("Type your choice(PICK or IGNORE?): ")
    c2=c2.lower()
    ans = 'incorrect'
    while(ans=='incorrect'):
        if c2=='pick':
                print("\nThe moment",name," picked up the",obj," it starts TALKING.")
                print("It tells",name," that",name," is in grave danger as there is the",villian, "in the house.")
                print("And the",villian," has captured their PARENTS as well!But it hugged ",name,"and told",name," not to get scared as it knows how to beat the",villian,".")  
                print("The",obj,"handed",name,"a magic potion which can weaken the",villian," and make him run away!",obj," handed the potion and then DISAPPEARED!",name,"moved forward.")
                ans = 'correct'
                pick="True"
        elif c2=='ignore':
                print()
                print(name,"decided not to pick up the",obj," and walked forward.")
                ans='correct'
                pick="False"
        else:
                print()
                c2=input("Wrong Input! PICK OR IGNORE?: ")

    print("After walking for a while",name," saw the ",villian," in front of",name,"!It had red eyes and evil looks.",name," got very scared!")

    if(pick=="True"):
        print("But then",name,"remembered!",name,"had the magic portion and",name," threw it on the" ,villian,"! Well" ,name," had nothing to lose!")
        print("The",villian," SCREAMED in pain and vanished in front of",name,"eyes.\n")
        print("You managed to save your character !\nCONGRATULATIONS. You get 50 coins :)")
        d[u][2]+=50
    elif(pick=="False"):
        print("The",villian," attacked" ,name," and hurt her!" ,name," was then thrown into another dimension by the ",villian,".\n")
        print("""You could not save your character ! You lost! 0 coins :(""")
    print("""\nGAME OVER""")


def game4():
    g8=0
    print ("Welcome to HACK IT !")
    print()
    print("""You are a professional Whit Hat Hacker from your secret organisation and you need to hack into another organisation's computer to find out important
information.You are in the final stage and just have 2 more steps to pass. You need to guess the email id and a new password will be generated as per your specifications of length, alphanumeric and special character count.
Don't worry you will be given hints.
All the Best!""")
    print()
    print("""You need to guess the username in the email id.
HINT 1: Sir loves his fat pet dog!
HINT 2: The main logo of Halloween is a fruit!(that is the pets name :))""")
    print()
    username1=['Pumpkin','pumpkin','PUMPKIN']
    domainname1=['Elizabeth','elizabeth','ELIZABETH']
    email1=['PUMPKIN@ELIZABETH.com','Pumpkin@Elizabeth.com','pumpkin@elizabeth.com']
    username=input("Enter the username: ")
    print()
    print("""You need to guess the domain name in the email id.
HINT 1: Sir loves his sister.
HINT 2: Her name is the same as that of the late Queen of England. (just the first name will do :))""")
    print()
    domainname=input("Enter the Domain name: ")
    n=0
    while(n==0):
        if(username in username1) and(domainname in domainname1):
            print("\nYou guessed it correctly!")
            print("You get 20 coins :)")
            g8+=20
            print()
            print("""You need to enter the email id to login to the account.
(format for email: username@domainname.com)""")
            print()
            email=input("Enter the email id: ")
            if (email in email1):
                    print("\nYou have guessed the email correctly!")
                    print("You get 10 coins more !")
                    g8+=10
                    print("\nYour total score is 30! \n")
                    pick="True"
            else:
                    print("\nYOU GUESSED IT WRONG!")
                    print("Total coins earned is 20!\n")
                    pick="False"

        else:
            print("\nYOU GUESSED WRONG ! FAILURE :(")
            print("You get 0 coins\n")
            pick="False"
        n+=1
            
    if (pick=="True"):
        print("""You have finished collecting and deleting some important information.Generate a new password so that the opponent takes time to log back in """)
        print('\n\n\nCreating New Password...\n')

        alphabets = list(string.ascii_letters)
        digits = list(string.digits)
        special_characters = list("!@#$%^&*()")
        characters =list(string.ascii_letters + string.digits + "!@#$%^&*()")
        length = int(input("Enter password length: "))
        print()
        alphabets_count = int(input("Enter alphabets count in password: "))
        print()
        digits_count = int(input("Enter digits count in password: "))
        print()
        print('Special characters include: ',special_characters)
        special_characters_count = int(input("Enter special characters count in password: "))
        print()
        characters_count = alphabets_count + digits_count + special_characters_count
        if characters_count > length:
            print("\nCharacters total count is greater than the password length. Not valid !\n")
            print("Total coins earned is 30\n")

        else:
            password = []
            for i in range(alphabets_count):
                password.append(random.choice(alphabets))
            for i in range(digits_count):
                password.append(random.choice(digits)) 
            for i in range(special_characters_count):
                password.append(random.choice(special_characters))
            if characters_count < length:
                random.shuffle(characters)
                for i in range(length - characters_count):
                    password.append(random.choice(characters))
            random.shuffle(password)
            print('New password: ',end='')
            print("".join(password))
            print("\nYou have successfully created a new password!")
            print("Total coins earned is 50 . Congratulations! \n")
            g8+=20

    print("GAME OVER")
    d[u][2]+=g8


def game5():
    print('Welcome to Hangman\n')
    print("How to play?")
    print("1. An English movie name is displayed and you have 6 chances to guess the name and no. of lives will be displayed alonside revealed letters as 'X's")
    print("2. Initial score is 60 with each wrong guess you take your score down by 10")
    print('3. After you guess all the letters enter the whole movie name to end the game')
    print('4. Valid inputs- Individual letters/ full name of the movie')
    print()
    l=['ENOLA HOLMES','RAYA AND THE LAST DRAGON','INTERSTELLAR','INCEPTION','SNOWPIERCER','SHANG CHI AND THE LEGEND OF THE TEN RINGS','A QUIET PLACE','RED NOTICE']
    x=random.randint(0,7)
    rl=[]
    for i in l[x]:
        if i!=' ':
            print('*',end='')
        else:
            print(' ',end='')
    print()
    count=0;g5=60;wrong=6
    while wrong>0:
        n=input("Enter a letter (or the entire movie name if you have guessed it): ")
        n=n.upper()
        rl+=n
        y=list(l[x])
        
        if n==l[x]:
            print("Congrats you have guessed the movie!")
            print("Coins: ",g5,'\n\nGAME OVER')
            break
        
        else:
            if n=='':
                g5=0
                break
            else:
                z=''
                if rl.count(n)>1:
                    print("Letter already inputed")
                else:
                    if n in y:
                        for i in range(len(y)):
                            if (y[i]!=n) and (y[i]!=' ') and (y[i] not in rl):
                                y[i]='*'
                            z+=y[i]
                        print(z,'\t','\t',('X '*wrong))
                    else:
                        wrong-=1
                        g5-=10
                        print("Wrong letter: ",('X '*wrong))
                        
    if g5==0:
        print("You have lost")
        print("You get 0 coins\n\nGAME OVER")            
    d[u][2]+=g5



def game6():
    g6=0
    print('Welcome to Book Quotes Trivia\n')
    que={1:['“All that is gold does not glitter, Not all those who wander are lost.”',
            'The Fellowship of the Ring',
            'The Hitchhiker\'s Guide to the Galaxy',
            'The Lion,the Witch and the Wardrobe',1],
        2:['“It was the best of times, it was the worst of times.”',
            'War And Peace',
            'The House Of Mirth',
            'A Tale Of Two Cities',3],
        3:['“It is a truth universally acknowledged, that a single man in possession of a good fortune, must be in want of a wife.”',
            'Pride And Prejudice',
            'Sense And Sensibility',
            'Great Expectations',1],
        4:['“I like large parties. They’re so intimate. At small parties there isn’t any privacy.”',
            'Tender Is The Night',
            'The Great Gatsby',
            'The Catcher In The Rye',2],
        5:['“Never doubt I love.”',
            'Romeo And Juliet',
            'Jane Eyre',
            'Hamlet',3]}
    dn=[]
    for a in que:
        print(f'Question {a} :\n')
        print(f'  {que[a][0]}')
        for nm in range(1,4):
            print(f'   {nm}  {que[a][nm]}')
        while True:
            xyz=int(input('\nEnter choice number: '))
            if xyz not in range(1,4):
                print('Valid inputs- 1/2/3')
                continue
            else:
                break

        if xyz==que[a][4]:
            print('Correct! +10 COINS\n\n')
            g6+=10
        else:
            cra=que[a][4]
            print(f'Wrong! +0 COINS\nCorrect answer was \"{que[a][cra]}\"\n\n')
    print('Total points: ',g6,' POINTS\n\nGAME OVER')
    d[u][2]+=g6



def game7():
    print('Welcome to Guess the Word\n')
    print('How to play?\n(1) Phrases describing a particular word is given\n(2) Guess that word\n(3) Three attempts for each word')
    db={1:['Good or Bad Sign','omen'],
        2:['tool with teeth','saw'],
        3:['Sci-Fi francise with "light cicles"','tron'],
        4:['Contellation named after a hunter from Greek Mythology','orion'],
        5:['Complete disorder and confusion','chaos'],
        6:['Of a vivid red to reddish-orange color ','vermillion'],
        7:['Surpassing the ordinary or normal','uncanny'],
        8:['Any maze or place with "intricate passageways”','labyrinth'],
        9:['Handrail in a ballet studio','barre']
        }
    questions=[]
    x=1
    g7=0
    while x<=3:
        chc=random.randint(1,9)
        if chc in questions:
            continue
        else:
            y=1
            questions.append(chc)
            print()
            print(f'Q{x} :\n{db[chc][0]}\nNumber of letters - {len(db[chc][1])}')
            while y<=3:
                print()
                aaa=input('Enter your answer: ')
                if aaa.lower()==db[chc][1]:
                    print('Correct!',end=' ')
                    if y==3:
                        print('+10POINTS\n\n\n')
                        g7+=10
                    elif y==2:
                        print('+20 COINS\n\n\n')
                        g7+=20
                    else:
                        print('+30 COINS\n\n\n')
                        g7+=30
                    break
                else:
                    print(f'Wrong! {3-y} attempts remaining\n')
                    if 3-y==0:
                        print(f'Attempt run out +0POINTS\nThe correct answer was {db[chc][1]}\n\n')
                    y+=1
                    continue
            x+=1
    print(f'Total coins: {g7}\n\nGAME OVER')
    d[u][2]+=g7




def game8():
    print('Welcome to Coding Encoding\n')
    print('How to play?\n(1)Decoded words are given and are encoded using common cypher like barconion cypher, binary code, morse code,etc\n(2)Only one chance at trying so use hint if needed\n(3)10POINTS for right answer and 0 for wrong')
    xyz= 'shty7i5c0fe4grjklxnr2d1ubmbdopq8'
    l=[]
    g4=0
    p=(8,16,24,32)
    for i in xyz:
        l.append(i)
    dx={'Code1':['  ...    -.-.    ..    - -     ..    -    .-    .-.','scimitar','Morse Code'],
        'Code2':['01000001    01000011    01000001    01000100    01000101    01001101    01011001','academy','Binary code,01000001= A'],
        'Code3':['baaab  baaba  baaaa abaaa abaab  aabaa',
                    'strike','a=aaaaa b=aaaab c=aaaba d=aaabb'],
        'Code4':['fodibounfou','enchantment','If b=a and c=b'],
        'Code5':['pass','hero','find the only meaningful 4 letter word']}
    for i in dx:
        if i=='Code5':
            print(i,'\n')
            for j in l:
                if j==l[7] or j==l[15] or j==l[23] or j==l[31]:
                    print(j,'\n')
                else:
                    print(j,'\t',end='')
        else:
            print()
            print(i," : \n",dx[i][0],'\n')
        y=input('Would you like a hint?(yes/no)')
        if y.lower()=='yes'or y.lower()=='y':
                print('HINT: ',dx[i][2],'\n')
        ans=input('Enter your answer: ')
        if ans.lower()==dx[i][1]:
            print()
            print('Correct answer! +10 COINS\n\n')
            g4+=10
        else:
            print()
            print(f'Wrong answer! +0 COINS \nCorrect answer was {dx[i][1]}\n\n')
    print(f'Total points for Game 4: {g4}\n\nGAME OVER')
    d[u][2]+=g4


def game9():
    g9=0
    nl=[]
    print('Welcome to Guess the Number\n')
    print("How to play?")
    print()
    print("1.Player inputs number of digits and a random number with those many digits is generated. The digits DO NOT repeat.")
    print("2.Player has to keep entering guesses(what they think the number might be) while the computer confirms whether the entered digits match the generated number or not until they input the rigt number")
    print("3.No. of chances is 3 times the number of digits the number and initial score is 10 times the number of chances(ex: 2 digit no.:6 chances:60 points, 3 digit no.:9 chances:90 points) but with each guess you take your score down by 10.")
    print("4.To exit at any point press 'e' when guess is asked but the game will be considered lost and score will be 0 for exiting midway")
    print()
    import random
    x=int(input("Enter number of digits you want the number to be(between 1 to 10): "))
    while x<1 or x>10:
        print("Sorry input a number between 1 to 10")
        x=int(input("Enter number of digits you want the number to be(between 1 to 10): "))
    while True:
        n=str(random.randint(10**(x-1),(10**x)-1))
        for i in n:
                if n.count(i)!=1:
                    break
        else:
            break
    count=0;g9=(x*30)
    print("Initial score: ",g9)
    print("No. of chances: ",x*3)
    print()
    for i in range(x*3):
        while True:
            gn=input("Enter your guess: ")
            if gn not in nl:
                break
            else:
                print("Number already inputed.Please re-enter")
        nl.append(gn)
        count+=1
        if gn==n:
            print("Congrats you guessed the number!")
            print("No. of turns taken: ",count)
            print("Coins: ",g9,'\n\nGAME OVER')
            break
        else:
            if gn=='e':
                    score=0
                    break
            else:
                for i in range (len(n)):
                    if gn[i] in n:
                        if gn[i]==n[i]:
                            print(gn[i],": Correct digit, Correct place")
                        else:
                            print(gn[i],": Correct digit, Wrong place")
                    else:
                        print(gn[i],": Wrong digit")
                print("Chances left: ",(x*3)-count)
                print()
                g9-=10
    if g9==0:
        print("The number was",n)
        print("You lost")
        print("You get 0 coins\n\nGAME OVER")
    d[u][2]+=g9

#################################################################################################################################

d={'bot':['000','IN',150,0,['bot1','bot2','bot3','bot4','bot5']],
'bot1':['111','IN',99,0,['bot']],
'bot2':['222','UK',160,0,['bot']],
'bot3':['333','US',999,0,['bot']],
'bot4':['444','UK',100,0,['bot']],
'bot5':['555','IN',500,0,['bot']]}
lst=[['Bot',[['Bot1','Hi!!!!!'],['Bot2','How are you?']]],
        ['Bot1',[['Bot','Heloow!']]],
        ['Bot2',[]],
        ['Bot3',[]],
        ['Bot4',[]],
        ['Bot5',[]]]


mydb = mysql.connector.connect(host="localhost", user="root", passwd="sql123")
cursor = mydb.cursor()
cursor.execute('drop database if exists arcadecloud')
cursor.execute('create database arcadecloud')
cursor.execute('use arcadecloud;')
cursor.execute('create table Global(Username varchar(20),Points int(10),CountryCode varchar(5))')
cursor.execute('insert into global values(\'Bot\',\'150\',\'IN\');')
cursor.execute('insert into global values(\'Bot1\',\'99\',\'IN\');')
cursor.execute('insert into global values(\'Bot2\',\'160\',\'UK\');')
cursor.execute('insert into global values(\'Bot3\',\'999\',\'US\');')
cursor.execute('insert into global values(\'Bot4\',\'100\',\'UK\');')
cursor.execute('insert into global values(\'Bot5\',\'500\',\'IN\');')
mydb.commit()
while True:
    print('\n<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>\n')
    print("Welcome to Arcade Cloud!")
    n=input("Do you wish to login - yes or no: ")
    if n=='yes':
        u=input("Enter username: ")
        if u in d:                                                                             #username exist
            p=input("Enter password: ")
            while (d[u])[0]!=p:                                                                #password check
                p=input("Wrong password. Please re-enter: ")
            print("Login Successful!!")
            cursor.execute('drop table if exists country')
            cursor.execute('drop table if exists friends')
            cursor.execute('create table country as select * from global where CountryCode =%s',(d[u][1],))
            cursor.execute('create table friends(Username varchar(20),Points int(10),CountryCode varchar(3))')
            for i in d[u][4]:
                sql='insert into friends values(%s,%s,%s)'
                rows=[i,d[i][2],d[i][1]]
                cursor.execute(sql,rows)
            file=open('ArcadeCloud.pkl','wb')
            pickle.dump(lst,file)
            file.close()
            cursor.execute('insert into friends values(%s,%s,%s)',(u,d[u][2],d[u][2]))
            mainmenu()
        else:                                                                                     #username does not exist
            print()
            print("Username does not exist. Do you wish to join? Enter 'yes' or 'no'")
            r=input("Enter response: ")
            print()
            if r=='yes':
                u=input("Create username: ")
                if u in d:
                    print("\nUsername exists. Please choose another")
                else:
                    p=input("Create password: ")
                    uc=input('Country: ')
                    print("\nAccount created!")
                    d[u]=[p,uc,0,0,[]]
                    cursor.execute('insert into Global values(%s,%s,%s)',(u,0,uc))
                    mydb.commit()
                    lst.append([u,[]])
                    print()
                    continue
            elif r=='no':
                print("Exiting...\nYou Have Exited")
                continue
            
    elif n=='no':                                                                                     #dont want to play
        print()
        print("Exiting...\nYou Have Exited")
        break
            

