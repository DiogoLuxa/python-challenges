# 🐍 Exercício 27 – Conversão de inteiro para string

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **função** que receba um número inteiro como parâmetro  
- Converta esse número em **string** usando a função `str()`  
- Imprima o valor convertido no console

> 💡 *Dica:* Em Python, `str(n)` converte qualquer número em string.

## 💻 Solução

```python
def int_para_str(n):
    return str(n)

print(int_para_str(3))
```

## 🧠 Explicação

- A função `int_para_str(n)` recebe um número inteiro `n`.  
- O comando `str(n)` converte o número em uma string.  
- O `print(...)` exibe o valor convertido no console.  
- Esse padrão pode ser aplicado a qualquer número inteiro.

## ✅ Exemplo de saída

```python
3
```

*(Aqui o número `3` é exibido como string, mas visualmente aparece igual. A diferença é que agora ele é do tipo `str` em Python.)*

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1SaW-qZ1qaX12bYaED5MYhWrLAQ7bK8-9?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar definição de funções e conversão de tipos em Python.

- [Desafio anterior → Desafio 26](./desafio_26.md)  
- [Próximo desafio → Desafio 28](./desafio_28.md)