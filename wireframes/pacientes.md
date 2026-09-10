# Wireframe — Página Pacientes

Composição: UX Director, Information Architect, UI Specialist.

Base: `strategy/information-architecture.md` (seção Pacientes), `strategy/personas.md` (Persona 1), `strategy/conversion-strategy.md`.

Breakpoints de referência: Desktop ≥ 1280px · Tablet 768–1279px · Mobile < 768px.

Este documento descreve estrutura e função. Não contém copy final nem Lorem Ipsum.

---

## 1. Objetivo da página

Reduzir objeções e converter visitantes qualificados em agendamento de avaliação, sem recorrer a gatilhos comerciais agressivos.

## 2. Jornada do usuário

Chegada (com desconfiança/cautela natural) → confirmação de que está no lugar certo → tradução da filosofia da marca em benefício pessoal → redução da objeção técnica ("vou ficar artificial") → redução da objeção de experiência ("serei tratada como número") → validação por prova social → neutralização de objeções remanescentes (FAQ) → ação de agendar avaliação.

## 3. Ordem de leitura

1. Hero de continuidade
2. Promessa aplicada ao paciente
3. Método / abordagem clínica
4. A experiência de ser paciente
5. Prova social qualificada
6. FAQ de objeções
7. Convocação final
8. Rodapé institucional

---

## 4. Estrutura completa das seções

### 4.1 Hero de continuidade

**Objetivo:** confirmar que o visitante está no território da mesma marca vista no Portfolio, já direcionado ao universo paciente.

**Componentes:**
- Navegação minimalista (logo + link discreto de retorno ao Portfolio).
- Imagem editorial (registro do universo "paciente" — mais próxima, mais pessoal que o hero institucional).
- Título curto de contexto (não é a promessa geral da marca, já é direcionado a "cuidar do seu rosto").
- CTA já presente aqui, em versão discreta (ver seção 6).

**Hierarquia:** imagem ainda domina, mas com menos escala que o hero do Portfolio — esta página é mais próxima/íntima, menos monumental.

**Comportamento:** estático, sem parallax pesado.

**Imagens necessárias:** 1 imagem editorial com tom mais pessoal/próximo (rosto em close, luz suave), coerente com `brandbook/FOTOS NOVAS`.

**CTA:** versão secundária/discreta de "Agendar avaliação" (âncora para seção 7), não o botão de maior destaque da página.

---

### 4.2 Promessa aplicada ao paciente

**Objetivo:** traduzir a filosofia da marca ("revelar, não criar") em benefício sensível e direto para quem está decidindo confiar seu rosto a uma profissional.

**Componentes:**
- Bloco de texto curto, centralizado ou em coluna de leitura confortável.
- Pode incluir uma imagem de apoio lateral (rosto/detalhe) em vez de bloco puramente tipográfico, para reforçar proximidade (diferente da seção equivalente no Portfolio, que é puramente tipográfica).

**Hierarquia:** texto como elemento central; imagem, se presente, é apoio, não protagonista.

**Comportamento:** entrada suave ao rolar.

**Imagens necessárias:** opcional — 1 imagem de detalhe (mãos, textura de pele, luz), sóbria, não clínica/fria.

**CTA:** nenhum.

---

### 4.3 Método / abordagem clínica

**Objetivo:** reduzir a objeção "vou ficar com cara de artificial/padronizada" com racional técnico-científico apresentado de forma acessível.

**Componentes:**
- Bloco explicativo do método (etapas ou princípios do processo de avaliação e planejamento — estrutural, não comercial).
- Pode usar numeração discreta (ex.: 3 etapas do processo) sem parecer "funil de vendas".

**Hierarquia:** clareza acima de tudo — esta seção existe para tranquilizar racionalmente, deve ser a mais "didática" da página.

**Comportamento:** estático, sem necessidade de animação.

**Imagens necessárias:** opcional — imagem de ambiente/consultório ou material técnico, se disponível e coerente com o padrão visual (evitar estética de clínica genérica).

**CTA:** nenhum.

---

### 4.4 A experiência de ser paciente

**Objetivo:** reduzir a objeção "serei tratada como número" — comunicar cuidado, escuta e individualidade do atendimento.

**Componentes:**
- Bloco narrativo curto sobre como é o processo de avaliação/acompanhamento (o "como", não o "quanto custa").
- Pode incluir imagem do espaço físico/atendimento, se disponível, ou permanecer puramente textual e sóbrio.

**Hierarquia:** tom mais pessoal que a seção 4.3 — aqui fala-se de experiência humana, não de método técnico.

**Comportamento:** estático.

**Imagens necessárias:** opcional — imagem de ambiente/consultório com estética alinhada ao Brand Book.

**CTA:** nenhum.

---

### 4.5 Prova social qualificada

**Objetivo:** reduzir a objeção "não sei se posso confiar" com evidência de terceiros, sempre sóbria.

