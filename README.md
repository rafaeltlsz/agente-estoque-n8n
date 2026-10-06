# Agente de Controle de Estoque com IA

Protótipo de agente de IA para controle de estoque via Telegram, criado com **n8n**, **Gemini API** e **Google Planilhas**.

O usuário envia mensagens em linguagem natural, como `Guardar 10 controles no estoque` ou `Quantidade de controles no estoque?`, e o fluxo interpreta a intenção, registra movimentações ou consulta o saldo atual em uma planilha.

Projeto individual desenvolvido em junho de 2026 para praticar automação, integração entre ferramentas e uso de IA em um fluxo com aplicação prática.

## Visão geral

```text
Telegram -> n8n -> Gemini API -> JavaScript -> Google Planilhas -> Telegram
```

O bot funciona como uma interface simples para controle de estoque. A IA interpreta a mensagem, o n8n organiza o fluxo, uma etapa em JavaScript trata a resposta e o Google Planilhas armazena as movimentações.

## Demonstração

<img width="1440" height="904" alt="Conversa com o bot no Telegram" src="https://github.com/user-attachments/assets/e3bb9cab-d826-4470-adb8-87bc73d89bd6" />

Na demonstração, o estoque começa com 10 unidades. Depois de uma retirada de 5 unidades, a consulta retorna 5 unidades disponíveis.

<img width="1440" height="760" alt="Fluxo no n8n" src="https://github.com/user-attachments/assets/707c3f5c-0d9e-453c-a7d6-307646d80de7" />

## Funcionalidades

- Registrar entrada de produtos no estoque.
- Registrar saída de produtos do estoque.
- Consultar a quantidade atual disponível.
- Interpretar comandos escritos em linguagem natural.
- Responder automaticamente pelo Telegram.
- Usar uma planilha como base de dados simples.

## Exemplos de mensagens

```text
Guardar 10 controles no estoque
Retirar 5 controles do estoque
Quantidade de controles no estoque?
```

Veja mais exemplos em [docs/exemplos-de-uso.md](docs/exemplos-de-uso.md).

## Como funciona

1. O usuário envia uma mensagem para o bot no Telegram.
2. O gatilho do Telegram inicia o fluxo no n8n.
3. A mensagem é enviada para a Gemini API para identificação da intenção.
4. Um trecho em JavaScript organiza a resposta da IA.
5. Um nó condicional decide se a operação é consulta ou registro.
6. O fluxo lê ou atualiza a planilha do Google.
7. O bot responde ao usuário no Telegram.

A explicação completa está em [docs/arquitetura.md](docs/arquitetura.md).

## Tecnologias utilizadas

- n8n
- Gemini API
- Telegram Bot
- Google Planilhas
- JavaScript
- JSON

## Estrutura do repositório

```text
.
├── README.md
└── docs/
    ├── arquitetura.md
    ├── exemplos-de-uso.md
    ├── fluxo-exemplo.md
    └── limitacoes.md
```

## Status do projeto

Este projeto está em estágio de **protótipo funcional documentado**.

O fluxo original foi criado no n8n Cloud, mas o workspace usado no projeto expirou. Por isso, o arquivo exportado do fluxo não está disponível neste repositório. Para manter o projeto compreensível, a documentação reúne prints, explicação da arquitetura e um fluxo-exemplo reconstruído em alto nível.

Mais detalhes em [docs/limitacoes.md](docs/limitacoes.md).

## Próximos passos

- Publicar o fluxo para o bot responder continuamente.
- Controlar múltiplos produtos no mesmo estoque.
- Adicionar alerta de estoque baixo.
- Recriar e exportar o fluxo em JSON.
- Evoluir a planilha para um banco de dados simples.

## Autor

Rafael Taborda Lopes

- [LinkedIn](https://www.linkedin.com/in/rafael-lopes0)
- [GitHub](https://github.com/rafaeltlsz)
