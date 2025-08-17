# 🐍 Exercício 22 – Frequência de palavras com ordenação alfanumérica

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **frase como entrada**  
- Calcule a **frequência de cada palavra** presente na frase  
- Imprima o resultado no formato `palavra:frequência`, **ordenado alfanumericamente pela palavra**

> Exemplo:  
Entrada →  
```
New to Python or choosing between Python 2 and Python 3? Read Python 2 or Python 3.
```  
Saída →  
```
2:2  
3.:1  
3?:1  
New:1  
Python:5  
Read:1  
and:1  
between:1  
choosing:1  
or:2  
to:1
```

## 💻 Solução

```python
entrada = sorted(input('Digite seu texto aqui: ').split())

entrada_para_dicionario = {n: entrada.count(n) for n in entrada}

[print(f'{chave}:{entrada_para_dicionario[chave]}') for chave in entrada_para_dicionario]
```

## 🧠 Explicação

- `input(...).split()` separa a frase em palavras usando espaços como delimitadores.
- `sorted(...)` organiza as palavras em ordem alfanumérica.
- O dicionário `entrada_para_dicionario` armazena a contagem de cada palavra.
- A list comprehension com `print(...)` exibe cada par `palavra:frequência`.

## ✅ Exemplo de saída

```python
Digite seu texto aqui: New to Python or choosing between Python 2 and Python 3? Read Python 2 or Python 3.
2:2
3.:1
3?:1
New:1
Python:5
Read:1
and:1
between:1
choosing:1
or:2
to:1
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1bygo_02WKDbMUdUcZbx4guj8RgPOxaGZ?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar manipulação de strings, dicionários e ordenação em Python.

- [Desafio anterior → Desafio 21](./desafio_21.md)  
- [Próximo desafio → Desafio 23](./desafio_23.md)