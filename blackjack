from random import randint
from time import sleep

baralho = ['Ás', 'Ás', 'Ás', 'Ás', 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 5, 5, 5, 5, 6, 6, 6, 6, 7, 7, 7, 7,
           8, 8, 8, 8, 9, 9, 9, 9, 10, 10, 10, 10, 'J', 'J', 'J', 'J', 'Q', 'Q', 'Q', 'Q', 'K', 'K', 'K', 'K']
meuspontos = 0
perdeu = False
ganhou = False
pontosoponentes = 0


def pegacarta(cartas):

    carta = cartas[randint(0, len(cartas))]
    cartas.remove(carta)
    verificacarta(carta)
    return carta


def define_dificuldade():
    print("""Escolha a dificuldade que desejar:
Fácil - O oponente tirará entre 15 e 21
Médio - O oponente tirará entre 17 e 21
Difícil- O oponente tirará entre 18 e 21""")
    while True:
        escolha = (input("""
[ 1 ] Fácil
[ 2 ] Médio
[ 3 ] Dificíl
Sua escolha:"""))
        if escolha.isalpha():
            print('Dificuldade inválida, digite um número entre 1 e 3')
        elif 1 <= int(escolha) <= 3:
            return int(escolha)


def define_pontos_oponente(nivel):
    global pontosoponentes
    if nivel == 1:
        pontosoponentes = randint(15, 21)
    elif nivel == 2:
        pontosoponentes = randint(17, 21)
    else:
        pontosoponentes = randint(18, 21)


def verificacarta(carta):
    global meuspontos
    print('=' * 40)
    print(f'     Você tirou a carta {carta}')
    if type(carta) == int:
        meuspontos += carta
    else:
        if carta in 'JQK':
            meuspontos += 10
        elif carta == 'Ás':
            if meuspontos > 11:
                meuspontos += 1
            else:
                meuspontos += 10


def pega_as_duas_primeiras_cartas(cartas):
    global meuspontos
    print('Distribuindo suas cartas')
    sleep(1)
    a = pegacarta(cartas)
    b = pegacarta(cartas)
    print('=' * 40)
    print(f'Suas cartas iniciais são {a} e {b}, você possui agora {meuspontos} pontos')


print('-' * 40)
print('{:^40}'.format("Bem vindo ao jogo BlackJack"))
print('-' * 40)
dificuldade = define_dificuldade()
define_pontos_oponente(dificuldade)
pega_as_duas_primeiras_cartas(baralho)
while True:

    resposta = int(input(f'''
Você gostaria de pegar mais uma carta? você possui {meuspontos} pontos. [ 1 ] Sim  [ 2 ] Não:'''))
    if resposta == 1:
        pegacarta(baralho)
        print('=' * 40)
    elif resposta == 2:
        print('Encerrando o jogo...')
        sleep(1)
        print(f'Você fez {meuspontos} pontos e o oponente fez {pontosoponentes} pontos')
        if meuspontos > pontosoponentes:
            print('Você ganhou')
        elif meuspontos < pontosoponentes:
            print('Você perdeu!')
        else:
            print('Houve um empate')
        break
    perdeu = meuspontos > 21
    ganhou = meuspontos == 21

    if perdeu:
        print(f'Você passou de 21 pontos, você perdeu com {meuspontos} pontos:(')
        break
    if ganhou:
        print('Parabéns, você atingiu 21 pontos. Você ganhou!')
        break
