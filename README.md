# Agente de Controle de Estoque com IA

Protótipo de um agente de IA para controle de estoque, com interação por mensagens no Telegram. O usuário escreve em linguagem natural, como "Guardar 10 controles no estoque" ou "Quantidade de controles no estoque?", e o fluxo registra a movimentação ou consulta o estoque atual em uma planilha.

Projeto individual, desenvolvido em junho de 2026 com **n8n**, **Gemini API** e **Google Planilhas**.

## Demonstração

![Conversa com o bot no Telegram](imagens/conversa-telegram.png)

<!-- Quando os vídeos estiverem no YouTube (não listado), descomente e troque os links:
- [Vídeo 1: conversa com o bot no Telegram](LINK_DO_VIDEO_1)
- [Vídeo 2: execução do fluxo no n8n](LINK_DO_VIDEO_2)
-->

## O que ele faz

- **Registra entradas:** "Guardar 10 controles no estoque"
- **Registra saídas:** "Retirar 5 controles do estoque"
- **Consulta o estoque:** "Quantidade de controles no estoque?"

Na demonstração, o estoque começa em 10 unidades e, depois da retirada de 5, a consulta retorna 5 unidades.

## Como funciona

1. A mensagem enviada ao bot chega ao fluxo pelo **gatilho do Telegram**.
2. Os campos da mensagem são organizados e enviados à **Gemini API**, que interpreta o texto.
3. Um **código em JavaScript** trata a resposta do modelo, e um nó **"Se"** decide o caminho:
   - **Consulta:** lê as linhas da planilha, calcula o estoque atual e responde no Telegram.
   - **Registro:** adiciona uma linha na planilha com a movimentação e responde com a confirmação.
4. O bot envia a resposta ao usuário no Telegram.

![Fluxo no n8n](imagens/fluxo-n8n.png)

## Tecnologias

n8n · Gemini API · Telegram Bot · Google Planilhas · JavaScript · JSON

## Status e limitações

- **Protótipo:** o fluxo rodava em modo de teste. Era preciso iniciar a execução no n8n a cada mensagem enviada ao bot; depois disso, todo o processamento era automático.
- **Arquivo do fluxo indisponível:** o workspace do n8n Cloud usado no projeto expirou, então o fluxo exportado não está neste repositório. A documentação reúne prints e vídeos da execução.

## Próximos passos

- Publicar o fluxo para o bot responder continuamente, sem iniciar a execução manualmente.
- Controlar mais de um produto no mesmo estoque.
- Enviar alerta quando o estoque estiver baixo.

## Autor

Rafael Taborda Lopes · [LinkedIn](https://www.linkedin.com/in/rafael-lopes0) · [GitHub](https://github.com/rafaeltlsz)
