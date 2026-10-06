# Exemplos de uso

Este documento mostra exemplos de mensagens que o usuário poderia enviar ao bot no Telegram e o comportamento esperado do agente.

## Registrar entrada no estoque

Mensagem do usuário:

```text
Guardar 10 controles no estoque
```

Comportamento esperado:

- Identificar o produto: `controles`
- Identificar a operação: `entrada`
- Identificar a quantidade: `10`
- Registrar a movimentação na planilha
- Responder com uma confirmação no Telegram

Resposta esperada:

```text
Entrada registrada: 10 controles adicionados ao estoque.
```

## Registrar saída do estoque

Mensagem do usuário:

```text
Retirar 5 controles do estoque
```

Comportamento esperado:

- Identificar o produto: `controles`
- Identificar a operação: `saída`
- Identificar a quantidade: `5`
- Registrar a movimentação na planilha
- Responder com uma confirmação no Telegram

Resposta esperada:

```text
Saída registrada: 5 controles removidos do estoque.
```

## Consultar estoque

Mensagem do usuário:

```text
Quantidade de controles no estoque?
```

Comportamento esperado:

- Identificar o produto consultado
- Ler as movimentações na planilha
- Calcular entradas menos saídas
- Retornar o saldo atual

Resposta esperada:

```text
Atualmente existem 5 controles no estoque.
```

## Possíveis variações de mensagens

O uso da IA permite aceitar frases menos rígidas, como:

```text
Adiciona 3 controles
Coloca mais 8 controles no estoque
Saiu 2 controles
Tira 1 controle do estoque
Quantos controles ainda tem?
```

## Melhorias futuras para os exemplos

- Validar mensagens sem quantidade informada.
- Responder quando o produto não existir na planilha.
- Impedir retirada maior que o estoque disponível.
- Aceitar mais de um produto no mesmo fluxo.
