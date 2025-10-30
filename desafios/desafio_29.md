# 🐍 Exercício 29 – Concatenação de duas strings

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **função** que receba duas strings como parâmetros  
- Concatene as duas strings usando o operador `+`  
- Imprima o resultado no console  

> 💡 *Dica:* Em Python, `x + y` concatena duas strings.

## 💻 Solução

```python
def concatena(x, y):
    return x + y

while True:
    entrada = input('Digite duas palavras separadas por vírgula ou espaço: ')
    partes = entrada.replace(',', ' ').split()
    
    if len(partes) == 2 and all(n.isalpha() for n in partes):
        x, y = partes
        concatenado = concatena(x, y)
        print(concatenado)
        break
    else:
        print('Valor inválido! Digite somente palavras.')
```

## 🧠 Explicação

- A função `concatena(x, y)` recebe duas strings e retorna a soma delas (concatenação).  
- `entrada.replace(',', ' ').split()` permite que o usuário digite as palavras separadas por vírgula ou espaço.  
- O `if len(partes) == 2` garante que exatamente duas palavras foram informadas.  
- `all(n.isalpha() for n in partes)` valida que ambas as entradas contenham apenas letras.  
- O resultado concatenado é exibido com `print(...)`.

## ✅ Exemplo de saída

```python
Digite duas palavras separadas por vírgula ou espaço: Python, Rocks
PythonRocks
```

> ℹ️ Esse exercício é excelente para praticar definição de funções, manipulação de strings e validação de entrada em Python.

- [Desafio anterior → Desafio 28](./desafio_28.md)
