# 🐍 Exercício 10 – Remoção de duplicatas e ordenação alfanumérica de palavras

- [Voltar ao Sumário](./SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **sequência de palavras separadas por espaço** como entrada.
- Remova todas as **palavras duplicadas**.
- Ordene as palavras restantes em **ordem alfanumérica**.
- Imprima o resultado em uma **única linha**, com as palavras separadas por espaço.

> Exemplo:  
Entrada → `hello world and practice makes perfect and hello world again`  
Saída → `again and hello makes perfect practice world`

> 💡 *Dica:* Use `set()` para eliminar duplicatas e `sorted()` para ordenar. Expressões regulares podem ajudar a validar a entrada.

## 💻 Solução

```python
import re

while True:
    try:
        texto = re.findall(r"\b[a-zA-ZÀ-ÿ]+\b", input('Digite apenas palavras separadas por espaço: '))
        if not texto:
            raise ValueError
        break
    except ValueError:
        print('Valor inválido. Tente novamente.')

print(*sorted(set(texto)))
```

## 🧠 Explicação

- `input()` recebe a sequência de palavras digitadas pelo usuário.
- `re.findall(r"\b[a-zA-ZÀ-ÿ]+\b", ...)` extrai apenas palavras válidas, incluindo acentuadas.
- `set(texto)` remove duplicatas automaticamente.
- `sorted(...)` ordena as palavras em ordem alfabética.
- `print(*...)` imprime as palavras separadas por espaço, usando desempacotamento.

## ✅ Exemplo de saída

```python
Digite apenas palavras separadas por espaço:  
hello world and practice makes perfect and hello world again
again and hello makes perfect practice world
```

> ℹ️ Esse exercício é excelente para praticar manipulação de texto, uso de conjuntos e ordenação — tudo com validação robusta.

- [Desafio anterior → Desafio 09](./desafio_09.md)  
- [Próximo desafio → Desafio 11](./desafio_11.md)