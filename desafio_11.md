# 🐍 Exercício 11 – Filtragem de binários divisíveis por 5

- [Voltar ao Sumário](./SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **sequência de números binários de 4 dígitos**, separados por vírgula.  
- Verifique quais desses números são **divisíveis por 5**.  
- Imprima os números válidos em uma **única linha**, separados por vírgula.

> Exemplo:  
Entrada → `0100,0011,1010,1001`  
Saída → `1010`

> 💡 *Dica:* Use `int(n, 2)` para converter binário para decimal e `% 5 == 0` para verificar divisibilidade.

## 💻 Solução

```python
import re

while True:
    try:
        valores = re.findall(r"(?:^|,)([01]{4})(?=,|$)", input('Digite uma sequência de números inteiros – sendo de 4 dígitos – separados por vírgula: '))
        if not valores:
            raise ValueError
        break
    except ValueError:
        print('Valor inválido. Tente novamente.')

print(*[n for n in valores if int(n, 2) % 5 == 0], sep=',')
```

## 🧠 Explicação

- `input()` recebe a sequência digitada pelo usuário.  
- `re.findall(r"(?:^|,)([01]{4})(?=,|$)", ...)` extrai apenas números binários de 4 dígitos.  
- `int(n, 2)` converte cada binário para decimal.  
- `int(n, 2) % 5 == 0` verifica se o número convertido é divisível por 5.  
- A list comprehension filtra os binários válidos.  
- `print(..., sep=',')` imprime os resultados em uma única linha, separados por vírgula.

## ✅ Exemplo de saída

```python
Digite uma sequência de números inteiros – sendo de 4 dígitos – separados por vírgula: 0100,0011,1010,1001
1010
```

> ℹ️ Esse exercício une expressões regulares, conversão binária e filtragem condicional — uma ótima prática para lógica e manipulação de strings.

- [Desafio anterior → Desafio 10](./desafio_10.md)  
- [Próximo desafio → Desafio 12](./desafio_12.md)