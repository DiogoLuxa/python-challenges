# 🐍 Exercício 19 – Ordenação de tuplas por múltiplos critérios

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **lista** no formato `nome, idade, nota` via entrada do usuário  
- Ordene a lista em **ordem crescente**, com base nos seguintes critérios:
  1. Nome
  2. Idade
  3. Nota

> A prioridade é nome > idade > nota.

- Imprima a lista ordenada como uma lista de tuplas

> Exemplo:  
Entrada →  
```
Tom,19,80 John,20,90 Jony,17,91 Jony,17,93 Json,21,85
```  
```
Saída →  
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]
```

## 💻 Solução

```python
import re
from operator import itemgetter

entrada = re.findall(r"[a-zA-Z]+,\d+,\d+", input('Cole sua lista de nomes, idades e notas (ex: Tom,19,80 John,20,90): '))
lista = [tuple(item.split(',')) for item in entrada]
lista_ordenada = sorted(lista, key=itemgetter(0, 1, 2))

print(lista_ordenada)
```

## 🧠 Explicação

- `re.findall(...)` extrai todas as tuplas válidas no formato `nome,idade,nota`.
- `split(',')` transforma cada string em uma tupla.
- `sorted(..., key=itemgetter(0, 1, 2))` ordena por nome, depois idade, depois nota.
- A saída é exibida como uma lista de tuplas ordenadas.

## ✅ Exemplo de saída

```python
Cole sua lista de nomes, idades e notas (ex: Tom,19,80 John,20,90): Tom,19,80 John,20,90 Jony,17,91 Jony,17,93 Json,21,85
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]
```

> ℹ️ Esse exercício é excelente para praticar ordenação com múltiplos critérios, manipulação de tuplas e expressões regulares em Python.

- [Desafio anterior → Desafio 18](./desafio_18.md)  
- [Próximo desafio → Desafio 20](./desafio_20.md)