# Limitações do protótipo

Este projeto foi desenvolvido como um protótipo funcional. Ele demonstra a ideia principal, mas ainda não possui todos os recursos necessários para uso contínuo em produção.

## Fluxo original indisponível

O fluxo foi criado em um workspace do n8n Cloud que expirou. Por isso, o arquivo exportado em JSON não está disponível neste repositório.

Para compensar isso, o repositório inclui:

- prints da conversa no Telegram;
- print do fluxo no n8n;
- documentação da arquitetura;
- exemplos de uso;
- uma reconstrução em alto nível do fluxo.

## Execução em modo de teste

Durante a demonstração, o fluxo rodava em modo de teste. Isso significa que era necessário iniciar a execução manualmente no n8n antes de enviar uma mensagem ao bot.

Em uma versão final, o fluxo deveria ficar publicado para responder continuamente.

## Controle de produtos limitado

A demonstração foi feita com um produto principal. Uma melhoria importante seria permitir múltiplos produtos de forma mais robusta.

## Validações pendentes

O protótipo ainda pode evoluir com validações como:

- impedir retirada maior que o estoque disponível;
- tratar mensagens incompletas;
- confirmar o produto antes de registrar movimentações ambíguas;
- padronizar nomes de produtos parecidos;
- responder quando a planilha estiver indisponível.

## Persistência dos dados

O Google Planilhas foi usado como uma base simples e visual. Para um sistema maior, seria melhor usar um banco de dados, como SQLite, PostgreSQL ou outro serviço dedicado.

## Segurança

Em uma versão publicada, seria importante proteger tokens e chaves de API, limitar quem pode usar o bot e evitar expor dados sensíveis do estoque.
