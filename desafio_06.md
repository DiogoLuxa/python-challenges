# 🐍 Exercício 06 – Fórmula matemática com filtragem e função personalizada

## 🧩 Enunciado

Escreva um programa que:

- Solicite uma **sequência de números inteiros separados por vírgula**.
- Calcule, para cada número da sequência, o valor da fórmula matemática abaixo:
  
$$
Q = \sqrt{\frac{2 \times C \times D}{H}}
$$

Valores fixos:
- `C = 50`
- `H = 30`

A saída deve ser uma **lista dos resultados arredondados** dos cálculos, separados por vírgula.

> Exemplo:  
Entrada → `100,150,180`  
Saída → `18,22,24`

> 💡 *Dica:* Use uma função personalizada para aplicar a fórmula e trate entradas inválidas com `isdigit()`.

## 💻 Solução

```python
import math

def formula_xpto(*d, c=50, h=30):
    """
    Calcula o valor da fórmula: √((2*c*n)/h) para cada número 'n' da sequência.

    Parâmetros:
    - *d: sequência de valores (strings ou números inteiros)
    - c: constante multiplicadora (default = 50)
    - h: constante divisora (default = 30)

    Retorna:
    - Lista com os resultados arredondados para cada valor da sequência.
    """
    return [round(float(math.sqrt((2 * c * int(n)) / h))) for n in d]

sequencia_usuario = input('digite uma sequência de números inteiros separados por vírgula: ')
sequencia_usuario_filtrada = [*filter(lambda n: n.strip().isdigit(), sequencia_usuario.split(','))]

print(*formula_xpto(*sequencia_usuario_filtrada), sep=',')
```

## 🧠 Explicação

- A função `formula_xpto` recebe uma sequência de números e aplica a fórmula matemática a cada um.
- O uso de `*d` permite passar os números como argumentos múltiplos.
- `isdigit()` filtra apenas os valores que podem ser convertidos com segurança para `int`.
- O `print` com `*` desempacota a lista, imprimindo os valores separados por vírgula.
- O cálculo usa `math.sqrt` e `round` para gerar a saída com números inteiros arredondados.

## ✅ Exemplo de saída

```python
digite uma sequência de números inteiros separados por vírgula: 
100,150,250.5,350b,450b550*650,,0,   ,-10,180
18,22,0,24
```

> ℹ️ Essa versão é mais modular e legível, ideal para reutilização da lógica em outros contextos. A filtragem garante que apenas números válidos sejam processados.
