# Exercício 02: O Filtro Robusto de 'Acesso Negado' (com Regex)

## 🛡️ Módulo 1.1: Análise de Logs (Blue Team)

- [Voltar ao Sumário](../SUMARIO.md)

### 🎯 O Cenário

Você recebeu um **arquivo de log** maior (simulado por uma lista em Python) e precisa filtrar apenas as linhas que indicam uma tentativa de acesso malsucedida.

O Gerente de SOC (Security Operations Center) quer saber todos os **IPs** que tentaram acessar recursos e receberam um erro **`401 Unauthorized`** (Acesso Não Autorizado).

Sua tarefa é escrever um script Python que:

1. Itere sobre uma **lista** de logs.  
2. Use a **Expressão Regular** do Exercício 1 para validar e "quebrar" cada linha.  
3. Verifique se o grupo `status` da linha corresponde a `401`.  
4. Extraia e imprima **apenas o IP** de cada linha correspondente.  

---

### 📋 Dados de Entrada

```python
log_data = [
    '192.168.1.1 - - [10/Nov/2025:10:01:15 +0000] "GET /home HTTP/1.1" 200 1234',
    '10.0.0.5 - - [10/Nov/2025:10:02:30 +0000] "POST /login HTTP/1.1" 401 500',
    '89.160.19.111 - - [10/Nov/2025:10:03:00 +0000] "GET /admin HTTP/1.1" 401 500',
    '172.16.0.10 - - [10/Nov/2025:10:04:45 +0000] "GET /static/img/logo.png HTTP/1.1" 200 7890',
    '10.0.0.5 - - [10/Nov/2025:10:05:15 +0000] "POST /login HTTP/1.1" 401 500'
]
```

---

### ✅ Requisitos de Saída

O script deve identificar e imprimir os IPs que tiveram acesso negado.  
Saída esperada:

```
IP com Acesso Negado (401): 10.0.0.5
IP com Acesso Negado (401): 89.160.19.111
IP com Acesso Negado (401): 10.0.0.5
```

---

### 💡 Conceitos-Chave

- **Módulo `re`** e **`re.search()`**  
- **Grupos Nomeados** (como `?P<status>`)  
- **Laços de Repetição**: `for` para iterar sobre a lista  
- **Estruturas Condicionais**: `if` com múltiplos testes (`and`)  
- **Comparação de String**: `match.group('status') == '401'`  

---

### 🐍 Solução Proposta

<details>
<summary>Clique para ver a solução</summary>

```python
import re

# 1. Dados de entrada (simulando um arquivo de log)
log_data = [
    '192.168.1.1 - - [10/Nov/2025:10:01:15 +0000] "GET /home HTTP/1.1" 200 1234',
    '10.0.0.5 - - [10/Nov/2025:10:02:30 +0000] "POST /login HTTP/1.1" 401 500',
    '89.160.19.111 - - [10/Nov/2025:10:03:00 +0000] "GET /admin HTTP/1.1" 401 500',
    '172.16.0.10 - - [10/Nov/2025:10:04:45 +0000] "GET /static/img/logo.png HTTP/1.1" 200 7890',
    '10.0.0.5 - - [10/Nov/2025:10:05:15 +0000] "POST /login HTTP/1.1" 401 500'
]

# 2. Padrão robusto do Exercício 1
pattern = (
    r'^(?P<ip>\d+\.\d+\.\d+\.\d+)\s'
    r'(?P<ident>\S+)\s'
    r'(?P<user>\S+)\s'
    r'\[(?P<data_hora>[^\]]+)\]\s'
    r'"(?P<metodo>[A-Z]+)\s(?P<recurso>\S+)\s(?P<protocolo>[^"]+)"\s'
    r'(?P<status>\d+)\s'
    r'(?P<tamanho>\d+)$'
)

print("Iniciando varredura de logs por erros 401...")

# 3. Iterar sobre cada linha na lista de logs
for log in log_data:
    # 4. Aplicar a regex a cada linha
    match = re.search(pattern, log)
    
    # 5. Condição dupla:
    if match and match.group('status') == '401':
        # 6. Se ambos forem verdadeiros, imprimir o IP
        print(f"IP com Acesso Negado (401): {match.group('ip')}")

print("Varredura concluída.")
```

</details>

---

### 🎓 Explicação da Solução

1. **Regex Completa:** valida a linha inteira antes de checar o status.  
2. **Loop `for`:** percorre cada entrada da lista.  
3. **Condição `if match and ...`:**  
   - `if match`: garante que a linha corresponde ao padrão.  
   - `match.group('status') == '401'`: filtra apenas os acessos negados.  
