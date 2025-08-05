# 🐍 Exercício 13 – Contagem de letras e dígitos em uma frase

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **frase qualquer** como entrada  
- Conte quantas **letras** e quantos **dígitos** existem na frase  
- Imprima os resultados em duas linhas, no formato:

```
LETRAS X  
DIGITOS Y
```

> Exemplo:  
Entrada → `hello world! 123`  
```
Saída →  
LETRAS 10  
DIGITOS 3
```

> 💡 *Dica:* Use `re.findall(r"\w", ...)` para capturar letras e números, e filtre com `isalpha()` e `isdigit()`.

## 💻 Solução

### ✅ Forma 1 – Usando `for` com listas separadas

```python
import re

letras = []
digitos = []
resposta = re.findall(r"\w", input('digite uma frase qualquer:'))

for i in resposta:
    if i.isdigit():
        digitos.append(i)
    else:
        letras.append(i)

print(f'LETRAS {len(letras)}\nDIGITOS {len(digitos)}')
```

### ✅ Forma 2 – Usando `filter()` com `isalpha()` e `isdigit()`

```python
import re

resposta = re.findall(r"\w", input('digite uma frase qualquer:'))
letras = [*filter(lambda i: i.isalpha(), resposta)]
digitos = [*filter(lambda i: i.isdigit(), resposta)]

print(f'LETRAS {len(letras)}\nDIGITOS {len(digitos)}')
```

### ✅ Forma 3 – Usando `sum()` com expressões geradoras

```python
import re

resposta = re.findall(r"\w", input('digite uma frase qualquer:'))
letras = sum(1 for i in resposta if i.isalpha())
digitos = sum(1 for i in resposta if i.isdigit())

print(f'LETRAS {letras}\nDIGITOS {digitos}')
```

## 🧠 Explicação

- `re.findall(r"\w", ...)` captura todos os caracteres alfanuméricos (letras e dígitos).
- `isalpha()` identifica letras.
- `isdigit()` identifica números.
- A primeira forma usa listas para armazenar e contar.
- A segunda forma usa `filter()` para separar os tipos.
- A terceira forma usa `sum()` com geradores para contar diretamente.
- `print(...)` exibe os resultados formatados em duas linhas.

## ✅ Exemplo de saída

```python
digite uma frase qualquer: hello world! 123
LETRAS 10
DIGITOS 3
```

> ℹ️ Esse exercício é excelente para praticar expressões regulares, filtragem de dados e contagem condicional em Python.

- [Desafio anterior → Desafio 12](./desafio_12.md)  
- [Próximo desafio → Desafio 14](./desafio_14.md)
