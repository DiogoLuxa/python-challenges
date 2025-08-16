# 🐍 Exercício 21 – Distância entre ponto inicial e posição final de um robô

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Simule o movimento de um robô em um plano cartesiano, partindo da origem `(0,0)`  
- Receba uma **sequência de comandos** no formato:
  - `UP n`
  - `DOWN n`
  - `LEFT n`
  - `RIGHT n`
- Calcule a **distância euclidiana** entre a posição final e o ponto inicial  
- Imprima o valor **arredondado para o inteiro mais próximo**

> Exemplo:  
Entrada →  
```
UP 5  
DOWN 3  
LEFT 3  
RIGHT 2
```  
Saída → `2`

> 💡 *Dica:* Use `math.sqrt(x² + y²)` para calcular a distância.  
Use expressões regulares para extrair os comandos e valores.

## 💻 Solução

```python
import re
import math

padrao = r'\b(up|down|left|right)[ ,]+(\d+)\b'

entrada = re.findall(padrao, input(
    'Digite os movimentos (ex: "up 5, left 3, down 2"): '), flags=re.IGNORECASE)

x, y = 0, 0

for direcao, passos in entrada:
    passos = int(passos)
    match direcao.lower():
        case 'up':
            y += passos
        case 'down':
            y -= passos
        case 'left':
            x -= passos
        case 'right':
            x += passos

distancia_euclidean = round(math.sqrt(x**2 + y**2))

print(distancia_euclidean)
```

## 🧠 Explicação

- A expressão regular extrai os comandos e passos da entrada do usuário.
- As variáveis `x` e `y` representam a posição atual do robô.
- O `match/case` atualiza `x` ou `y` conforme a direção.
- A distância é calculada com a fórmula euclidiana:  
  \[
  \text{distância} = \sqrt{x^2 + y^2}
  \]
- O resultado é arredondado com `round(...)` para o inteiro mais próximo.

## ✅ Exemplo de saída

```python
Digite os movimentos (ex: "up 5, left 3, down 2"): up 5, down 3, left 3, right 2
2
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/12x5XD9gtqwNe7IW2wh1rJ267-aKhqv4n?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar vetores, distância euclidiana, expressões regulares e controle de fluxo com `match/case`.

- [Desafio anterior → Desafio 20](./desafio_20.md)  
- [Próximo desafio → Desafio 22](./desafio_22.md)