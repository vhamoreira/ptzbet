# Palpites Mundial 2026

App de palpites para o Mundial 2026, com dados guardados no Supabase (em vez do armazenamento da Claude).

## Como publicar no Vercel (sem precisar de GitHub)

1. Instala o Node.js se ainda não tiveres (https://nodejs.org — versão LTS).
2. Abre um terminal dentro desta pasta (`mundial-app`).
3. Instala as dependências:
   ```
   npm install
   ```
4. Instala a ferramenta do Vercel:
   ```
   npm install -g vercel
   ```
5. Faz login (abre o browser para autenticares):
   ```
   vercel login
   ```
6. Publica:
   ```
   vercel
   ```
   Responde às perguntas com as opções por defeito (Enter, Enter, Enter...). No final dá-te um link tipo `https://mundial-app-xxxx.vercel.app` — esse é o link para mandares aos amigos.
7. Sempre que quiseres atualizar (depois de uma alteração no código), corre `vercel --prod` outra vez dentro da pasta.

## Alternativa: GitHub + Vercel

Se preferires, cria um repositório no GitHub, faz `git push` deste código para lá, e depois em vercel.com clica em "Add New Project" e escolhe esse repositório — o Vercel deteta automaticamente que é um projeto Vite e configura tudo sozinho.

## Como funciona o armazenamento

- Os dados partilhados (resultados dos jogos, palpites de todos) ficam guardados numa tabela chamada `app_storage` no teu projeto Supabase.
- Os dados pessoais (o teu nome, se és admin) ficam guardados no `localStorage` do browser de cada pessoa — não saem do telemóvel/computador dela.
- O código do Supabase (URL + chave pública) já está dentro de `src/App.jsx`. É seguro estar ali — essa chave é pública por natureza; quem protege os dados são as regras (RLS) da tabela, já configuradas para qualquer pessoa poder ler e escrever (é um jogo entre amigos, sem necessidade de login).

## Código de admin

O código para desbloquear o painel de admin (registar resultados) continua a ser **2026** — podes mudá-lo procurando `ADMIN_PIN` em `src/App.jsx`.
