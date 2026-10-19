# Implantação do painel OrinChats na Vercel

Esta configuração é para o **painel web Next.js** em `apps/builder`. Ela não transforma os serviços persistentes (`auth`, `ai`, `realtime`, `javascript-executor`) em funções Vercel automaticamente.

## Importação recomendada

1. Na Vercel, importe `OrinChats/orinchats-bot` como um projeto **individual** para o painel web.
2. Em **Root Directory**, selecione `apps/builder`.
3. Ative **Include source files outside of the Root Directory** (incluir arquivos fora do diretório raiz), porque o painel usa pacotes `workspace:*` localizados em `packages/` e `integrations/`.
4. Framework Preset: `Next.js`.
5. Mantenha os comandos definidos no `apps/builder/vercel.json`. O comando de instalação executa `pnpm install` na raiz do monorepo e o de build executa o pacote `builder` no workspace.
6. Cadastre na Vercel as variáveis de ambiente exigidas pelo projeto. Consulte `.env.example` como lista de referência, mas **não copie valores secretos para o Git**. Use valores reais nos Environment Variables da Vercel.
7. Faça Deploy e confira os logs de instalação/build.

## Atenção às dependências de runtime

O painel usa serviços e pacotes que podem exigir banco PostgreSQL, Redis/filas, autenticação, armazenamento, webhooks e serviços auxiliares. Esses recursos devem ser provisionados e as URLs/segredos correspondentes configurados antes de esperar que todas as funções funcionem. A Vercel hospeda o painel Next.js, mas não mantém automaticamente processos worker ou servidores WebSocket persistentes apenas porque o monorepo foi importado.

## Se a compilação falhar

Abra **Deployments → deployment → Build Logs** e copie o primeiro erro real (remova tokens, URLs privadas e segredos antes de compartilhar). Não crie variáveis de ambiente com valores inventados para tentar passar a compilação.
