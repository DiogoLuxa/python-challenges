# 🐍 Exercício 14 – Contagem de letras maiúsculas e minúsculas

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **frase qualquer** como entrada  
- Conte quantas **letras maiúsculas** e quantas **letras minúsculas** existem na frase  
- Imprima os resultados no formato:

```
UPPER CASE X  
LOWER CASE Y
```

> Exemplo:  
Entrada → `Hello world!`  
```
Saída →  
UPPER CASE 1  
LOWER CASE 9
```

## 💻 Solução

```python
import re

entrada_usuario = re.findall(r'[a-zA-ZÀ-ÿ]', input('digite sua palavra ou frase:'))
print(f'UPPER CASE {sum(1 for l in entrada_usuario if l.isupper())}\nLOWER CASE {sum(1 for l in entrada_usuario if l.islower())}')
```

## 🧠 Explicação

- `re.findall(r'[a-zA-ZÀ-ÿ]', ...)` identifica todas as letras (inclusive acentuadas).
- `isupper()` detecta letras maiúsculas.
- `islower()` detecta letras minúsculas.
- A contagem é feita diretamente com `sum()` e expressões geradoras, tornando o código enxuto e eficiente.
- O `print(...)` exibe o resultado conforme o formato solicitado, em duas linhas.

## ✅ Exemplo de saída

```python
digite sua palavra ou frase: Hello world!
UPPER CASE 1
LOWER CASE 9
```

> ℹ️ Uma ótima forma de praticar expressões regulares e classificação de caracteres em Python!

- [Desafio anterior → Desafio 13](./desafio_13.md)  
- [Próximo desafio → Desafio 15](./desafio_15.md)
