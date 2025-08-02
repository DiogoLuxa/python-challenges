# 🐍 Exercício 04 – Lista e tupla a partir de números separados por vírgula

- [Voltar ao Sumário](./SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que aceite uma **sequência de números inteiros separados por vírgula**, fornecida pelo usuário.  
O programa deve gerar e imprimir:

- Uma **lista** contendo os números.
- Uma **tupla** contendo os mesmos valores.

> Exemplo:  
Entrada → `34,67,55,33,12,98`  
Saída →  
```python
[34, 67, 55, 33, 12, 98]  
(34, 67, 55, 33, 12, 98)
```

> 💡 *Dica:* Você pode usar `split(',')` ou expressões regulares para tratar a entrada e extrair os números.

## 💻 Solução

```python
import re

usuario = input('digite uma sequência de números separados por vírgula: ')
sequencia = [int(n) for n in re.findall(r'\b\d+\b', usuario)]
print(sequencia, tuple(sequencia), sep='\n')
```

## 🧠 Explicação

- `input()` captura a sequência digitada pelo usuário.
- `re.findall(r'\b\d+\b', usuario)` busca todos os números inteiros presentes na entrada.
- `[int(n) for n in ...]` converte cada número encontrado em `int` e gera uma lista.
- `tuple(sequencia)` transforma a lista em tupla.
- `print(..., ..., sep='\n')` imprime lista e tupla, cada uma em uma linha.

## ✅ Exemplo de saída

```python
digite uma sequência de números separados por vírgula: 34,67,55,33,12,98
[34, 67, 55, 33, 12, 98]
(34, 67, 55, 33, 12, 98)
```

> ℹ️ Essa abordagem com `re.findall` garante que apenas os números sejam capturados, ignorando espaços ou possíveis caracteres inválidos na entrada.

- [Desafio anterior → Desafio 03](./desafio_03.md)  
- [Próximo desafio → Desafio 05](./desafio_05.md)