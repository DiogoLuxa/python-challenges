# 🐍 Exercício 01 – Números divisíveis por 7 mas não múltiplos de 5

## 🧩 Enunciado

Escreva um programa que encontre todos os números **divisíveis por 7** mas que **não sejam múltiplos de 5**, no intervalo entre **2000 e 3200** (incluindo os limites).

Os números encontrados devem ser impressos em uma única linha, separados por **vírgula**.

> 💡 *Dica:* Considere utilizar o método `range(início, fim)` para percorrer o intervalo.

## 💻 Solução

```python
print(*[n for n in range(2000, 3201) if n % 7 == 0 and n % 5 != 0], sep=', ')
```

## 🧠 Explicação

- `range(2000, 3201)` percorre os números de 2000 até 3200 (inclusive).
- A list comprehension `[n for n in ... if ...]` filtra os valores:
  - `n % 7 == 0` → verifica se o número é divisível por 7.
  - `n % 5 != 0` → exclui os que são múltiplos de 5.
- `print(*lista, sep=', ')` imprime os números da lista separados por vírgula, todos em uma única linha.

## ✅ Exemplo de saída

```
2002,2009,2016,2023,2037,2044,...
```

> ℹ️ Essa é uma solução compacta e eficiente usando list comprehension e desempacotamento com `*`. Ideal para quem já domina os fundamentos de Python.

