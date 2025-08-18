# 🐍 Exercício 23 – Cálculo do quadrado de um número com validação

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Solicite ao usuário um **número** (inteiro ou decimal, com vírgula ou ponto)  
- Valide a entrada usando **expressão regular**  
- Calcule o **quadrado** do número usando o operador `**`  
- Exiba o resultado com **duas casas decimais**

> 💡 *Dica:* Use `n**2` para calcular o quadrado de `n` e `re.match(...)` para validar a entrada.  

## 💻 Solução

```python
import re

padrao = r'^\d+(\.\d+)?$'

def calcular_quadrado(n):
    return n**2

while True:
    entrada = input('Digite um valor para elevar ao quadrado: ').replace(',', '.')

    if re.match(padrao, entrada):
        print(f'{calcular_quadrado(float(entrada)):.2f}')
        break
    else:
        print('Valor inválido! Tente novamente.')
```

## 🧠 Explicação

- `padrao` é uma expressão regular que valida números inteiros ou decimais com ponto.
- `replace(',', '.')` permite que o usuário digite com vírgula, convertendo para ponto.
- `re.match(...)` verifica se a entrada é válida.
- A função `calcular_quadrado(n)` retorna o quadrado de `n`.
- O resultado é exibido com duas casas decimais usando `:.2f`.

## ✅ Exemplo de saída

```python
Digite um valor para elevar ao quadrado: 3,5
12.25
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/118F44rDBHmduophTxizq2XTMPi4mjudG?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar validação de entrada, expressões regulares e formatação numérica em Python.

- [Desafio anterior → Desafio 22](./desafio_22.md)  
- [Próximo desafio → Desafio 24](./desafio_24.md)