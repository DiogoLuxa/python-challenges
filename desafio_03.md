# 🐍 Exercício 03 – Dicionário com quadrados de números

## 🧩 Enunciado

Com um número inteiro `n` fornecido pelo usuário, escreva um programa que gere um **dicionário**, onde cada chave `i` representa um número entre `1` e `n` (inclusive), e o valor correspondente seja o **quadrado de `i`** (`i × i`).  
Ao final, o programa deve imprimir o dicionário.

> Exemplo:  
Entrada → `8`  
Saída → `{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}`

> 💡 *Dica:* Use `input()` para capturar o valor.

## 💻 Solução

```python
while True:
    try:
        numero = int(input('digite um número inteiro: '))
    except ValueError:
        print('tem que ser um número inteiro!')
    else:
        break

print({n: n**2 for n in range(1, numero + 1)})
```

## 🧠 Explicação

- `while True:` cria um loop que continua até que uma entrada válida seja digitada.
- `try/except` trata casos em que o usuário insere algo que não pode ser convertido para inteiro.
- `range(1, numero + 1)` gera os valores entre `1` e `n`, inclusive.
- `{n: n**2 for n in ...}` é uma **dict comprehension** que cria o dicionário onde cada número é a chave e seu quadrado é o valor.
- `print(...)` exibe o dicionário gerado.

## ✅ Exemplo de saída

```python
digite um número inteiro: 8
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}
```

> ℹ️ Esse exercício reforça o uso de compreensões em Python e a manipulação de tipos de dados como dicionários. Simples, direto e poderoso.
