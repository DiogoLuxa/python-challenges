# 🐍 Exercício 16 – Quadrado dos números ímpares de uma lista

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **sequência de números inteiros separados por vírgula**  
- Calcule o **quadrado de cada número ímpar** da lista  
- Imprima os resultados em uma **única linha**, separados por vírgula

> Exemplo:  
Entrada → `1,2,3,4,5,6,7,8,9`  
Saída → `1,9,25,49,81`

> 💡 *Dica:* Use **list comprehension** para aplicar a operação e `int(x) % 2 != 0` para filtrar os ímpares.  
Use `print(..., sep=',')` para formatar a saída.

## 💻 Solução

```python
import re

while True:
    sequencia_numeros_usuario = re.findall(r"(?:,|^)(\d+)(?=,|$)", input('Digite uma sequencia de numeros separados por virgula: '))
    if sequencia_numeros_usuario:
        break

print(*[int(x) ** 2 for x in sequencia_numeros_usuario if int(x) % 2 != 0], sep=',')
```

## 🧠 Explicação

- `input(...)` recebe a sequência digitada pelo usuário.
- `re.findall(...)` extrai os números inteiros da entrada, ignorando espaços ou caracteres inválidos.
- A **list comprehension** filtra os ímpares e calcula seus quadrados.
- `print(*lista, sep=',')` imprime os elementos da lista separados por vírgula, sem colchetes.

## ✅ Exemplo de saída

```python
Digite uma sequencia de numeros separados por virgula: 1,2,3,4,5,6,7,8,9
1,9,25,49,81
```

> ℹ️ Esse exercício é excelente para treinar list comprehension, expressões regulares e formatação de saída.

- [Desafio anterior → Desafio 15](./desafio_15.md)  
- [Próximo desafio → Desafio 17](./desafio_17.md)
