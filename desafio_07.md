# 🐍 Exercício 07 – Geração de matriz bidimensional com produto de índices

## 🧩 Enunciado

Escreva um programa que receba **dois números inteiros X e Y** como entrada.  
O programa deve gerar uma **matriz bidimensional (lista de listas)** de tamanho `X × Y`, onde o valor de cada elemento na posição `(i, j)` seja o resultado de `i × j`.

> Exemplo:  
Entrada → `3,5`  
Saída → `[[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]]`

## 💻 Solução

```python
while True:
    try:
        valores = [int(n.strip()) for n in input('digite X,Y: ').split(',')]
        if len(valores) != 2 or any(n < 0 for n in valores):
            raise ValueError
        break
    except ValueError:
        print('Digite apenas dois números inteiros positivos e separados por vírgula.')

x, y = valores

matriz = [[n * i for n in range(y)] for i in range(x)]

print(matriz)
```

## 🧠 Explicação

- `input()` solicita ao usuário os valores de `X` e `Y`, separados por vírgula.
- `.split(',')` divide a entrada e `int(n.strip())` garante que sejam inteiros válidos.
- A validação rejeita entradas negativas ou com quantidade incorreta de números.
- A matriz é gerada com list comprehension dupla:
  - `for i in range(x)` para cada linha
  - `for n in range(y)` para cada coluna
  - `n * i` calcula o valor do elemento da célula
- `print(matriz)` exibe a estrutura final da matriz como lista de listas.

## ✅ Exemplo de saída

```python
digite X,Y: 3,5
[[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]]
```

> ℹ️ Esse exercício reforça raciocínio matricial e uso de compreensão de listas — fundamentais para quem avança com Python em ciência de dados ou lógica de programação.