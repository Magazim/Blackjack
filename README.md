import random
import time

money = 100

while money > 0:
    
    print("regler:")
    print("du kan bare bete fra 10-100(og hels ti-tall)")
    print("du kan ikke bete mer enn du har og ikke mer enn 100")
    print("")
    
    print("Du har", money, "kr")
    time.sleep(1)

    bet_T = int(input("Hvor mye ^beter^ du? "))

    if bet_T > money:
        bet_T = 10

    money -= bet_T
    print("du beter:", bet_T)
    print("")
    time.sleep(1)

    # p1 sinne kort
    P1_card1 = random.randint(1, 11)
    P1_card2 = random.randint(1, 11)

    print("ditt første kort er:", P1_card1)
    time.sleep(1)
    print("ditt andre kort er:", P1_card2)
    time.sleep(1)

    P1_total = P1_card1 + P1_card2
    print("din total er:", P1_total)
    print("")
    time.sleep(1)

    # bot sinne kort
    bot_card1 = random.randint(1, 11)
    bot_card2 = random.randint(1, 11)

    print("bot sitt første kort er:", bot_card1)
    time.sleep(1)
    print("bot sitt andre kort er: ?")
    print("")
    time.sleep(1)

    # nytt kort eller stay
    if P1_total < 21:
        
        print("1 = ta kort")
        print("2 = stay")
        
        valg = int(input("hva tar du? "))
        
        if valg==1:
            
            while valg==1:
            
             print("du trekker et kort til")
             time.sleep(1.5)
             P1_new_card = random.randint(1, 11)
             P1_total += P1_new_card
             print("du fikk kortet:", P1_new_card)
             print("din total er:", P1_total)
             time.sleep(1)
             
             if P1_total==21:
                 print("du fikk blackjack")
                 valg=2
                 
             elif P1_total>21:
            
                print("du har mer en 21")
                valg=2
            
             else:
                print("hva gjør du nå?")
                print("")
                print("1 = ta kort")
                print("2 = stay")
                valg = int(input("hva tar du? "))
                
            valg==2
            print("du:stay")
            print("")
            
        else:
              
            print("du:stay")
            print("")
                

                

    if P1_total > 21:
        print("Du har mer enn 21, du tapte")
        time.sleep(2)
        continue

    
    time.sleep(1)

    # bot sin tur
    bot_total = bot_card1 + bot_card2
    print("bot sitt skjulte kort var:", bot_card2)
    time.sleep(1)
    print("bot sin total:", bot_total)
    time.sleep(1)

    while bot_total < 16:
        print("bot trekker et kort til")
        time.sleep(1.5)
        new_card = random.randint(1, 11)
        bot_total += new_card
        print("bot fikk kortet:", new_card)
        print("bot sin total er:", bot_total)
        time.sleep(1)

    if bot_total<21:
        print("bot: stay")
        time.sleep(1)
    elif bot_total==21:
        print("bot: Blackjack")
        time.sleep(1)
    else:
        print("bot: for mye  :(")
        time.sleep(1)
        
    # hvem som vinner
    if bot_total > 21:
        print("Bot fikk over 21, du vant")
        money += bet_T * 2

    elif bot_total > P1_total:
        print("bot vant")

    elif bot_total < P1_total:
        print("du vant")
        money += bet_T * 2

    else:
        print("uavgjort")
        money += bet_T

    time.sleep(2)
    print("ny runde")
    print("")

print("Du er tom for penger, game over")
