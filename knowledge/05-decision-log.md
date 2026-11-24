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

## Decisão 022

Análise comparativa com concorrente real (fordermclinic.com.br, Dra. Andressa Faucz) em 19/10/2026, feita sob pedido do usuário, definiu a arquitetura de **Procedimentos** (pilar "Procedimentos" de `strategy/seo-content-strategy.md`, seção 4):

- Rotas: `/procedimentos` (hub, grid de cards) + `/procedimentos/[slug]` (página individual, template único reutilizável: intro → como funciona → para quem é indicada → o que pode proporcionar → CTA de WhatsApp específico do procedimento → procedimentos relacionados).
- A página `/paciente` ganha uma seção com os cards de procedimentos, como entrada principal para esse conteúdo.

**Emenda à Decisão 002** (Portfolio "não venderá procedimentos nem cursos"): o Portfolio ganha uma seção nova, estilo carrossel, com fotos reais de procedimentos em andamento (ex.: aplicação de preenchimento, microagulhamento) — sem preço, sem nome técnico, sem CTA de venda, só uma frase curta e link para `/paciente`. Motivo: visitante novo não tinha nenhuma pista visual de que a prática é real antes de decidir qual caminho seguir. A Decisão 002 permanece válida quanto a "não vender" — a seção é evidência visual, não oferta.

**Avaliações/depoimentos:** mantidos como estão (vídeos do YouTube em `/paciente` e `/aluno`). Widget de Google Reviews avaliado e descartado por ora.

**Antes/depois:** não implementado. Decisão explicitamente adiada — precisa de confirmação direta da Dra. Ana (e possivelmente de advogado) antes de qualquer trabalho de design ou código. Achado relevante que motiva a cautela: a concorrente usada como referência (Dra. Andressa Faucz) se apresenta como biomédica esteta, não cirurgiã-dentista — segue outro conselho profissional (CRBM), com regras de publicidade diferentes das do CFO que regem a Dra. Ana (CRO-PR 12088). As fotos de antes/depois vistas no site dela não tinham aviso de consentimento nem de variação de resultado. Copiar esse elemento não é risco equivalente entre as duas.

**Achado complementar:** a página de Cursos e Mentorias da concorrente é a mais fraca do site dela (sem link para curso individual, sem formato, sem depoimento de aluno, sem CTA dedicado) — nossa página `/aluno` já é estruturalmente mais forte nesse ponto (estrutura da formação, suporte pós-curso, depoimentos em vídeo reais). Não é prioridade de melhoria.

**Pendências para avançar com Procedimentos:** lista real dos procedimentos que a Dra. Ana realiza (bloqueador principal, segue pendente desde a Decisão 015); confirmação da Dra. sobre antes/depois.

---

## Decisão 023

Padrão de `<title>` com termo de busca real + cidade, adotado para `/paciente` e `/aluno` (e que se repete em `/procedimentos/[slug]` quando a lista de procedimentos chegar — ver Decisão 022):

- `/paciente`: "Harmonização Orofacial em Curitiba"
- `/aluno`: "Mentoria VIP Full Face em Curitiba" (menção a "Be Younger HOF" fica na description, não no title — o title já soma 58 caracteres com o sufixo automático "— Ana Carolina Nogueira" do layout; incluir também a marca de ensino estourava o limite de ~60 caracteres do Google e cortava o texto no resultado de busca)

Decisão sobre registro de mentorias ministradas (Decisão 022): fica como seção dentro de `/aluno` ("Turmas realizadas" — data, número da turma, referência à Be Younger HOF em cada linha), não como páginas individuais por turma. Motivo: conteúdo por turma seria fino demais (só data e número) para justificar uma URL própria — risco de conteúdo fino/duplicado no Google. Só reconsiderar página própria por turma se cada uma tiver conteúdo único (fotos, depoimento específico daquela edição). Avaliado e descartado colocar essa lista também no Portfolio — a seção "Prova de autoridade" já cobre credibilidade de ensino em nível mais alto para os dois públicos; detalhe operacional de turma pertence a `/aluno`, onde já está decidido quem quer ser aluno.

Implementado e verificado em produção em 19/10/2026.

---

## Decisão 024

Fundação técnica de SEO (Fase 4, parte que não depende de conteúdo novo da Dra.) implementada em 10/11/2026:

- `canonical` em todas as 4 páginas.
- `og:image`/Twitter Card por página (imagens próprias geradas a partir das fotos já existentes, 1200×630, em `public/og/`), com fallback pro Portfolio nas páginas sem imagem dedicada.
- Dados estruturados (JSON-LD, tipo `Dentist`) no layout raiz — nome, endereço (igual ao Perfil da Empresa, Decisão 020), telefone, e-mail, CRO, Instagram. Presente em todas as páginas.
- `alt` de imagem corrigido em duas fotos do Portfolio que descreviam o botão, não a imagem.
- 404 com `noindex` explícito (Next.js já injeta um `noindex` próprio nela também — redundante, mas inofensivo).

