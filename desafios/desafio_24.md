# 🐍 Exercício 24 – Exibição de documentação de funções com `__doc__`

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Exiba a **documentação interna (`__doc__`)** de algumas funções built-in do Python, como `abs()`, `int()` e `input()`  
- Defina uma **função personalizada** com sua própria docstring  
- Crie uma função que receba qualquer objeto Python e retorne sua docstring  
- Imprima a documentação da função personalizada usando essa função

> 💡 *Dica:* Todo objeto Python que possui documentação acessa o conteúdo via `objeto.__doc__`

## 💻 Solução

```python
def retorna_nada():
    return

def mostrar_docstring(funcao):
    """
    Retorna a docstring (__doc__) de um objeto Python, como funções, classes ou tipos built-in.
    """
    return funcao.__doc__ or 'Esse objeto não possui docstring.'

# Exibindo documentação de funções built-in
print(mostrar_docstring(abs))
print(mostrar_docstring(int))
print(mostrar_docstring(input))

# Exibindo documentação da função personalizada
print(mostrar_docstring(retorna_nada))
```

## 🧠 Explicação

- A função `mostrar_docstring(funcao)` recebe qualquer objeto e retorna sua docstring.
- A função `retorna_nada()` é definida sem docstring, então o retorno será uma mensagem padrão.
- `abs`, `int` e `input` são funções nativas do Python, e suas descrições internas são acessadas com `__doc__`.
- O uso de `or` garante que, se não houver docstring, uma mensagem alternativa seja exibida.

## ✅ Exemplo de saída

```python
Return the absolute value of the argument.
Convert a number or string to an integer, or return 0 if no arguments are given.
Read a string from standard input. The trailing newline is stripped.
Esse objeto não possui docstring.
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1VQbYX-kSNN2N9781ySGxCxIZr55g46BS?usp=sharing)

> ℹ️ Esse exercício é excelente para explorar introspecção em Python, entender a estrutura de objetos e como acessar metadados como documentação interna.

- [Desafio anterior → Desafio 23](./desafio_23.md)  
- [Próximo desafio → Desafio 25](./desafio_25.md)