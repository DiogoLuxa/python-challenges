# 🐍 Exercício 26 – Soma de dois números com validação

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Solicite ao usuário **dois números** (inteiros ou decimais), separados por vírgula ou espaço  
- Valide a entrada para garantir que sejam dois valores numéricos  
- Calcule a **soma dos dois números** usando uma função  
- Exiba o resultado como número decimal

## 💻 Solução

```python
def soma_dois(x, y):
    return x + y

while True:
    entrada = input("Digite dois números separados por vírgula ou espaço: ")
    partes = entrada.replace(",", " ").split()
    if len(partes) == 2:
        try:
            x, y = map(float, partes)
            break
        except ValueError:
            pass
    print("Valor inválido. Tente novamente.")

print(soma_dois(x, y))
```

## 🧠 Explicação

- A função `soma_dois(x, y)` recebe dois números e retorna a soma.  
- `entrada.replace(",", " ").split()` permite que o usuário digite números separados por vírgula ou espaço.  
- O `if len(partes) == 2` garante que exatamente dois valores foram informados.  
- `map(float, partes)` converte os valores para números decimais.  
- Caso a conversão falhe, o programa pede novamente a entrada.  
- O resultado final é exibido com `print(...)`.

## ✅ Exemplo de saída

```python
Digite dois números separados por vírgula ou espaço: 3, 7
10.0
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1yB2NEZiAily3Gks0kpnYGztlKVE10TXW?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar definição de funções, manipulação de strings e validação de entrada em Python.

- [Desafio anterior → Desafio 25](./desafio_25.md)  
- [Próximo desafio → Desafio 27](./desafio_27.md)