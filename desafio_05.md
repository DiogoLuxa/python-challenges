# 🐍 Exercício 05 – Classe com encapsulamento e exibição de string em maiúsculo

- [Voltar ao Sumário](./SUMARIO.md)  

## 🧩 Enunciado

Implemente uma classe que:

- Tenha um método para **receber uma palavra** do usuário.
- Outro método para **imprimir essa palavra em letras maiúsculas**.

A classe deve armazenar a palavra como um **atributo de instância**.  
Inclua um **teste simples** ao final para verificar o funcionamento.

> Exemplo:  
Entrada → `python`  
Saída → `PYTHON`

> 💡 *Dica:* Use o método `__init__` para inicializar o atributo.

## 💻 Solução

```python
class PalavraEmCaixaAlta:
    def __init__(self):
        self.palavra = ''
        
    def receber_palavra(self):
        while True:
            palavra = input('Digite uma única palavra - sem números ou espaços: ').strip()
            if not palavra:
                print('Campo vazio! Tente novamente.')
            elif not palavra.isalpha():
                print('Digite apenas letras, sem espaço, números ou caracteres especiais!')
            else:
                self.palavra = palavra
                break
        
    def imprimir_palavra(self):
        print(self.palavra.upper())

# 🧪 Teste da classe
instancia_teste = PalavraEmCaixaAlta()
instancia_teste.receber_palavra()
instancia_teste.imprimir_palavra()
```

## 🧠 Explicação

- `__init__` inicializa o atributo `self.palavra` como string vazia.
- `receber_palavra()` solicita a entrada do usuário, valida e atribui à instância.
- `imprimir_palavra()` acessa o atributo armazenado e o imprime em letras maiúsculas usando `.upper()`.
- O bloco de teste final instância a classe e executa os dois métodos em sequência.

## ✅ Exemplo de saída

```python
Digite uma única palavra - sem números ou espaços: python
PYTHON
```

> ℹ️ Essa versão aprimorada segue os princípios de encapsulamento e reutilização de estado interno da instância.

- [Desafio anterior → Desafio 04](./desafio_04.md)  
- [Próximo desafio → Desafio 06](./desafio_06.md)