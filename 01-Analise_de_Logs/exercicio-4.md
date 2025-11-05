# Exercício 04: O Dicionário de Ameaças

## 🛡️ Módulo 1.1: Análise de Logs (Blue Team)

- [Voltar ao Sumário](../SUMARIO.md)

### 🎯 O Cenário

Seu script do Exercício 3 foi um sucesso. Agora, o time do SOC (Security Operations Center) não quer mais ver *cada* alerta individual. Eles precisam de um **relatório agregado**.

A pergunta deles é: **"Quais são os IPs que mais estão nos atacando e quantas vezes cada um tentou?"**

Sua tarefa é modificar seu script para:

1.  Ler um arquivo de log maior (`access_full.log`) com múltiplos ataques (`403` e `404`) vindos dos mesmos IPs.
2.  Parar de imprimir cada alerta individual.
3.  Contar quantas vezes cada IP atacante apareceu.
4.  Imprimir um sumário final com a contagem de tentativas por IP.

### 📋 Dados de Entrada

Crie um arquivo chamado `access_full.log` no mesmo diretório do seu script e cole este conteúdo:

```text
192.168.1.1 - - [12/Nov/2025:15:01:00 +0000] "GET /index.html HTTP/1.1" 200 5012
# Scanner 1 (IP: 54.12.11.1)
54.12.11.1 - - [12/Nov/2025:15:02:10 +0000] "GET /wp-admin/ HTTP/1.1" 404 231
54.12.11.1 - - [12/Nov/2025:15:02:11 +0000] "GET /wp-login.php HTTP/1.1" 404 231
54.12.11.1 - - [12/Nov/2025:15:02:12 +0000] "GET /admin.php HTTP/1.1" 404 231
192.168.1.3 - - [12/Nov/2025:15:03:00 +0000] "GET /images/logo.png HTTP/1.1" 200 1534
# Scanner 2 (IP: 10.40.5.110)
10.40.5.110 - - [12/Nov/2025:15:04:00 +0000] "GET /config/.env HTTP/1.1" 403 500
10.40.5.110 - - [12/Nov/2025:15:04:01 +0000] "POST /login HTTP/1.1" 403 500
54.12.11.1 - - [12/Nov/2025:15:05:00 +0000] "GET /administrator/ HTTP/1.1" 404 231
# Linha corrompida
{"timestamp": "12/Nov/2025:15:05:10", "error": "buffer_overflow"}
10.40.5.110 - - [12/Nov/2025:15:06:00 +0000] "GET /backup.zip HTTP/1.1" 403 500
```

### ✅ Requisitos de Saída

O script deve ler `access_full.log` e imprimir o relatório agregado de ameaças.

**Saída esperada:**

```
--- Relatório de Ameaças ---
IP: 54.12.11.1 | Tentativas: 4
IP: 10.40.5.110 | Tentativas: 3
--- Fim do Relatório ---
```

*(Note que o total de alertas também deve ser 7)*

### 💡 Conceitos-Chave

  * **Dicionários como Contadores:** Usar um dicionário (`{}`) para armazenar IPs como chaves e suas contagens como valores.
  * **Listas de Interesse:** `if status in ['403', '404']:`
  * **Atualização de Dicionário:** Acessar, verificar e incrementar valores.
  * **Método `.get()`:** `dict.get(chave, valor_padrao)` para evitar erros `KeyError`.
  * **Iteração Final:** Usar `for chave, valor in dict.items():` para imprimir o relatório.

-----

### 🐍 Solução Proposta

Esta é a solução mais eficiente e idiomática em Python, usando um dicionário como um *hash map* para contagem instantânea.

<details>
<summary>Clique para ver a solução</summary>

