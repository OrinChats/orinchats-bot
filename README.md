# OrinChats

Plataforma de automação de conversas e marketing, baseada no projeto open-source ChatbotX.

## Idioma e marca
- Nome da aplicação: OrinChats
- Idioma padrão da interface: Português do Brasil (`pt-BR`)
- O catálogo `apps/builder/messages/pt-BR.json` já existe no projeto; revise as traduções restantes antes de considerar a localização 100% concluída.

## Implantação
Este repositório é um monorepo e não é uma aplicação estática simples. O painel web usa Next.js, mas funcionalidades do sistema dependem de serviços externos, banco de dados, filas/workers e integrações. Publicar somente o painel na Vercel não garante que todo o sistema funcione.

1. Importe o repositório para a Vercel e selecione `apps/builder` como aplicação apenas se a configuração de monorepo estiver ajustada para esse diretório.
2. Configure as variáveis de ambiente exigidas em `.env.example` e pela documentação do projeto.
3. Configure os serviços de banco de dados, cache/filas e workers em provedores compatíveis. Não coloque segredos no código nem no Git.
4. Teste login, persistência, filas, webhooks e cada integração antes de usar em produção.

## Observações
A alteração do idioma padrão não traduz automaticamente mensagens de integrações externas, conteúdo gerado por usuários, nomes técnicos ou chaves que ainda estejam em inglês. Faça uma revisão da interface e execute `pnpm i18n:check` no pacote `apps/builder`.

A licença e os avisos de copyright do projeto original foram mantidos. OrinChats é uma personalização baseada no código-fonte original, não uma alegação de autoria do projeto upstream.
