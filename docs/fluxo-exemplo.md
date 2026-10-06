# Fluxo-exemplo reconstruído

O arquivo original exportado do n8n não está disponível porque o workspace usado no projeto expirou. Este documento registra uma reconstrução em alto nível do fluxo, com base na demonstração e na arquitetura do projeto.

## Sequência dos nós

```text
1. Telegram Trigger
2. Set / organização dos campos da mensagem
3. Gemini API
4. Code node em JavaScript
5. If / decisão do tipo de operação
6. Google Sheets: append ou read
7. Telegram: enviar resposta
```

## 1. Telegram Trigger

Recebe a mensagem enviada pelo usuário ao bot.

Dados importantes:

- `chat_id`
- texto da mensagem
- nome ou identificador do usuário
- data/hora da mensagem

## 2. Organização dos campos

Prepara os dados para enviar à IA, mantendo principalmente a mensagem original do usuário.

Exemplo de entrada:

```json
{
  "mensagem": "Guardar 10 controles no estoque"
}
```

## 3. Gemini API

Interpreta a intenção da mensagem e retorna uma estrutura parecida com:

```json
{
  "operacao": "entrada",
  "produto": "controles",
  "quantidade": 10
}
```

Para consulta, poderia retornar:

```json
{
  "operacao": "consulta",
  "produto": "controles"
}
```

## 4. Tratamento em JavaScript

Organiza a resposta da IA para que o fluxo consiga decidir o próximo passo.

Pseudocódigo:

```javascript
const dados = respostaDaIA;

return {
  operacao: dados.operacao,
  produto: dados.produto,
  quantidade: dados.quantidade || 0,
  mensagemOriginal: mensagemUsuario
};
```

## 5. Decisão do fluxo

O nó condicional separa os caminhos:

- Se `operacao` for `consulta`, o fluxo lê a planilha e calcula o saldo.
- Se `operacao` for `entrada` ou `saida`, o fluxo registra uma nova linha na planilha.

## 6. Google Planilhas

Para registro, adiciona uma linha com os dados da movimentação.

Para consulta, lê as movimentações e calcula o estoque atual.

## 7. Resposta no Telegram

Envia uma mensagem final ao usuário.

Exemplos:

```text
Entrada registrada: 10 controles adicionados ao estoque.
```

```text
Atualmente existem 5 controles no estoque.
```

## Observação

Este documento não substitui o fluxo original exportado do n8n, mas ajuda a explicar a lógica do projeto para estudo, revisão e reconstrução futura.
