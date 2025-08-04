# 🐍 Exercício 12 – Números com todos os dígitos pares

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Encontre todos os números entre **1000 e 3000** (inclusive)  
- Verifique se **todos os dígitos** de cada número são **pares**  
- Imprima os números válidos em uma **única linha**, separados por vírgula

> Exemplo:  
Saída → `2000,2002,2004,...`

> 💡 *Dica:* Use `str(n)` para iterar sobre os dígitos e `int(e) % 2 == 0` para verificar se são pares.

## 💻 Solução

### ✅ Forma 1 – Usando `for` com `continue`

```python
sequencia = []

for n in range(1000, 3001):
    if any(int(e) % 2 != 0 for e in str(n)):
        continue
    else:
        sequencia.append(n)

print(*sequencia, sep=',')
```

### ✅ Forma 2 – Usando `filter()` com `any()`

```python
print(*list(filter(lambda n: not any(int(e) % 2 != 0 for e in str(n)), range(1000, 3001))), sep=',')
```

### ✅ Forma 3 – Usando `filter()` com `all()`

```python
print(*list(filter(lambda n: all(int(e) % 2 == 0 for e in str(n)), range(1000, 3001))), sep=',')
```

## 🧠 Explicação

- `range(1000, 3001)` percorre todos os números entre 1000 e 3000, inclusive.
- `str(n)` converte o número em string para iterar sobre os dígitos.
- `int(e) % 2 == 0` verifica se o dígito é par.
- `any(... % 2 != 0)` retorna `True` se houver algum dígito ímpar.
- `all(... % 2 == 0)` retorna `True` apenas se todos os dígitos forem pares.
- `filter(...)` aplica a lógica de validação sobre o intervalo.
- `print(*..., sep=',')` imprime os números válidos em uma única linha, separados por vírgula.

## ✅ Exemplo de saída

```python
2000,2002,2004,2006,2008,2020,2022,2024,...
```

> ℹ️ Esse exercício é ótimo para praticar lógica condicional, iteração sobre strings e uso de funções como `any()`, `all()` e `filter()`.

- [Desafio anterior → Desafio 11](./desafio_11.md)  
- [Próximo desafio → Desafio 13](./desafio_13.md)
