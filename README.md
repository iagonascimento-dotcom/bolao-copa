# 🏆 Bolão da Copa 2026 · Roda Conveniência

Web app para gerenciar bolões da Copa do Mundo 2026 nas ações de condomínio da **Roda Conveniência** (mercadinhos dentro de condomínios).

Funciona direto no celular, sem instalar nada. Cada PDV pode ter seus próprios jogos rodando ao mesmo tempo.

## ⚽ O que o app faz

- **Cadastrar jogo** vinculado a um PDV (ex: `Brasil × Marrocos` no `MM BTG BOTAFOGO`, com data e horário)
- **Cadastrar palpites** dos moradores: nome, bloco, apartamento, telefone e palpite de placar
- **Listar** todas as pessoas que palpitaram em cada jogo
- **Gerar resultado**: você lança o placar final + os jogadores que marcaram gol
- **Ranking Top 5** automático com os ganhadores dos kits

## 📋 Regras do bolão

- São **5 kits** sorteados por jogo (configurável ao cadastrar)
- Pontuação dos palpites:
  - **3 pontos** — acertou o placar exato
  - **2 pontos** — acertou o vencedor e o saldo de gols
  - **1 ponto** — acertou só quem venceu (ou o empate)
- **Critério de desempate:** se mais gente acertar do que a quantidade de kits, ganha quem acertou **qual jogador marcaria gol**. Persistindo o empate, vale quem cadastrou primeiro.

## 🚀 Como colocar no ar (GitHub Pages)

1. Crie um repositório novo no GitHub (ex: `bolao-copa`)
2. Suba o arquivo `index.html` para o repositório
3. Vá em **Settings → Pages**
4. Em **Source**, escolha a branch `main` e a pasta `/ (root)`
5. Salve. Em ~1 minuto o site fica disponível em:
   `https://SEU-USUARIO.github.io/bolao-copa/`

Pronto, é só compartilhar o link com o pessoal do condomínio.

## 🗄️ Banco de dados

Os dados ficam num banco **Supabase** (projeto *Agent Roda*), online e compartilhado entre todos os dispositivos. Tabelas usadas (todas prefixadas com `bolao_` para não conflitar com o restante do sistema):

| Tabela | Função |
|---|---|
| `bolao_pdvs` | Lista dos 263 PDVs (locais das ações) |
| `bolao_jogos` | Jogos cadastrados, vinculados a um PDV |
| `bolao_palpites` | Palpites das pessoas |

## 🔒 Sobre a chave do Supabase

O `index.html` usa a **chave publishable (pública)** do Supabase, que é segura para ficar em código de front-end — ela só permite as operações liberadas pelas políticas de acesso (RLS) do banco. Não há chaves secretas no projeto.

---

Feito para a **Roda Conveniência** ⚽
