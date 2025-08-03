# 🐍 Exercício 08 – Ordenação alfabética de palavras separadas por vírgula

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **sequência de palavras separadas por vírgula** fornecida pelo usuário.
- Organize as palavras em **ordem alfabética**.
- Imprima o resultado em uma **única linha**, com as palavras separadas por vírgula.

> Exemplo:  
Entrada → `without,hello,bag,world`  
Saída → `bag,hello,without,world`

> 💡 *Dica:* Utilize `split(',')` para separar as palavras e `sorted()` para ordenar. Valide se todas as entradas são compostas apenas por letras com `.isalpha()`.

## 💻 Solução

```python
while True:
    try:
        entrada = input('Digite a lista de palavras que deseja ordenar – separadas por vírgula (ex: carteira,perfume,livro):').split(',')
        if any(not _.isalpha() for _ in entrada):
            raise ValueError
        break
    except ValueError:
        print('Ops! Use apenas palavras e separadas por vírgulas.')

print(",".join(sorted(entrada)))
```

## 🧠 Explicação

- `input(...).split(',')` separa as palavras digitadas usando vírgulas como delimitador.
- `any(... not isalpha())` garante que todas as entradas sejam compostas apenas por letras (sem números ou símbolos).
- `sorted(entrada)` ordena a lista de palavras em ordem alfabética.
- `".".join(...)` une a lista final em uma única `string` com vírgulas entre os elementos.
- A estrutura `while True + try/except` permite validar a entrada e repedir se estiver inválida.

## ✅ Exemplo de saída

```python
Digite a lista de palavras que deseja ordenar – separadas por vírgula (ex: carteira,perfume,livro): 
without,hello,bag,world
bag,hello,without,world
```

> ℹ️ Esse desafio reforça a manipulação de listas, validação de entrada e ordenação — fundamentos sólidos para quem quer dominar Python com estilo.

- [Desafio anterior → Desafio 07](./desafio_07.md)  
- [Próximo desafio → Desafio 09](./desafio_09.md)