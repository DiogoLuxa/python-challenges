# 🐍 Exercício 25 – Classe com parâmetro de classe e instância

- [Voltar ao Sumário](../SUMARIO.md)  

## 🧩 Enunciado

Escreva um programa que:

- Defina uma **classe com um parâmetro de classe** (compartilhado por todas as instâncias)  
- Permita que esse mesmo parâmetro seja **sobrescrito por instâncias específicas**  
- Crie alguns objetos da classe e exiba os valores para verificar o comportamento

> 💡 *Dica:* Parâmetros de classe são definidos diretamente dentro da classe.  
Você pode sobrescrevê-los dentro do `__init__()` usando `self`.

## 💻 Solução

```python
class Humanoide:
    raca = 'Robô'

    def __init__(self, nome, id, raca=None):
        self.nome = nome.capitalize()
        self.id = id
        if raca:
            self.raca = raca.capitalize()

r1 = Humanoide('RX-42', 102)
r2 = Humanoide('Zeta', 300)
r3 = Humanoide('A-7', 1, 'ciborgue')
```

## 🧠 Explicação

- `raca = 'Robô'` é um **parâmetro de classe**, acessível por todas as instâncias.
- No `__init__()`, se o usuário fornecer uma nova raça, ela será atribuída como **parâmetro de instância**.
- `self.raca` sobrescreve o valor padrão da classe apenas para aquela instância.
- `capitalize()` é usado para deixar o nome e a raça com a primeira letra maiúscula.

## ✅ Exemplo de uso

```python
print(r1.raca)  # Robô
print(r2.raca)  # Robô
print(r3.raca)  # Ciborgue
```

## ▶️ Teste no Google Colab

Quer testar o código diretamente no navegador?

👉 [Abrir no Google Colab](https://colab.research.google.com/drive/1UVD6rN83eSTL9m_rWjhwT2G1A_PSo9_3?usp=sharing)

> ℹ️ Esse exercício é excelente para entender a diferença entre atributos de classe e atributos de instância em Python.

- [Desafio anterior → Desafio 24](./desafio_24.md)  
- [Próximo desafio → Desafio 26](./desafio_26.md)