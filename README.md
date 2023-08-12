def user1():
    global hod_user1
    global hod
    I = int(input("Введите номер клетки для хода Х: "))
    if 0 < I < 10:
        if I not in history:
            history.append(I)
            for i in range(3):
                for j in range(3):
                    if pole[i][j] == I:
                        pole[i][j] = "X"
                        print('Х на поле', I)
                        hod_user1.append(I)
                        hod_user1.sort()
                        if hod > 4:
                            semai = list(map(set, wins_comb))
                            for v in range(len(semai)):
                                wen = set(hod_user1).intersection(semai[v])
                                if len(wen) == 3:
                                    hod_user1 = list(wen)
                                    hod_user1.sort()
        else:
            print("Клетка уже занята")
            return user1()
    else:
        print("неверный номер клетки")
        return user1()

def user2():
    global hod_user2
    I = int(input("Введите номер клетки для хода O: "))
    if 0 < I < 10:
        if I not in history:
            history.append(I)
            for i in range(3):
                for j in range(3):
                    if pole[i][j] == I:
                        pole[i][j] = "O"
                        print('O на поле', I)
                        hod_user2.append(I)
                        hod_user2.sort()
                        if hod > 5:
                            semai = list(map(set, wins_comb))
                            for v in range(len(semai)):
                                wen = set(hod_user2).intersection(semai[v])
                                if len(wen) == 3:
                                    hod_user2 = list(wen)
                                    hod_user2.sort()
        else:
            print("Клетка уже занята")
            return user2()
    else:
        print("неверный номер клетки")
        return user2()


def pol():
    for i in range(3):
        print(*pole[i])


def game():
    global hod
    pol()
    user1()
    hod += 1
    if hod != 9:
        if hod_user1 not in wins_comb:
            pol()
            user2()
            hod += 1
            if hod_user2 not in wins_comb:
                game()
            else:
                pol()
                print("Победа игрока О")
        else:
            pol()
            print("Победа игрока Х")
    else:
        pol()
        print("Ничья!")

history = []
hod = 0
pole = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
]

wins_comb = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    [1, 4, 7],
    [2, 5, 8],
    [3, 6, 9],
    [1, 5, 9],
    [3, 5, 7]
]

hod_user1 = []
hod_user2 = []

game()
