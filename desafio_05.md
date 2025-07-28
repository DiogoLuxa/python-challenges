# 🐍 Exercício 05 – Classe com métodos para manipulação de string

## 🧩 Enunciado

Defina uma classe com pelo menos dois métodos:

- `getString`: para **receber uma string** do console.
- `printString`: para **imprimir a string em letras maiúsculas**.

Inclua também uma função simples de teste para **executar os métodos** da classe.

> Exemplo:  
Entrada → `python`  
Saída → `PYTHON`

> 💡 *Dica:* Valide que a entrada não contenha números ou caracteres especiais usando o método `.isalpha()`.

## 💻 Solução

```python
class PalavraEmCaixaAlta:
    def receber_palavra(self):
        while True:
            palavra = input('Digite uma única palavra - sem números ou espaços: ').strip()
            if not palavra:
                print('Campo vazio! Tente novamente.')
            elif not palavra.isalpha():
                print('Digite apenas letras, sem espaço, números ou caracteres especiais!')
            else:
                self.imprimir_palavra(palavra.upper())
                break
        
    def imprimir_palavra(self, palavra):
        print(f"Resultado: {palavra}")

# 🧪 Teste simples da classe
instancia_teste = PalavraEmCaixaAlta()
instancia_teste.receber_palavra()
```

## 🧠 Explicação

- A classe `PalavraEmCaixaAlta` encapsula os métodos de entrada e exibição da string.
- `receber_palavra()` utiliza `input()` e valida a entrada:
  - `.strip()` remove espaços extras.
  - `.isalpha()` garante que a palavra contenha apenas letras.
- Se a entrada estiver válida, o método chama `imprimir_palavra()` com a versão maiúscula da string.
- O teste da classe é feito instanciando o objeto e chamando o método de entrada.

## ✅ Exemplo de saída

```python
Digite uma única palavra - sem números ou espaços: python
Resultado: PYTHON
```

> ℹ️ Esse exercício ilustra conceitos de orientação a objetos e boas práticas de validação de entrada em Python.

