# Status atual do projeto

Última atualização: 10/11/2026. Este documento é o ponto de partida pra retomar o projeto — resume o estado real das coisas sem precisar ler o `05-decision-log.md` inteiro. Em caso de dúvida sobre o porquê de alguma decisão, o decision-log tem o detalhe; este arquivo só diz **onde as coisas estão agora**.

Se você é um Claude novo retomando este projeto: leia este arquivo, depois `05-decision-log.md` por cima, e os arquivos de `strategy/` e `knowledge/` conforme a tarefa pedir. Os repositórios são:

- **Site** (Next.js, no ar): `github.com/Vicoftn/lps12.git` — branches `main` (produção) e `feat/spell-animations` (mantida em espelho de `main`, sem motivo prático pra divergirem).
- **Contesto** (este repositório — documentação/estratégia/ativos de marca): `github.com/Vicoftn/lpmommy.git`.

---

## 1. O que está no ar, funcionando e verificado

- **Site:** `https://www.acnodontologia.com.br`, hospedado na Vercel, 4 páginas (`/`, `/paciente`, `/aluno`, `/privacidade`), domínio e DNS configurados na Vercel.
- **E-book por e-mail:** formulário em `/` (seção 4.6) → Resend envia o link → PDF hospedado no Vercel Blob (`ebook-visagismo-hof.pdf`, público). Testado ponta a ponta, e-mail chega, link baixa.
- **Privacidade:** página `/privacidade`, linkada no rodapé/formulário/e-mail. CRO-PR 12088 exibido no rodapé, e-mail e política.
- **Redirects + 404:** `/politica-de-privacidade` → `/privacidade`, `/project` → `/` (301). Página 404 própria, na identidade da marca.
- **Analytics:** Vercel Web Analytics + Speed Insights (não GA4 — ver Decisão 021 pro porquê). Eventos: `whatsapp_click` (com a persona), `ebook_download`, `ebook_download_error`. Sem cookie, sem banner.
- **SEO técnico:** sitemap.xml e robots.txt corretos, Search Console com propriedade de domínio verificada (`sc-domain:acnodontologia.com.br`), sitemap enviado, indexação confirmada (checado em 10/11/2026). Títulos com termo de busca real em `/paciente` e `/aluno`. `canonical`, `og:image`/Twitter Card por página e dados estruturados (JSON-LD, `Dentist`, com o endereço/telefone/CRO) nas 4 páginas, verificados em produção — ver Decisão 024.
- **Imagens-fonte:** comprimidas em 10/11/2026, `public/images` caiu de ~120MB para ~8MB, sem perda visual — ver Decisão 025. Script reutilizável em `site/scripts/compress-source-images.mjs` para fotos novas.
- **Rodapé:** endereço completo (Av. Mal. Floriano Peixoto, 306 – Conj. 61 – Centro, Curitiba – PR, 80010-130), igual ao Perfil da Empresa no Google (já existia e está correto).

## 2. Variáveis de ambiente / credenciais (não estão em nenhum arquivo do repositório)

Configuradas direto no painel da Vercel (Project → Settings → Environment Variables). Se for reconfigurar o projeto do zero numa conta nova, precisa recriar:

- `RESEND_API_KEY` (secret) — conta Resend, domínio `acnodontologia.com.br` verificado (SPF/DKIM/DMARC já estão no DNS da Vercel).
- `EMAIL_FROM` (config) — remetente do e-mail do e-book.
- `EBOOK_DOWNLOAD_URL` (config) — URL pública do PDF no Vercel Blob.
- `BLOB_READ_WRITE_TOKEN` — só precisa localmente, num `.env.local` (nunca commitado), pra rodar `site/scripts/upload-ebook.mjs` de novo caso o PDF mude.

## 3. O que está decidido mas ainda não implementado — bloqueado por conteúdo da Dra.

Arquitetura e template já definidos (Decisões 022 e 023), só falta o conteúdo real. **Pendências que destravam tudo isso, todas dependem de uma conversa do usuário com a Dra. Ana:**

1. **Lista real dos procedimentos** que ela realiza (nome, o que é, como ela avalia antes de indicar).
2. **Decisão sobre antes/depois** nas páginas de procedimento — precisa do aval dela (e possivelmente advogado), por causa das regras do CFO. Ver Decisão 022 pro racional completo (inclusive por que copiar o que uma concorrente faz não é seguro aqui).
3. **Datas e números das turmas de Mentoria VIP Full Face** já ministradas, pra seção "Turmas realizadas".

Quando isso chegar, implementar nesta ordem (tudo já desenhado, só falta o conteúdo):

- `/procedimentos` (hub, grid de cards) + `/procedimentos/[slug]` (template: intro → como funciona → para quem é indicada → o que pode proporcionar → CTA de WhatsApp específico → relacionados). Título de cada página: "`[Procedimento] em Curitiba`".
- Seção nova dentro de `/paciente` com os cards de procedimento.
- Seção nova no Portfolio (`/`): carrossel de fotos reais de procedimento acontecendo, sem preço, sem venda, link pra `/paciente` (emenda a Decisão 002, ver Decisão 022).
- Seção "Turmas realizadas" dentro de `/aluno` (lista/timeline, não páginas individuais por turma — risco de conteúdo fino).

## 4. O que foi avaliado e descartado (não repetir)

- GA4 — trocado por Vercel Analytics (Decisão 021).
- Página própria por turma de mentoria — vira conteúdo fino/duplicado; optou-se por seção única em `/aluno` (Decisão 023).
- Lista de procedimentos no Portfolio — avaliado, mantido só carrossel de fotos, sem lista/texto de venda.
- Widget de Google Reviews — avaliado, mantido como está (só vídeos) por ora, pode ser retomado depois.

## 5. Como rodar localmente

```
# site/
npm install
npm run dev          # ou: npx next dev -p 3000
```

Precisa do `.env.local` (ver seção 2) só se for testar o envio de e-book local. Sem ele, o formulário retorna erro 500 controlado ("Serviço de e-mail não configurado"), o resto do site funciona normal.

## 6. Convenções deste projeto, pra quem for continuar

- Nunca commitar/subir nada sem aprovação explícita do usuário — ele revisa o diff antes.
- Toda decisão estrutural nova vira uma entrada no `05-decision-log.md`, numerada sequencialmente.
- Brand Book prevalece sobre qualquer decisão em conflito (Decisão 005). Tom sempre sereno, nunca promocional — ver `03-brand-rules.md` e `04-voice-and-tone.md`.
- `main` e `feat/spell-animations` do site ficam sempre sincronizadas — não há motivo pra divergirem hoje.
