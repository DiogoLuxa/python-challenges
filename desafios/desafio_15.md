# 🐍 Exercício 15 – Cálculo de a + aa + aaa + aaaa

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba um **único dígito inteiro** como entrada  
- Calcule o valor da expressão:  
  ```
  a + aa + aaa + aaaa
  ```
  onde `a` é o dígito fornecido

- Imprima o resultado como um número inteiro

> Exemplo:  
Entrada → `9`  
Saída → `11106`

> 💡 *Dica:* Use manipulação matemática ou string para construir os termos `a`, `aa`, `aaa`, `aaaa`.

## 💻 Solução

```python
import re
from functools import reduce

while True:
    entrada_usuario = int(*re.findall(r'^\d+$', input('Digite um número inteiro: ')))
    if entrada_usuario:
        break

print(reduce(lambda acc, i: acc + (entrada_usuario * ((10**i - 1) // 9)), range(1, 5), 0))
```

## 🧠 Explicação

- `re.findall(r'^\d+$', ...)` garante que a entrada seja um número inteiro positivo.
- `int(...)` converte o valor capturado para inteiro.
- `reduce(...)` acumula a soma dos termos `a`, `aa`, `aaa`, `aaaa`:
  - A fórmula `(10**i - 1) // 9` gera números como `1`, `11`, `111`, `1111`
  - Multiplicando pelo dígito `a` gera `a`, `aa`, `aaa`, `aaaa`
- `range(1, 5)` define os quatro termos da sequência.
- O resultado é impresso diretamente com `print(...)`.

## ✅ Exemplo de saída

```python
Digite um número inteiro: 9
11106
```

> ℹ️ Esse exercício é excelente para praticar manipulação matemática, uso de `reduce` e validação de entrada com expressões regulares.

- [Desafio anterior → Desafio 14](./desafio_14.md)  
- [Próximo desafio → Desafio 16](./desafio_16.md)