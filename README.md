# trabalho-

import time

def bubble_sort(lista):
    n = len(lista)
    for i in range(n):
        for j in range(0, n-i-1):
            if lista[j] > lista[j+1] :
                lista[j], lista[j+1] = lista[j+1], lista[j]

def selection_sort(lista):
    for i in range(len(lista)):
        min_idx = i
        for j in range(i+1, len(lista)):
            if lista[min_idx] > lista[j]:
                min_idx = j
        lista[i], lista[min_idx] = lista[min_idx], lista[i]

def medir_tempo(funcao, lista):
    inicio = time.time()
    funcao(lista)
    fim = time.time()
    return fim - inicio

with open('texto.txt', 'r') as arquivo:
    palavras = []
    for linha in arquivo:
        palavras.extend(linha.split())

# Cópia da lista original para cada método
lista_original = palavras.copy()

# Bubble Sort
lista_bubble = lista_original.copy()
tempo_bubble = medir_tempo(bubble_sort, lista_bubble)
print("Bubble Sort:", tempo_bubble)
print(lista_bubble)

# Selection Sort
lista_selection = lista_original.copy()
tempo_selection = medir_tempo(selection_sort, lista_selection)
print("Selection Sort:", tempo_selection)
print(lista_selection)

# Método nativo sort
lista_sort = lista_original.copy()
tempo_sort = medir_tempo(lista_sort.sort, lista_sort)
print("Método sort:", tempo_sort)
print(lista_sort)

# Escolha do método mais rápido (exemplo: Bubble Sort)
lista_ordenada = lista_bubble

# Gravar em arquivo
with open('palavras_ordenadas.txt', 'w') as arquivo:
    for palavra in lista_ordenada:
        arquivo.write(palavra + '\n')
