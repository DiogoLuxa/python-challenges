# 🐍 Exercício 28 – Soma de dois inteiros em formato string

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **função** que receba dois números inteiros em formato **string**  
- Converta-os para inteiros usando `int()`  
- Calcule a **soma** dos dois números  
- Imprima o resultado no console  

> 💡 *Dica:* Use `map(int, partes)` para converter as strings em inteiros.

## 💻 Solução

```python
def soma_dois(x, y):
    return x + y

while True:
    entrada = input('Digite dois números inteiros separados por vírgula ou espaço: ')
    partes = entrada.replace(',', ' ').split()
    if len(partes) == 2:
        try:
            x, y = map(int, partes)
            soma = soma_dois(x, y)
            print(soma)
            break
        except ValueError:
            pass
    print('Valor inválido! Digite apenas dois números inteiros.')
```

## 🧠 Explicação

- A função `soma_dois(x, y)` recebe dois inteiros e retorna a soma.  
- `entrada.replace(',', ' ').split()` permite que o usuário digite os números separados por vírgula ou espaço.  
- O `if len(partes) == 2` garante que exatamente dois valores foram informados.  
- `map(int, partes)` converte as strings em inteiros.  
- Caso a conversão falhe (`ValueError`), o programa pede novamente a entrada.  
- O resultado é exibido com `print(...)`.

## ✅ Exemplo de saída

```python
Digite dois números inteiros separados por vírgula ou espaço: 4, 9
13
```

> ℹ️ Esse exercício é excelente para praticar definição de funções, conversão de tipos e validação de entrada em Python.

- [Desafio anterior → Desafio 27](./desafio_27.md)
- [Próximo desafio → Desafio 29](./desafio_29.md)