# Exercício 01: O Analisador de Log Robusto

## 🛡️ Módulo 1.1: Análise de Logs (Blue Team)

- [Voltar ao Sumário](../SUMARIO.md)

### 🎯 O Cenário

Você está monitorando os logs de acesso de um servidor web. Sua tarefa é escrever um script Python que receba **uma única linha de log** em formato padrão (Common Log Format) e extraia de forma **robusta** três informações vitais:

1. O **Endereço IP** de origem.  
2. A **Data e Hora** do acesso.  
3. O **Recurso Solicitado** (a página ou arquivo).  

Você deve usar **Expressões Regulares (Regex)** para garantir que a extração funcione corretamente, mesmo que o formato do log tenha variações sutis.

---

### 📋 Dados de Entrada

A linha de log a ser analisada é:

```python
log_line = '89.160.19.111 - - [10/Nov/2025:13:55:36 +0000] "GET /admin/login.php HTTP/1.1" 200 4521'
```

### ✅ Requisitos de Saída

Seu script deve imprimir as informações extraídas de forma clara:

```
IP: 89.160.19.111
Data/Hora: 10/Nov/2025:13:55:36 +0000
Recurso: /admin/login.php
```

---

### 💡 Conceitos-Chave (Dicas)

Para resolver este desafio, você precisará usar:

- **Módulo `re`:** A biblioteca padrão do Python para Expressões Regulares.  
- **`re.search()`:** Função para encontrar a primeira ocorrência de um padrão em uma string.  
- **Grupos Nomeados:** Usar `(?P<nome>...)` para dar um nome a um grupo, facilitando a extração com `match.group("nome")`.  
- **Metacaracteres Regex:**  
  - `\d` → dígito  
  - `\.` → ponto literal  
  - `\s` → espaço  
  - `\S+` → um ou mais não-espaços  
  - `[^\]]+` → um ou mais caracteres que *não* sejam `]`  

---

### 🐍 Solução Proposta

<details>
<summary>Clique para ver a solução</summary>

```python
import re

# Linha de log fornecida
log_line = '89.160.19.111 - - [10/Nov/2025:13:55:36 +0000] "GET /admin/login.php HTTP/1.1" 200 4521'

# Expressão regular para capturar IP, Data/Hora e Recurso
pattern = (
    r'^(?P<ip>\d+\.\d+\.\d+\.\d+)\s'
    r'(?P<ident>\S+)\s'
    r'(?P<user>\S+)\s'
    r'\[(?P<data_hora>[^\]]+)\]\s'
    r'"(?P<metodo>[A-Z]+)\s(?P<recurso>\S+)\s(?P<protocolo>[^"]+)"\s'
    r'(?P<status>\d+)\s'
    r'(?P<tamanho>\d+)$'
)

# Aplicando a regex
match = re.search(pattern, log_line)

# Verificando se houve correspondência
if match:
    print(f"IP: {match.group('ip')}")
    print(f"Data/Hora: {match.group('data_hora')}")
    print(f"Recurso: {match.group('recurso')}")
else:
    print("Nenhuma correspondência encontrada. O formato do log pode estar incorreto.")
```

</details>

---

### 🎓 Explicação da Solução

Esta solução usa o poder total do módulo `re` do Python:

1. **`import re`** → Importa a biblioteca de expressões regulares.  
2. **`pattern = (...)`** → Define a regex como uma *raw string* (`r""`) dividida em várias linhas para melhor legibilidade.  
3. **Quebra da Regex:**  
   - `^` → início da string.  
   - `(?P<ip>\d+\.\d+\.\d+\.\d+)` → captura o endereço IP.  
   - `\s` → espaço.  
   - `(?P<ident>\S+)` e `(?P<user>\S+)` → capturam identificador e usuário (quando presentes).  
   - `\[(?P<data_hora>[^\]]+)\]` → captura a data e hora entre colchetes.  
   - `"(?P<metodo>[A-Z]+)\s(?P<recurso>\S+)\s(?P<protocolo>[^"]+)"` → captura método, recurso e protocolo.  
   - `(?P<status>\d+)` → código de status HTTP.  
   - `(?P<tamanho>\d+)` → tamanho da resposta.  
4. **`re.search()`** → procura o padrão na string.  
5. **`if match:`** → garante que houve correspondência antes de acessar os grupos.  
6. **`match.group('nome')`** → acessa os valores capturados pelos grupos nomeados.  