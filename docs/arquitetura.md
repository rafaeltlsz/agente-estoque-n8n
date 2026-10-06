# Arquitetura do projeto

Este projeto foi construído como um fluxo de automação no n8n, conectando Telegram, Gemini API, JavaScript e Google Planilhas.

## Fluxo principal

```text
Usuário
  ↓
Telegram Bot
  ↓
n8n
  ↓
Gemini API
  ↓
Tratamento em JavaScript
  ↓
Decisão: consulta ou registro
  ↓
Google Planilhas
  ↓
Resposta no Telegram
```

## Componentes

### Telegram Bot

Responsável por receber a mensagem do usuário e enviar a resposta final. Ele funciona como a interface do sistema.

### n8n

Ferramenta central da automação. O n8n conecta os serviços, organiza os dados entre os nós e define o caminho que a mensagem deve seguir.

### Gemini API

Usada para interpretar a mensagem em linguagem natural. A ideia é transformar frases comuns em uma intenção mais estruturada, como entrada, saída ou consulta.

### JavaScript

Usado dentro do fluxo para tratar a resposta da IA, organizar os campos e preparar os dados antes da decisão do fluxo.

### Google Planilhas

Usado como uma base de dados simples para registrar movimentações de estoque e consultar o saldo disponível.

## Tipos de operação

### Registro de entrada

Quando o usuário informa que deseja guardar ou adicionar produtos, o fluxo registra uma nova movimentação positiva na planilha.

Exemplo:

```text
Guardar 10 controles no estoque
```

### Registro de saída

Quando o usuário informa que deseja retirar produtos, o fluxo registra uma nova movimentação negativa na planilha.

Exemplo:

```text
Retirar 5 controles do estoque
```

### Consulta de estoque

Quando o usuário pergunta pela quantidade disponível, o fluxo lê a planilha, calcula o saldo e responde no Telegram.

Exemplo:

```text
Quantidade de controles no estoque?
```

## Modelo de dados sugerido

A planilha pode ser organizada com colunas como:

| Data | Produto | Tipo | Quantidade | Mensagem original |
| --- | --- | --- | --- | --- |
| 2026-06-01 | controle | entrada | 10 | Guardar 10 controles no estoque |
| 2026-06-01 | controle | saída | 5 | Retirar 5 controles do estoque |

Com esse modelo, o saldo pode ser calculado somando entradas e subtraindo saídas.
