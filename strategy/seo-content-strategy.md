# SEO & Content Strategy — Dra. Ana Carolina Nogueira

Base: `strategy/positioning.md`, `strategy/conversion-strategy.md`, `strategy/information-architecture.md`, `knowledge/05-decision-log.md` (Decisões 012, 015, 016, 017, 019, 020).

Este documento registra a evolução do projeto de "landing page institucional" para "produto digital que também é encontrado por busca" — sem alterar a identidade, o posicionamento ou o tom de voz já definidos nas Fases 1–3. Ver `Prompt — Nova visão estratégica do projeto.md` (raiz do projeto) para o pedido original.

---

## 1. Diagnóstico (29/09/2026)

**O que já existe:**
- 3 páginas (Portfolio, Paciente, Aluno) com IA, wireframe e copy prontos e no ar.
- `sitemap.xml` e `robots.txt` válidos (gerados pelo Next.js).
- Um único `h1` por página; textos das animações (BlurReveal/RandomizedText) ficam acessíveis no HTML via `sr-only`, então são rastreáveis por buscadores.
- Página de Política de Privacidade (`/privacidade`).
- Domínio `acnodontologia.com.br` reaproveitado (Decisão 012) — não é domínio novo, tem histórico de tráfego real (Decisão 019).

**Lacunas técnicas identificadas:**
- Sem `canonical`, `og:image`, Twitter card ou dados estruturados (JSON-LD) em nenhuma página.
- Títulos e descrições das páginas Paciente/Aluno são genéricos, sem termo de busca.
- `alt` das imagens da bifurcação (Portfolio) é o texto do botão, não uma descrição da imagem.
- Imagens-fonte em `public/images` pesam de 8 a 21MB cada (o Next otimiza na entrega, mas isso é ineficiente no repositório/build).
- Sem página 404 personalizada.
- ~~Sem instrumentação de medição~~ — implementado em 30/09/2026 (Decisão 021): Vercel Web Analytics + Speed Insights, eventos `whatsapp_click` e `ebook_download`.
- Rodapé sem cidade/CEP — falta consistência de NAP com o Perfil da Empresa no Google (Decisão 020).

**Sobre o domínio antigo:** era um site WordPress da mesma marca/negócio (não um domínio genérico) — teve tráfego e páginas indexadas (Decisão 019). O plano de migração trata isso como ativo (redirecionar o que tem valor), não como lixo a apagar. Ver checklist técnico na seção 5.

---

## 2. Reconciliação com o Brand Book

O pedido de capturar busca por termos como "harmonização orofacial", "procedimentos estéticos", "visagismo" e "mentoria/curso" parece, à primeira vista, tensionar com `knowledge/03-brand-rules.md` ("não vender procedimentos nem cursos", "nunca marketing agressivo"). Na prática, não tensiona — desde que se preserve uma distinção:

| Tipo de conteúdo | Exemplo | Permitido? |
|---|---|---|
| Comercial/transacional | Preço, promoção, "agende agora e ganhe desconto" | Não — nunca |
| Educacional/autoral | O que é o procedimento, como ela avalia antes de indicar, ciência por trás, cuidados | Sim — é o próprio tom "Sábio" da marca |

Google trata conteúdo de saúde como YMYL (Your Money or Your Life) e recompensa exatamente o que o Brand Book já exige: texto sóbrio, assinado por quem pratica, sem promessa de resultado. A restrição de tom não é um obstáculo para SEO médico — é o que o Google busca (E-E-A-T: Experience, Expertise, Authoritativeness, Trust).

**Atenção jurídica:** conteúdo sobre procedimento odontológico/estético segue as regras de publicidade do CFO (Conselho Federal de Odontologia) — proibição de antes/depois, promessa de resultado, preço como gancho. Toda página de procedimento precisa de validação da Dra. (ou de seu advogado) antes de publicar. Isso é adicional à revisão de tom de voz já exigida em `knowledge/04-voice-and-tone.md`.

---

## 3. Mapa de intenção de busca