**Achado técnico registrado pra não repetir o erro:** definir `openGraph` no metadata de uma página do Next.js **substitui** o objeto inteiro herdado do layout, não mescla campo a campo — `site_name`/`locale`/`type` precisam ser repetidos em cada página que define `openGraph.images`, senão somem do HTML. `twitter` já herda normalmente, não tem esse problema.

Verificado em produção (canonical, og:image e JSON-LD conferidos nas 4 URLs reais).

---

## Decisão 025

Imagens-fonte em `public/images` (fotos direto da câmera, 8 a 22MB cada, ~120MB no total) foram redimensionadas (largura máxima 3840px) e recomprimidas (JPEG mozjpeg, qualidade 82), em 10/11/2026. Resultado: ~8MB no total (redução de 93%), sem perda visual perceptível (conferido lado a lado, com zoom em rosto/pele/cabelo, nas 3 fotos mais críticas, e teste visual das 3 páginas no navegador antes do commit).

Não afeta o que o visitante já via — o `next/image` já servia versões otimizadas na entrega. O ganho é em peso do repositório, velocidade de build e de deploy.

Script reutilizável adicionado em `site/scripts/compress-source-images.mjs`, para comprimir fotos novas que a Dra. envie no futuro antes de subir ao repositório.

---

## Decisão 026

Aditivo à Decisão 022 (carrossel de fotos reais no Portfolio): o tipo de foto prioritário a pedir pra Dra. Ana é ela **marcando/avaliando o rosto do paciente e explicando** (leitura de Visagismo em ação), não só "procedimento acontecendo" de forma genérica. Sugerido em 24/11/2026, pelo usuário.

Motivo: é a prova visual mais direta do próprio conceito central da marca ("ler o rosto antes de tocá-lo") — mais forte como prova de método do que uma foto só de técnica. Serve às duas pontas sem criar conteúdo duplicado:

- **Paciente:** entra no carrossel do Portfolio já aprovado (Decisão 022) — reduz o medo de "procedimento às cegas", mostra análise antes de intervenção.
- **Aluno:** reforça com imagem real a promessa já existente em `/aluno` de "hands-on e atendimento clínico em pacientes" durante a formação.

Recomendação registrada pra quando o pedido de fotos for feito à Dra.: preferir ângulos em que o paciente não fique totalmente identificável de frente, a menos que ele já tenha autorizado aparecer — reduz a exigência de autorização de imagem por foto e mantém o foco na Dra. Isso não substitui a exigência de autorização sempre que o rosto do paciente for reconhecível (ver Decisão 027).

Ainda bloqueado pelo mesmo motivo de sempre: depende da sessão de fotos / material que a Dra. Ana enviar.

---

## Decisão 027

**Antes/depois nas páginas de procedimento: aprovado.** Confirmado em 24/11/2026 pelo usuário, que conversou diretamente com a Dra. Ana — ela quer usar antes/depois. Isso resolve o bloqueio registrado na Decisão 022 (que exigia confirmação direta dela, por risco regulatório específico do CFO para cirurgiões-dentistas).

Condições registradas junto com a aprovação:

1. **Toda foto de antes/depois precisa de autorização do paciente**, sem exceção — essa exigência não muda com a aprovação do formato; é uma camada separada (LGPD/direito de imagem) que vale pra cada paciente individualmente, não uma autorização genérica única.
2. **Aviso de que o resultado varia de paciente para paciente** deve acompanhar o antes/depois. Recomendação registrada (decisão de implementação, não só documento interno): colocar uma linha curta e discreta junto de cada par de fotos na própria página de procedimento (ex.: "Resultado individual — pode variar de paciente para paciente"), no mesmo tom sóbrio do Brand Book — não como aviso jurídico extenso, mas como frase natural. Motivo de recomendar isso no site, não só em formulário de consentimento interno: é exatamente o tipo de cautela que o CFO cobra (não prometer resultado igual/garantido), e tem custo de implementação praticamente zero.

**Não registrado como confirmado:** se um advogado da Dra. revisou especificamente esse formato — a Decisão 022 mencionava isso como possível, não obrigatório. Se isso for relevante, vale confirmar com ela antes de publicar a primeira página de procedimento com antes/depois.

Ainda bloqueado pelo mesmo motivo de sempre: depende da lista de procedimentos e do material de fotos que a Dra. Ana enviar (ver Decisão 015/022). A pendência nº 3 da seção 7 de `strategy/seo-content-strategy.md` (validação jurídica geral do CFO antes de publicar qualquer página de procedimento) continua de pé, independente do antes/depois.

---

## Próximas decisões

Registrar todas as mudanças importantes aprovadas durante o projeto.