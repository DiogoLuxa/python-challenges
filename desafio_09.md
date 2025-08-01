# 🐍 Exercício 09 – Capitalização de todas as linhas de um texto

## 🧩 Enunciado

Escreva um programa que:

- Aceite uma **sequência de linhas** como entrada.
- Converta **todas as letras** de cada linha para **maiúsculas**.
- Imprima o resultado, **preservando as quebras de linha** originais.

```
Exemplo:

Entrada →  
Hello world  
Practice makes perfect

Saída →  
HELLO WORLD  
PRACTICE MAKES PERFECT
```

## 💻 Solução

```python
texto = '''Hello world
Practice makes perfect'''

def texto_maiusculo(texto):
    """
    Converte todas as linhas de um texto para letras maiúsculas.

    Parâmetros:
        texto (str): Texto de entrada contendo uma ou mais linhas.

    Retorna:
        str: Texto com todas as linhas convertidas para letras maiúsculas,
             preservando as quebras de linha originais.
    """
    return "\n".join(map(lambda l: l.upper(), texto.splitlines()))

print(texto_maiusculo(texto))
```

## 🧠 Explicação

- `texto` é uma string multilinha.
- `.splitlines()` divide o texto em uma lista de linhas.
- `map(lambda l: l.upper(), ...)` aplica a capitalização em cada linha.
- `"\n".join(...)` reconstrói o texto com as quebras de linha originais.
- A função `texto_maiusculo` encapsula toda a lógica e pode ser reutilizada facilmente.

## ✅ Exemplo de saída

```python
HELLO WORLD
PRACTICE MAKES PERFECT
```

> ℹ️ Esse exercício é útil para manipulação de textos multilinha e demonstra como aplicar transformações linha a linha com elegância funcional.
