# 🐍 Exercício 30 – Comparação de comprimento entre duas strings

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **função** que receba duas strings como parâmetros  
- Compare o comprimento das duas strings usando `len()`  
- Imprima no console a string com **maior comprimento**  
- Caso ambas tenham o **mesmo tamanho**, imprima as duas strings, uma em cada linha  

> 💡 *Dica:* Use `len()` para obter o tamanho de uma string.

## 💻 Solução

```python
def max_len(x, y):
    print(max([x, y], key=len)) if len(x) != len(y) else print(x, y, sep='\n')

while True:
    try:
        x, y = input('Digite duas palavras separadas por vírgula ou espaço: ').replace(',', ' ').split()
        break
    except ValueError:
        print('Valor inválido! Tente novamente.')

max_len(*[valor.capitalize() for valor in [x, y]])
```

## 🧠 Explicação

- A função `max_len(x, y)` compara o comprimento das duas strings:  
  - Se forem diferentes, imprime apenas a maior.  
  - Se forem iguais, imprime ambas em linhas separadas.  
- `entrada.replace(',', ' ').split()` permite que o usuário digite as palavras separadas por vírgula ou espaço.  
- O bloco `try/except` garante que exatamente duas palavras sejam fornecidas.  
- A list comprehension `[valor.capitalize() for valor in [x, y]]` padroniza as palavras com a primeira letra maiúscula.  

## ✅ Exemplo de saída

```python
Digite duas palavras separadas por vírgula ou espaço: Python, Java
Python
```

```python
Digite duas palavras separadas por vírgula ou espaço: CSharp, Kotlin
Csharp
Kotlin
```

> ℹ️ Esse exercício é excelente para praticar definição de funções, uso de `len()` e controle condicional em Python.

- [Desafio anterior → Desafio 29](./desafio_29.md)
- [Próximo desafio → Desafio 31](./desafio_31.md)