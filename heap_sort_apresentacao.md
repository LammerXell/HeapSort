---
marp: false
theme: default
paginate: true
title: Algoritmo Heap Sort
description: Apresentação sobre o algoritmo Heap Sort, incluindo teoria, implementação em Python e comparação com outros métodos de ordenação.
---

# Heap Sort

**Disciplina:** Estrutura de Dados  
**Aluno:** Sócrates Luna  
**Data:** 28/07/2025

---

## Introdução

- O **Heap Sort** é um algoritmo de ordenação baseado em uma estrutura de dados chamada **Heap** (ou fila de prioridade).
- Usa uma estrutura de **árvore binária completa** representada como vetor.
- É um algoritmo **não estável** com **complexidade O(n log n)** no pior caso.

---

## Motivação

- Ótimo desempenho em grandes volumes de dados.
- Usa memória constante (in-place).
- Baseado na estrutura **Heap Máximo ou Mínimo**.

---

## Complexidade

| Caso           | Complexidade |
|----------------|--------------|
| Melhor Caso    | O(n log n)   |
| Caso Médio     | O(n log n)   |
| Pior Caso      | O(n log n)   |
| Espaço Extra   | O(1)         |

---

## Funcionamento

1. Construir o heap a partir do vetor.
2. Repetidamente:
   - Trocar o primeiro (maior) com o último.
   - Reduzir o tamanho do heap.
   - Aplicar o `heapify`.

---

## Implementação em Python

```python
def heapify(arr, n, i):
    maior = i
    esq = 2 * i + 1
    dir = 2 * i + 2

    if esq < n and arr[esq] > arr[maior]:
        maior = esq
    if dir < n and arr[dir] > arr[maior]:
        maior = dir
    if maior != i:
        arr[i], arr[maior] = arr[maior], arr[i]
        heapify(arr, n, maior)

def heap_sort(arr):
    n = len(arr)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]
        heapify(arr, i, 0)

```
---
## Exemplo prático

🔢 Vetor de entrada:

```python
[4, 10, 3, 5, 1]
```
Após construir o Heap
```python
[10, 5, 3, 4, 1]
```
Ordenação Final
```python
[1, 3, 4, 5, 10]
```
---
## Comparações com outros algoritmos
|Algoritmo	|Estável	|In-place	 |Pior Caso  |
|-----------|-----------|-------------|-----------|
|Heap Sort	|❌        |✅          |O(n log n) |
|Merge Sort	|✅	      |❌	      |O(n log n) |
|Quick Sort	|❌	      |✅	      |O(n²)      |

---
## Vantagens
- Desempenho garantido: O(n log n)
- Uso eficiente da memória: In-place

## ❌ Desvantagens
- Não preserva a ordem de elementos iguais
- Mais lento que QuickSort na prática
---
## Conclusão
- Heap Sort é eficiente e previsível
- Útil em sistemas com pouca memória
- Ideal quando o pior caso precisa ser controlado
- Não indicado se a estabilidade for importante
---
## Visualização da execução
🔗 Acesse o passo a passo:

https://visualgo.net/en/heap
