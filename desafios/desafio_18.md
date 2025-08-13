# 🐍 Exercício 18 – Validação de senhas com múltiplos critérios

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **lista de senhas separadas por vírgula**  
- Verifique se cada senha atende aos seguintes critérios:
  - Pelo menos **1 letra minúscula** `[a-z]`
  - Pelo menos **1 letra maiúscula** `[A-Z]`
  - Pelo menos **1 número** `[0-9]`
  - Pelo menos **1 caractere especial** entre `$#@`
  - Comprimento entre **6 e 12 caracteres**

- Imprima apenas as senhas válidas, separadas por vírgula

> Exemplo:  
Entrada → `ABd1234@1,a F1#,2w3E*,2We3345`  
Saída → `ABd1234@1`

> 💡 *Dica:* Use expressões regulares com `re.fullmatch()` para validar cada senha.

## 💻 Solução

```python
import re

mensagem = """Insira uma lista de senhas, separadas por vírgulas.
A SENHA DEVE CONTER AO MENOS:
- 1 caractere minúsculo
- 1 maiúsculo
- 1 dígito de 0-9
- 1 caractere especial $#@
- Ter entre 6 e 12 caracteres
(ex: Senha123@,abcDEF1#,Xx12$aa)
"""

regex = r'^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[$#@])[a-zA-Z\d$#@]{6,12}$'

while True:
    entrada = input(mensagem).split(',')
    senhas = [senha.strip() for senha in entrada]
    senhas_validas = [*filter(lambda senha: re.fullmatch(regex, senha), senhas)]
    
    if senhas_validas:
        print(f'\nSenha válidas: {",".join(senhas_validas)}')
        break
    else:
        print('Nenhuma senha válida. Tente novamente!\n')
```

## 🧠 Explicação

- A variável `regex` define os critérios de validação usando lookaheads.
- `re.fullmatch(...)` garante que a senha inteira obedeça à regra.
- O loop permite que o usuário tente novamente até que ao menos uma senha válida seja encontrada.
- `filter(...)` aplica a verificação a cada senha da lista.
- `",".join(...)` imprime as senhas válidas separadas por vírgula.

## ✅ Exemplo de saída

```python
Insira uma lista de senhas, separadas por vírgulas.
A SENHA DEVE CONTER AO MENOS:
- 1 caractere minúsculo
- 1 maiúsculo
- 1 dígito de 0-9
- 1 caractere especial $#@
- Ter entre 6 e 12 caracteres
(ex: Senha123@,abcDEF1#,Xx12$aa)
ABd1234@1,a F1#,2w3E*,2We3345

Senha válidas: ABd1234@1
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1r7iSdjO4OPO8BtV0D2usE65zxa-DLP8r?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar expressões regulares, validação de entrada e lógica de segurança em Python.

- [Desafio anterior → Desafio 17](./desafio_17.md)  
- [Próximo desafio → Desafio 19](./desafio_19.md)