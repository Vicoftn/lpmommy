# Decision Log

Este documento registra todas as decisões importantes do projeto.

Seu objetivo é manter consistência durante todas as fases do desenvolvimento.

Sempre que uma decisão estrutural for tomada, registre-a aqui.

---

## Decisão 001

A landing será composta por três páginas.

- Portfolio
- Paciente
- Aluno

---

## Decisão 002

A página Portfolio será responsável apenas por apresentar a marca e direcionar o visitante.

Ela não venderá procedimentos nem cursos.

---

## Decisão 003

A página Paciente terá como único objetivo converter visitantes em pacientes.

CTA principal:

Agendar avaliação.

---

## Decisão 004

A página Aluno terá como único objetivo converter profissionais interessados em cursos.

CTA principal:

Entrar para a próxima turma.

---

## Decisão 005

Toda comunicação seguirá rigorosamente o Brand Book.

Caso exista conflito entre qualquer decisão e o Brand Book, o Brand Book prevalece.

---

## Decisão 006

O WhatsApp é segmentado por persona, com dois números distintos:

- Paciente → número da clínica (41 98506-6632).
- Aluno → número pessoal da Dra. Ana (41 99962-1255).

Cada botão abre uma mensagem inicial diferente, adaptada à persona, mencionando que a pessoa veio do site. Isso permite filtrar a origem dos leads diretamente pelo WhatsApp.

---

## Decisão 007

O e-book de Visagismo não fica disponível para download direto na página.

Ele é entregue por e-mail, mediante formulário (nome + e-mail) na página Portfolio (seção 4.6). O link de download é enviado por e-mail transacional.

---

## Decisão 008

A Dra. Ana Carolina é CEO da marca de ensino **Be Younger HOF**. A logo da Be Younger HOF aparece no rodapé do site, ao lado da logo ACN.

---

## Decisão 009

Os depoimentos em vídeo (pacientes e alunos) ficam hospedados no YouTube (Shorts, já com legenda), embutidos no site como player facade 9:16 — não são hospedados localmente.

---

## Decisão 010

Os infoprodutos "Kit de Visagismo (Formatos Faciais)" e "Kit Fotográfico" ficam adiados. Não fazem parte do escopo atual do site.

---

## Decisão 011

O nome oficial da formação é **Mentoria VIP Full Face** — "VIP" sempre maiúsculo em toda a comunicação.

---

## Decisão 012

O domínio do site é `acnodontologia.com.br`, registrado no Registro.br. É o mesmo domínio usado anteriormente pelo site em WordPress da mãe da Dra. Ana (mesma marca/negócio, plataforma antiga) — não é um domínio novo, então o histórico e a autoridade dele no Google são reaproveitados, não descartados.

O DNS foi delegado para os nameservers da Vercel (`ns1`/`ns2.vercel-dns.com`), que hospeda o site atual (Next.js). Toda gestão de DNS (incluindo registros de e-mail) passou a ser feita no painel da Vercel, não mais no Registro.br.

---

## Decisão 013

O envio do e-book por e-mail usa **Resend** (e-mail transacional) com domínio `acnodontologia.com.br` verificado (SPF/DKIM/DMARC). O PDF (112MB) é hospedado no **Vercel Blob** (store público), não enviado como anexo.

Variáveis de ambiente no projeto Vercel: `RESEND_API_KEY` (secret), `EMAIL_FROM` e `EBOOK_DOWNLOAD_URL` (config). Fluxo testado e funcionando em produção (28/09/2026).

---

## Decisão 014

O site tem uma página de Política de Privacidade (`/privacidade`), linkada no rodapé de todas as páginas, no formulário do e-book e no rodapé do e-mail transacional. O e-mail do e-book também traz `reply-to` para o e-mail pessoal da Dra., para pedidos de exclusão de dados.

O CRO da Dra. Ana (**CRO-PR 12088**) passou a ser exibido no rodapé do site, no e-mail do e-book e na Política de Privacidade.

---

## Decisão 015

O escopo do projeto se abre para **conteúdo editorial** (SEO / Content Engine), revisando a restrição registrada em `strategy/sitemap.md` §6 ("fora de escopo nesta fase"). Aprovado em 29/09/2026, condicionado a: todo texto publicado é escrito ou validado pela Dra. Ana antes de ir ao ar.

Ver `strategy/seo-content-strategy.md` para o plano completo (pilares de conteúdo, arquitetura, mapa de intenção de busca, fases).

---

## Decisão 016

Direção de aquisição: o crescimento prioritário é via **Google** (SEO orgânico + Google Ads), não Instagram — o Instagram já é o canal forte da Dra. por conta própria e não é foco deste projeto.

---

## Decisão 017

O e-book de Visagismo é direcionado prioritariamente ao público **Aluno** (profissionais), não ao público Paciente — ainda que hospedado na página Portfolio, acessível a ambos.

---

## Decisão 018

Não existe instrumentação digital de atribuição de leads ainda (Fase 5 do projeto). Até que exista, a origem de cada lead novo (paciente ou aluno) é registrada manualmente pela secretária da Dra., a partir do relato do próprio lead.

---

## Decisão 019

O domínio antigo (mesmo domínio, plataforma WordPress anterior) tinha tráfego real e páginas indexadas no Google. Por isso, o histórico do domínio é tratado como ativo a preservar — URLs antigas com conteúdo relevante recebem redirecionamento 301 para o equivalente no site novo, em vez de serem simplesmente descartadas.

---

## Decisão 020

A Dra. Ana possui Perfil da Empresa no Google, com endereço em Curitiba/PR, CEP 80010-130, já correto e validado. Esse perfil é a fonte de verdade para o NAP (nome, endereço, telefone) usado no rodapé do site e em dados estruturados — precisa ser mantido idêntico entre o site e o perfil.

---

## Decisão 021

A ferramenta de analytics do site (Fase 5) é **Vercel Web Analytics + Speed Insights**, não Google Analytics (GA4). Motivos:

1. **Sem cookie, sem banner de consentimento.** GA4 identifica visitantes entre sessões via cookie, o que exige aviso de consentimento (LGPD) — normalmente um pop-up/banner, proibido por `knowledge/03-brand-rules.md`. A Vercel Analytics não usa cookie nem identificador persistente, então não precisa de banner.
2. **Sem conta/infraestrutura nova.** Já está dentro do painel da Vercel, que já é usado para hospedar o site — nenhum cadastro, propriedade ou stream de dados adicional para configurar ou aprender a navegar.
3. **Suficiente para as perguntas atuais:** volume de visitantes, páginas mais vistas, cliques no WhatsApp por persona (evento `whatsapp_click`, com o valor `paciente` ou `aluno`) e envios do e-book (`ebook_download` / `ebook_download_error`). Nenhum dado pessoal (nome/e-mail) é enviado nesses eventos.

**Limite reconhecido:** não faz funis multi-etapa nem rastreamento de campanha paga. Se o projeto avançar para Google Ads (ver Decisão 016), a conversa sobre GA4/Google Ads Conversion — e sobre o banner de cookies que isso implica — deve ser reaberta nesse momento. Implementado e verificado em produção em 30/09/2026 (evento de pageview e de clique confirmados no painel da Vercel).

---

## Próximas decisões

Registrar todas as mudanças importantes aprovadas durante o projeto.