```python
import re

# 1. Regex melhorada: agora aceita '-' no tamanho do arquivo
pattern = re.compile(
    r'^(?P<ip>\d+\.\d+\.\d+\.\d+)\s'
    r'(?P<ident>\S+)\s'
    r'(?P<user>\S+)\s'
    r'\[(?P<data_hora>[^\]]+)\]\s'
    r'"(?P<metodo>[A-Z]+)\s(?P<recurso>\S+)\s(?P<protocolo>[^"]+)"\s'
    r'(?P<status>\d+)\s'
    r'(?P<tamanho>\d+|-)$'
)

def parse_log_line(linha):
    """
    Recebe uma linha de log, aplica a Regex.
    Retorna o IP se for um alerta 403 ou 404.
    Retorna None caso contrário.
    """
    match = pattern.search(linha)
    
    # 2. Filtro modificado para pegar ambos os status
    if match and match.group('status') in ('403', '404'):
        return match.group('ip')
    
    return None

# --- Bloco Principal ---
arquivo = './access_full.log'
total_alertas = 0
# 3. Dicionário vazio para ser nosso contador
ip_counts = {}

mensagem_load = f"Iniciando análise do arquivo '{arquivo}'..."
print("\n" + "=" * len(mensagem_load))
print(mensagem_load)
print("=" * len(mensagem_load))

try:
    with open(arquivo, 'r', encoding='utf-8') as logs:
        for linha in logs:
            # 4. A função retorna o IP do atacante ou None
            ip_atacante = parse_log_line(linha)
            
            if ip_atacante:
                total_alertas += 1
                
                # 5. A MÁGICA DOS CONTADORES:
                # "Pegue a contagem atual para este IP. Se não existir, comece com 0. Some 1."
                ip_counts[ip_atacante] = ip_counts.get(ip_atacante, 0) + 1

    # 6. Loop final para imprimir o relatório agregado
    print("\n--- Relatório de Ameaças ---")
    for ip, tentativas in ip_counts.items():
        print(f"IP: {ip} | Tentativas: {tentativas}")
    print("--- Fim do Relatório ---")

    print(f'\nAnálise do arquivo "{arquivo}" concluída.')
    print(f'Total de alertas (403/404): {total_alertas}')

except FileNotFoundError:
    print(f"ERRO: O arquivo '{arquivo}' não foi encontrado.")
except Exception as e:
    print(f"Ocorreu um erro inesperado: {e}")

```

</details>

-----

### 🎓 Explicação da Solução

1.  **Regex Robusta**: A Regex foi atualizada no grupo `tamanho` para `(\d+|-)` para aceitar tanto números quanto o caractere `-`, que apareceu nos logs (embora não fosse usado neste exercício, é uma boa prática).
2.  **Função Modificada**: A `parse_log_line` agora retorna *apenas* o IP se a linha for um alerta (`403` ou `404`), e `None` caso contrário. Isso simplifica o loop principal.
3.  **Dicionário Contador (`ip_counts = {}`)**: Esta é a estrutura de dados central. Em Python, dicionários são *hash maps*, o que significa que buscar, adicionar ou atualizar uma chave (nosso IP) é uma operação O(1), ou seja, quase instantânea, não importa quantos IPs já tenhamos.
4.  **`ip_counts.get(ip_atacante, 0)`**: Esta é a forma mais segura de incrementar um contador. `get(chave, padrao)` tenta pegar o valor da `chave`. Se a `chave` (o IP) não existir no dicionário (é a primeira vez que o vemos), ele retorna o valor `padrao` (no caso, `0`), evitando um `KeyError`.
5.  **Lógica de Contagem**: A linha `ip_counts[ip_atacante] = ip_counts.get(ip_atacante, 0) + 1` é a forma mais idiomática em Python de se implementar um contador.
6.  **Loop Final (`.items()`)**: Após o arquivo ser todo lido, o dicionário `ip_counts` está completo. Usamos o método `.items()` para iterar sobre pares de `(chave, valor)` - no nosso caso, `(ip, tentativas)` - e imprimir o relatório final.
