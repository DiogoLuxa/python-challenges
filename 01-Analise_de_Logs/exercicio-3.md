# Exercício 03: O Analisador de Arquivo

## 🛡️ Módulo 1.1: Análise de Logs (Blue Team)

- [Voltar ao Sumário](../SUMARIO.md)

### 🎯 O Cenário

Seus scripts anteriores funcionavam, mas tinham limitações do mundo real:

1. Os logs estavam "chumbados" (hardcoded) dentro do script. Precisamos ler de um **arquivo real**.  
2. O script era linear. Se quisermos reutilizar a lógica de *parsing*, teremos que copiar e colar.  
3. O script era frágil. Logs reais contêm linhas em branco, comentários ou lixo. Um script que assume que *toda* linha bate com a Regex quebraria.

Sua tarefa é criar um script robusto que:

- Abra e leia um arquivo `access.log` real.  
- Encapsule a lógica de *parsing* (Regex) dentro de uma **Função**.  
- Lide com linhas malformadas sem quebrar.  
- Filtre e imprima **apenas** os alertas de status `403` (Forbidden).

---

### 📋 Dados de Entrada

Crie um arquivo chamado `access.log` no mesmo diretório do seu script e cole o seguinte conteúdo (as linhas "lixo" são propositais para testar a robustez):

```text
192.168.1.5 - - [11/Nov/2025:10:01:15 +0000] "GET /home HTTP/1.1" 200 1234
# Log de manutenção iniciado
89.160.19.111 - - [11/Nov/2025:10:03:00 +0000] "GET /admin/config.php HTTP/1.1" 403 500
172.16.0.10 - - [11/Nov/2025:10:04:45 +0000] "GET /img/logo.png HTTP/1.1" 200 7890

LINHA_MAL_FORMADA_ISTO_VAI_QUEBRAR_O_REGEX

10.0.0.5 - - [11/Nov/2025:10:05:15 +0000] "POST /login.php HTTP/1.1" 403 500
```

---

### ✅ Requisitos de Saída

O script deve processar o arquivo `access.log` e imprimir um relatório limpo apenas com os alertas `403`.

🔍 **Saída esperada:**

```text
[ALERTA 403] IP: 89.160.19.111 | Recurso: /admin/config.php
[ALERTA 403] IP: 10.0.0.5 | Recurso: /login.php
Análise do arquivo 'access.log' concluída.
Total de alertas 403: 2
```

---

### 💡 Conceitos-Chave

- **Leitura de Arquivos:** `with open(arquivo, 'r') as f:`  
- **Funções:** `def nome_da_funcao(parametro):`  
- **Otimização de Regex:** `re.compile()`  
- **Dicionários:** Retornar dados estruturados (ex: `{'ip': '...'}`)  
- **Lógica Robusta:** Usar `if match:` para pular linhas que não correspondem.

---

### 🐍 Solução Proposta

<details>
<summary>Clique para ver a solução</summary>

```python
import re

# 1. Padrão Regex compilado para otimização
pattern = re.compile(
    r'^(?P<ip>\d+\.\d+\.\d+\.\d+)\s'
    r'(?P<ident>\S+)\s'
    r'(?P<user>\S+)\s'
    r'\[(?P<data_hora>[^\]]+)\]\s'
    r'"(?P<metodo>[A-Z]+)\s(?P<recurso>\S+)\s(?P<protocolo>[^"]+)"\s'
    r'(?P<status>\d+)\s'
    r'(?P<tamanho>\d+)$'
)

def parse_log_line(linha):
    """
    Recebe uma linha de log, aplica a Regex.
    Retorna um dicionário com 'ip' e 'recurso' se for um alerta 403.
    Retorna None caso contrário.
    """
    match = pattern.search(linha)

    # 2. Condição de filtro
    if match and match.group('status') == '403':
        # 3. Retorna dados estruturados (Dicionário)
        return {'ip': match.group('ip'), 'recurso': match.group('recurso')}
    
    # Retorna None para qualquer linha que não seja um alerta 403
    return None

# --- Bloco Principal ---

arquivo = './access.log'
alertas = 0

print(f"Iniciando análise do arquivo '{arquivo}'...")

try:
    # 4. Leitura de arquivo com 'with open'
    with open(arquivo, 'r', encoding='utf-8') as logs:
        for linha in logs:
            # 5. Chama a função de parsing
            log_data = parse_log_line(linha)
            
            # 6. Lógica robusta: só age se a função retornar dados
            if log_data:
                alertas += 1
                print(f'[ALERTA 403] IP: {log_data["ip"]} | Recurso: {log_data["recurso"]}')

    print(f'\nAnálise do arquivo "{arquivo}" concluída.')
    print(f'Total de alertas 403: {alertas}')

except FileNotFoundError:
    print(f"ERRO: O arquivo '{arquivo}' não foi encontrado.")
except Exception as e:
    print(f"Ocorreu um erro inesperado: {e}")
```

</details>

---

### 🎓 Explicação da Solução

1. **`re.compile(pattern)`**: A Regex é compilada uma única vez, fora do loop, para otimizar performance.  
2. **Função `parse_log_line`**: Isola a lógica de parsing e torna o loop principal mais limpo.  
3. **Dicionários**: Retorna dados estruturados com `{'ip': ..., 'recurso': ...}`.  
4. **`with open(...)`**: Garante fechamento automático do arquivo, mesmo em caso de erro.  
5. **Robustez (`if log_data:`)**: Ignora linhas inválidas e só processa as que retornam dados válidos.  
6. **`try...except`**: Evita falhas caso o arquivo não exista e exibe mensagens amigáveis.