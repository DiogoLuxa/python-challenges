# 🐍 Exercício 17 – Registro de transações bancárias com saldo final

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Receba uma **sequência de transações bancárias** via entrada do usuário  
- Cada transação deve seguir o formato:
  - `D valor` → depósito
  - `W valor` → saque
- Calcule o **saldo final** da conta após todas as operações

> Exemplo:  
Entrada →  
```
D 300  
D 300  
W 200  
D 100
```  
Saída → `500`

> 💡 *Dica:* Use uma estrutura de classe para organizar as operações de depósito, saque e consulta de saldo.  
Valide os comandos com expressões regulares e permita interação contínua até que o usuário finalize.

## 💻 Solução

```python
import re

class ContaBancaria:
    """
    Representa uma conta bancária simples com operações de depósito, saque e consulta de saldo.
    
    Atributos:
        saldo (float): O saldo atual da conta.
    
    Métodos:
        consultar(): Exibe o saldo atual.
        depositar(valor): Adiciona valor ao saldo, se for positivo.
        sacar(valor): Subtrai valor do saldo, se houver saldo suficiente.
    """
    def __init__(self):
        self.saldo = 0
        
    def consultar(self):
        print(f'Seu saldo é de R$ {self.saldo:.2f}')
    
    def depositar(self, valor):
        if valor <= 0:
            print('Valor inválido para depósito!')
        else:
            self.saldo += valor
            print(f'Depositado R$ {valor:.2f} com sucesso!')
    
    def sacar(self, valor):
        if valor <= 0:
            print('Valor inválido para saque!')
        elif valor > self.saldo:
            print('Saldo insuficiente.')
        else:
            self.saldo -= valor
            print(f'Saque de R$ {valor:.2f} realizado com sucesso!')

minha_conta = ContaBancaria()

while True:
    entrada = input('OPÇÕES\n[d] depositar\n[s] sacar\n[c] consultar saldo\n[f] finalizar\nDigite o comando (ex: d 50.00): ').lower().strip()
    
    entrada = entrada.replace(',', '.')

    if re.match(r'^(d|s)\s\d+(\.\d{1,2})?$|^f$|^c$', entrada):
        
        partes = entrada.split()
        
        if len(partes) == 2:
            acao, valor = partes
            valor = float(valor)
            if acao == 'd':
                minha_conta.depositar(valor)
            elif acao == 's':
                minha_conta.sacar(valor)
        else:
            acao = partes[0]
            if acao == 'c':
                minha_conta.consultar()
            elif acao == 'f':
                print('Encerrando operação...')
                break
    else:
        print('Comando inválido! Tente novamente.')
```

## 🧠 Explicação

- A classe `ContaBancaria` encapsula o saldo e as operações bancárias.
- `depositar()` e `sacar()` validam os valores e atualizam o saldo.
- `consultar()` exibe o saldo atual com formatação monetária.
- O loop principal permite múltiplas interações com o usuário.
- `re.match(...)` valida comandos como `d 100`, `s 50`, `c`, `f`.
- O programa aceita valores com ponto ou vírgula e trata entradas inválidas com mensagens claras.

## ✅ Exemplo de saída

```python
OPÇÕES
[d] depositar
[s] sacar
[c] consultar saldo
[f] finalizar
Digite o comando (ex: d 50.00): d 300
Depositado R$ 300.00 com sucesso!
Digite o comando (ex: d 50.00): d 300
Depositado R$ 300.00 com sucesso!
Digite o comando (ex: d 50.00): s 200
Saque de R$ 200.00 realizado com sucesso!
Digite o comando (ex: d 50.00): d 100
Depositado R$ 100.00 com sucesso!
Digite o comando (ex: d 50.00): c
Seu saldo é de R$ 500.00
Digite o comando (ex: d 50.00): f
Encerrando operação...
```
## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1YfrWQUmsnHq99RRZsBwoEtNeFwwybyf6?usp=sharing)

> ℹ️ Esse exercício é excelente para praticar orientação a objetos, validação de entrada e lógica de fluxo interativo em Python.

- [Desafio anterior → Desafio 16](./desafio_16.md)  
- [Próximo desafio → Desafio 18](./desafio_18.md)