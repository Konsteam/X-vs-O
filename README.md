def user1():
    I = int(input("Введите номер клетки для хода Х: "))
    if 0 < I < 10 :
        for i in range(3):
            for j in range (3):
                if pole[i][j] == I:
                    pole [i][j] = "X"
                    print('Х на поле', I )
    else:
        print("неверный номер клетки")

def user2():
    I = int(input("Введите номер клетки для хода O: "))
    if 0 < I < 10:
        for i in range(3):
            for j in range(3):
                if pole[i][j] == I:
                    pole[i][j] = "O"
                    print('O на поле', I)
    else:
        print("неверный номер клетки")



def pol():
    for i in range (3):
        print(*pole[i])

pole = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
]

pol()
user1()
pol()
user2()
pol()
user1()
pol()
user2()
pol()
user1()
pol()
user2()
pol()
user1()
pol()
user2()
pol()
