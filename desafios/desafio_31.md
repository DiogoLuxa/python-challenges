# 🐍 Exercício 31 – Dicionário de números e seus quadrados

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **função** que receba um dicionário como parâmetro  
- O dicionário deve conter números de **1 a 20** como chaves  
- Os valores devem ser o **quadrado das chaves**  
- A função deve imprimir cada par `chave: valor` no console  

> 💡 *Dica:*
> Use o operador `**` para calcular potências.  

## 💻 Solução

```python
def dicionario_quadrados(dic):
    for chave, valor in dic.items():
        print(f'{chave}: {valor}')

dicionario_quadrados({n: n**2 for n in range(1, 21)})
```

## 🧠 Explicação

- `{n: n**2 for n in range(1, 21)}` cria um dicionário por **compreensão**, onde:  
  - As chaves são os números de 1 a 20.  
  - Os valores são os quadrados das chaves.  
- A função `dicionario_quadrados(dic)` percorre o dicionário com `.items()` e imprime cada par.  
- O operador `**` é usado para calcular o quadrado de cada número.  

## ✅ Exemplo de saída

```python
1: 1
2: 4
3: 9
4: 16
...
20: 400
```

> ℹ️ Esse exercício é excelente para praticar **compreensão de dicionários**, uso de `range()` e iteração com `.items()` em Python.

- [Desafio anterior → Desafio 30](./desafio_30.md)