| Intenção | Exemplos de busca | Página/conteúdo que atende |
|---|---|---|
| Informacional — paciente | "o que é harmonização orofacial", "harmonização dói", "diferença entre preenchimento e harmonização" | Artigos de procedimento + Visagismo |
| Comercial investigativa — paciente | "harmonização orofacial Curitiba", "harmonização resultado natural" | `/paciente` (otimizada) + SEO local |
| Navegacional/marca | "Ana Carolina Nogueira dentista", "Be Younger HOF" | `/` (Portfolio), dados estruturados de pessoa |
| Informacional — profissional | "como aprender harmonização orofacial", "o que é visagismo aplicado à odontologia" | Artigos de formação + Visagismo |
| Comercial investigativa — profissional | "mentoria full face", "curso HOF completo" | `/aluno` (otimizada) |

---

## 4. Pilares de conteúdo

| Pilar | Conteúdo | Alimenta | Observação |
|---|---|---|---|
| **Procedimentos** | Uma página por procedimento real (o que é, para que serve, como ela avalia, cuidados, FAQ) | `/paciente` | Depende da lista de procedimentos (Dra. Ana — pendente) + validação CFO |
| **Palestras & ciência aplicada** | Registro do que já foi apresentado (Univ. de Leida 2024, Full Face Congress 2025, SBTI, Face Congress) | `/paciente` e `/aluno` | Conteúdo autoral, não replicável por concorrentes |
| **Visagismo** | Extensão do e-book | `/paciente` e `/aluno`, prioritariamente Aluno (Decisão 017) | Pilar já validado |
| **Formação/mentoria** | Método de ensino, o que uma especialização em HOF exige | `/aluno` | — |

**Arquitetura proposta:** rota única `/conteudo/[slug]` com campo de categoria (procedimento, palestra, visagismo, formação), em vez de pastas separadas por tipo — um template, um sitemap, manutenção mais simples. Cada artigo termina com convite discreto para `/paciente` ou `/aluno`, nunca um CTA de venda.

---

## 5. Checklist técnico — domínio antigo

| # | Ação | Responsável |
|---|---|---|
| 1 | Cadastrar propriedade de domínio no Google Search Console, enviar sitemap | Usuário (feito, em andamento) |
| 2 | Solicitar indexação manual das 4 páginas atuais | Usuário |
| 3 | Atualizar URL do site no Perfil da Empresa do Google para o domínio novo | Usuário — confirmar |
| 4 | Ferramenta "Remover conteúdo desatualizado" do Google para snapshots antigos do WordPress | Usuário, se necessário |
| 5 | Redirecionar `/politica-de-privacidade` → `/privacidade` e `/project` → `/` | Pendente aprovação de implementação |
| 6 | Página 404 personalizada, na identidade da marca | Pendente aprovação de implementação |
| 7 | Deixar o restante (`wp-content`, `wp-admin`, `wp-json`) resolver em 404 naturalmente | Nenhuma ação necessária |

---

## 6. Programa de fases

| Fase | Pergunta que responde | Entregáveis | Status |
|---|---|---|---|
| **1 · Brand** | — | Brandbook, knowledge | Concluída |
| **2 · Business/Marketing** | Quem procura, com qual intenção, o que é sucesso? | Mapa de intenção de busca (seção 3), metas de aquisição (Google como eixo — Decisão 016) | Em andamento |
| **3 · Structure/Content** | Onde mora cada conteúdo? | Arquitetura `/conteudo/[slug]` (seção 4), modelo de artigo | A iniciar |
| **4 · SEO/Content Engine** | Como ser encontrada? | (a) Fundação técnica: canonical, og:image, JSON-LD, títulos/descrições, alt, redirects, 404, NAP consistente; (b) calendário editorial e primeiros artigos-âncora | Fundação técnica pendente de aprovação; conteúdo pendente da lista de procedimentos |
| **5 · Measurement** | O que está funcionando? | Analytics sem cookies, eventos de conversão (clique WhatsApp por persona, envio do e-book), Search Console, processo manual via secretária como fallback (Decisão 018) | Analytics implementado (Decisão 021); painel/rotina mensal de revisão ainda a definir |

---

## 7. Pendências abertas

1. Lista de procedimentos que a Dra. Ana realiza de fato (bloqueia o pilar "Procedimentos") — aguardando conversa do usuário com a Dra.
2. Endereço exato como aparece no Perfil da Empresa do Google (rua, número, bairro) — para deixar o rodapé e os dados estruturados idênticos ao perfil (Decisão 020).
3. Aprovação para implementar os itens 5 e 6 da seção 5 (redirects + página 404) — proposto, aguardando sim/não do usuário.
4. Validação jurídica (CFO) antes de publicar qualquer página de procedimento.
