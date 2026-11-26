def gra():
    ekwipunek = {"miecz": 1, "mikstura": 3, "zloto": 50}
    ceny = {
        "miecz": 20,
        "mikstura": 10,
        "tarcza": 30,
        "luk": 25
    }
    while True:
        print("\nMenu:")
        print("1. Pokaz przedmioty")
        print("2. Kup przedmiot")
        print("3. Uzyj przedmiotu")
        print("4. Sprawdz przedmiot")
        print("5. Wyjdz")
        wybor = input("Wybierz opcje: ")
        if wybor == "1":
            for nazwa, ilosc in ekwipunek.items():
                print(f"{nazwa}: {ilosc}")
        elif wybor == "2":
            print("\nSklep:")
            for nazwa, cena in ceny.items():
                print(f"{nazwa}: {cena} zlota")
            przedmiot = input("Co chcesz kupic? ").lower()
            if przedmiot in ceny:
                cena = ceny[przedmiot]
                if ekwipunek["zloto"] >= cena:
                    ekwipunek["zloto"] -= cena
                    if przedmiot in ekwipunek:
                        ekwipunek[przedmiot] += 1
                    else:
                        ekwipunek[przedmiot] = 1
                    print(f"Kupiono {przedmiot} za {cena} zlota.")
                else:
                    print("Nie masz wystarczajaco zlota!")
            else:
                print("Nie ma takiego przedmiotu w sklepie.")
        elif wybor == "3":
            przedmiot = input("Jaki przedmiot chcesz uzyc/usunac? ").lower()
            if przedmiot in ekwipunek and przedmiot != "zloto":
                ekwipunek[przedmiot] -= 1
                if ekwipunek[przedmiot] <= 0:
                    del ekwipunek[przedmiot]
                print("Uzyto przedmiotu.")
            else:
                print("Nie masz takiego przedmiotu.")
        elif wybor == "4":
            przedmiot = input("Co chcesz sprawdzic? ").lower()
            if przedmiot in ekwipunek:
                print(f"Masz to: {przedmiot}, sztuk: {ekwipunek[przedmiot]}")
            else:
                print("Nie ma tego w ekwipunku.")
        elif wybor == "5":
            print("Koniec.")
            break
        else:
            print("Zly wybor, wpisz cyfre od 1 do 5.")
gra()
