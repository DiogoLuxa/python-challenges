# 🐍 Exercício 02 – Fatorial de um número fornecido

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que calcule o **fatorial de um número inteiro** fornecido pelo usuário. O resultado deve ser **impresso em uma única linha**, em formato numérico simples (sem lista), como no exemplo abaixo:

> Exemplo:  
Entrada → `8`  
Saída → `40320`

> 💡 *Dica:* Use `input()` para capturar o valor.

## 💻 Solução

```python
from functools import reduce

while True:
    try:
        numero = int(input('digite um número inteiro: '))
        break
    except ValueError:
        print('tem que ser um número inteiro!')

print(reduce(lambda acc, n: acc * n, list(range(1, numero + 1)), 1))
```

## 🧠 Explicação

- `input()` solicita a entrada do usuário e o `int()` garante que seja um número inteiro.
- O `while True` cria um laço que só encerra quando o usuário digitar corretamente.
- `reduce(lambda acc, n: acc * n, ...)` acumula a multiplicação dos elementos, calculando o fatorial.
- `range(1, numero + 1)` cria uma lista de números de 1 até o número fornecido.
- `print(...)` exibe diretamente o valor final do fatorial.

## ✅ Exemplo de saída

```python
digite um número inteiro: 8
40320
```

> ℹ️ Essa solução lida com entrada inválida e calcula o fatorial de forma eficiente usando programação funcional com `reduce`.

---

- [Desafio anterior → Desafio 01](./desafio_01.md)  
- [Próximo desafio → Desafio 03](./desafio_03.md)