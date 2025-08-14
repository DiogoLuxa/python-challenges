# 🐍 Exercício 20 – Gerador de números divisíveis por 7

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **classe com um gerador** que itere sobre os números **divisíveis por 7**  
- O intervalo deve ir de **0 até n**, onde `n` é fornecido pelo usuário

> Exemplo:  
Entrada → `7`  
Saída →  
```
0  
7
```

> 💡 *Dica:* Use `yield` dentro de um método da classe para criar o gerador.  
Valide a entrada com expressões regulares para garantir que seja um número inteiro positivo.

## 💻 Solução

```python
import re

class DivisiveisPorSete:
    """Classe que gera números divisíveis por 7 até um limite especificado."""
    def __init__(self, limite):
        self.limite = limite
        
    def gerar_divisiveis(self):
        for numero in range(self.limite + 1):
            if numero % 7 == 0:
                yield numero

while True:
    entrada = input('Digite um número inteiro: ')
    if re.match(r'^\d+$', entrada):
        limite = int(entrada)
        break
    print('Valor inválido!')

divisiveis = DivisiveisPorSete(limite)

for valor in divisiveis.gerar_divisiveis():
    print(valor)
```

## 🧠 Explicação

- A classe `DivisiveisPorSete` recebe um limite e gera números de 0 até esse limite.
- O método `gerar_divisiveis()` usa `yield` para retornar apenas os números divisíveis por 7.
- O loop `for valor in ...` consome o gerador e imprime os valores um por um.
- A entrada é validada com `re.match(...)` para garantir que seja um número inteiro positivo.

## ✅ Exemplo de saída

```python
Digite um número inteiro: 7
0
7
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/11NifZYVv3cNMOMsbkNyFCiIMO2oNeVme?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar criação de geradores, uso de `yield` e encapsulamento com classes em Python.

- [Desafio anterior → Desafio 19](./desafio_19.md)  
- [Próximo desafio → Desafio 21](./desafio_21.md)