**Componentes:**
- Bloco de depoimentos (1–3 por vez, com possível rotação/carrossel discreto) — texto específico e verossímil, nunca hiperbólico (`strategy/conversion-strategy.md`, seção 3).
- Atribuição discreta (iniciais ou primeiro nome, respeitando privacidade), sem fotos "antes/depois".

**Hierarquia:** o texto do depoimento é o elemento central; qualquer elemento gráfico (aspas, moldura) deve ser mínimo.

**Comportamento:** rotação automática opcional e lenta, ou navegação manual discreta.

**Imagens necessárias:** nenhuma obrigatória — priorizar texto. Se houver, apenas retrato sóbrio da pessoa (com consentimento), nunca imagem de procedimento.

**CTA:** nenhum.

---

### 4.6 FAQ de objeções

**Objetivo:** neutralizar objeções remanescentes (segurança, processo, investimento) antes da decisão final, sem tom defensivo ou comercial.

**Componentes:**
- Acordeão de perguntas frequentes, baseado nas objeções listadas em `strategy/brand-analysis.md` (seção 7, eixo Paciente).
- Perguntas cobrindo no mínimo: segurança/naturalidade do resultado, processo de avaliação, o que esperar na primeira consulta, dúvidas sobre investimento (respondidas com transparência serena, não com tabela de preços).

**Hierarquia:** perguntas em ordem de relevância decrescente (da objeção mais comum para a mais específica).

**Comportamento:** expansão/colapso ao clique, apenas um item aberto por vez (padrão de acordeão), transição suave.

**Imagens necessárias:** nenhuma.

**CTA:** nenhum dentro do FAQ — a ação fica reservada à seção 7.

---

### 4.7 Convocação final

**Objetivo:** converter confiança acumulada em ação concreta.

**Componentes:**
- Bloco de fechamento com imagem editorial (pode retomar o tom do hero) + frase de fechamento curta + botão de CTA em destaque máximo desta página.
- Pode incluir texto de transparência sobre o próximo passo (o que acontece após clicar), reduzindo incerteza sem prometer resultado.

**Hierarquia:** o CTA aqui é o elemento de maior destaque visual de toda a página.

**Comportamento:** estático.

**Imagens necessárias:** 1 imagem editorial de fechamento, tom sereno.

**CTA principal:** "Agendar avaliação" — botão de maior contraste/tamanho da página.

---

### 4.8 Rodapé institucional

Idêntico em função ao rodapé do Portfolio (ver `wireframes/portfolio.md`, seção 4.7) — dados de contato, retorno à navegação, sem reabrir CTA de conversão com o mesmo peso da seção 4.7.

---

## 5. Componentes esperados (biblioteca da página)

- Navegação com retorno ao Portfolio.
- Hero de continuidade com CTA discreto.
- Bloco de promessa aplicada (texto + imagem opcional).
- Bloco de método (lista numerada discreta).
- Bloco de experiência (narrativo + imagem opcional).
- Carrossel/lista de depoimentos.
- Acordeão de FAQ.
- Bloco de convocação final com CTA de destaque máximo.
- Rodapé institucional (compartilhado com as demais páginas).

## 6. Posicionamento dos CTAs

"Agendar avaliação" aparece **duas vezes**: em versão discreta no hero (seção 4.1, como âncora de intenção antecipada) e em versão de destaque máximo na convocação final (seção 4.7). Nenhuma outra seção interrompe a leitura com CTA — respeita o limite de repetição definido em `strategy/conversion-strategy.md` (seção 4).

## 7. Comportamento responsivo

**Tablet (768–1279px):**
- Seções com layout texto+imagem lado a lado (4.2, 4.4) passam a empilhar caso o espaço fique apertado, priorizando legibilidade.
- Depoimentos (4.5) mantêm carrossel, ajustando para exibir 1 item por vez em vez de múltiplos.
- FAQ (4.6) mantém acordeão de largura total.

**Mobile (< 768px):**
- Todas as seções em coluna única.
- Hero (4.1) com imagem em proporção retrato, CTA discreto visível sem exigir rolagem excessiva.
- Depoimentos (4.5) em carrossel de deslize horizontal por toque, 1 item por vez.
- FAQ (4.6) com áreas de toque ampliadas (mínimo 44px de altura) para acessibilidade.
- Convocação final (4.7): CTA fixo de largura total, com folga adequada de toque.

## 8. Observações de UX

- Nenhuma menção a preço como gancho, nenhum contador, nenhum selo de "vagas limitadas" (`knowledge/03-brand-rules.md`).
- O botão "Agendar avaliação" deve manter identidade visual consistente (cor, tipografia, raio de borda) em todas as suas ocorrências na página.
- Depoimentos e FAQ devem ser tratados com o mesmo cuidado editorial do restante da página — nunca em componente de UI genérico/"template de SaaS".
- Avaliar, na Fase 4, se o formulário/fluxo pós-clique de "Agendar avaliação" é embutido (modal/seção) ou redireciona para agenda externa — decisão técnica, não estratégica, a ser validada antes da implementação.
