# adivinhacao
adivinhação das letras do alfabeto de a à z, com 10 tentativas máximas
import random

def jogo_adivinhacao_letras():
    print("Bem-vindo ao Jogo de Adivinhação de Letras!")
    print("Estou pensando em uma letra entre A e Z. Tente adivinhar!")
    
    letra_secreta = chr(random.randint(ord('a'), ord('z')))
    tentativas = 0
    max_tentativas = 10
    letras_tentadas = []
    
    while tentativas < max_tentativas:
        tentativa = input(f"Tentativa {tentativas + 1}/{max_tentativas}. Seu palpite: ").lower()
        
        if len(tentativa) != 1 or not tentativa.isalpha():
            print("Por favor, digite apenas UMA letra de A a Z.")
            continue
        
        if tentativa in letras_tentadas:
            print("Você já tentou essa letra. Tente outra!")
            continue
            
        letras_tentadas.append(tentativa)
        tentativas += 1
        
        if tentativa < letra_secreta:
            print("A letra secreta está DEPOIS desta na ordem alfabética!")
        elif tentativa > letra_secreta:
            print("A letra secreta está ANTES desta na ordem alfabética!")
        else:
            print(f"Parabéns! Você acertou a letra '{letra_secreta.upper()}' em {tentativas} tentativas!")
            return
    
    print(f"Fim de jogo! A letra era '{letra_secreta.upper()}'.")
    print(f"Letras tentadas: {', '.join([l.upper() for l in letras_tentadas])}")

# Iniciar o jogo
jogo_adivinhacao_letras()
