# Wireframe — Página Portfolio

Composição: UX Director, Information Architect, UI Specialist.

Base: `strategy/information-architecture.md` (seção Portfolio), `strategy/positioning.md`, `strategy/conversion-strategy.md`.

Breakpoints de referência: Desktop ≥ 1280px · Tablet 768–1279px · Mobile < 768px.

Este documento descreve estrutura e função. Não contém copy final nem Lorem Ipsum.

---

## 1. Objetivo da página

Construir confiança suficiente, em uma única rolagem, para que o visitante escolha conscientemente entre dois caminhos: tornar-se paciente ou tornar-se aluno. A página nunca vende procedimento nem curso.

## 2. Jornada do usuário

Chegada → impacto de sofisticação imediato → reconhecimento da filosofia da marca → humanização da autoridade (quem é a Dra. Ana) → racionalização dos pilares → validação por prova de autoridade → decisão consciente de caminho.

A leitura é linear, vertical, sem atalhos de navegação que desviem o visitante da sequência antes da seção 6.

## 3. Ordem de leitura

1. Hero de marca
2. Filosofia / promessa
3. Apresentação da Dra. Ana
4. Pilares da prática
5. Prova de autoridade
6. Bifurcação de caminhos (CTAs)
7. Rodapé institucional

---

## 4. Estrutura completa das seções

### 4.1 Hero de marca

**Objetivo:** impacto imediato de sofisticação; comunicar "referência" antes de qualquer leitura.

**Componentes:**
- Barra de navegação minimalista fixa (logo "ACN" à esquerda; nenhum menu extenso — no máximo um link de retorno/âncora, mantendo o foco na rolagem).
- Imagem editorial em tela cheia (linguagem visual do motivo "pincelada sobre o rosto" presente em `brandbook/MOCKUPS`).
- Wordmark/monograma sobreposto com espaço negativo generoso.
- Uma frase de assinatura curta (a definir na fase de copy) — sem subtítulo longo.
- Indicador sutil de rolagem (seta ou linha fina), sem CTA nesta seção.

**Hierarquia:** imagem domina 70–80% do viewport; tipografia sobreposta em contraste mínimo necessário para legibilidade, sem caixas ou fundos que interrompam a fotografia.

**Comportamento:** estático ou com micro-parallax sutil na imagem ao rolar (opcional, avaliar na Fase 4 quanto a performance/Lighthouse). Nenhuma animação que atrase a percepção de conteúdo.

**Imagens necessárias:** 1 imagem editorial vertical/quase-quadrada de altíssima resolução, com espaço de respiro para sobreposição de tipografia (referência: `brandbook/MOCKUPS/1.png`).

**CTA:** nenhum. Esta seção não pede ação, apenas impressiona.

---

### 4.2 Filosofia / promessa da marca

**Objetivo:** ancorar a promessa central da marca em uma leitura de poucos segundos.

**Componentes:**
- Bloco centralizado, largura de leitura restrita (para não parecer texto de site institucional genérico).
- Tipografia de destaque (peso leve/editorial da família Blauer Nue) para a frase-promessa.
- Espaço em branco generoso acima e abaixo — nenhum elemento decorativo concorrente.

**Hierarquia:** uma única frase como elemento dominante; nenhum texto de apoio compete em peso visual.

**Comportamento:** fade-in sutil ao entrar no viewport (opcional, discreto).

**Imagens necessárias:** nenhuma — seção deliberadamente tipográfica, para criar contraste de ritmo com o hero e as seções seguintes.

**CTA:** nenhum.

---

### 4.3 Apresentação da Dra. Ana

**Objetivo:** humanizar a autoridade — transformar confiança abstrata em confiança em uma pessoa real.

**Componentes:**
- Layout dividido em duas colunas (retrato editorial + bloco de texto biográfico curto).
- Selo textual discreto de credenciais (mestre, professora, 20+ anos) — tratado como legenda, não como badge promocional.

**Hierarquia:** retrato e texto com peso visual equilibrado (50/50); nenhum elemento gráfico adicional (ícones, molduras decorativas) que destoe da sobriedade do Brand Book.

**Comportamento:** estático. Pode incluir leve entrada de imagem (fade/slide curto) ao rolar.

**Imagens necessárias:** 1 retrato editorial da Dra. Ana, estilo consistente com `brandbook/FOTOS NOVAS` (fotografia autoral, não banco de imagens genérico).

**CTA:** nenhum.

---

### 4.4 Pilares da prática

**Objetivo:** justificar racionalmente a percepção emocional já construída — ciência, arte, naturalidade, precisão, exclusividade.

**Componentes:**
- Grade de 5 itens (ícone ou numeração discreta + palavra-chave + linha de apoio curta).
- Estilo editorial: linhas finas, espaçamento amplo, sem cards com sombra/skeuomorfismo.

**Hierarquia:** os 5 itens têm peso visual idêntico entre si — nenhum pilar é hierarquicamente superior aos demais.

**Comportamento:** entrada sequencial discreta ao rolar (stagger sutil), opcional.

**Imagens necessárias:** nenhuma, ou textura/elemento gráfico mínimo extraído do Brand Book (ex.: linha, traço), nunca ícones genéricos de estoque.

**CTA:** nenhum.

---

### 4.5 Prova de autoridade

**Objetivo:** validação social qualificada — reforçar status, não popularidade.

**Componentes:**
- Faixa discreta de menções/participações (palestras, formação de profissionais, presença institucional) — tratada como lista editorial, não como carrossel de logos "estilo parceiros".
- Espaço para uma citação/depoimento de autoridade (par profissional ou instituição), se disponível.

**Hierarquia:** conteúdo textual sóbrio; nenhuma ênfase em números de vaidade (curtidas, seguidores).

**Comportamento:** estático, ou rolagem horizontal discreta se houver múltiplos itens.

**Imagens necessárias:** logos institucionais/eventos (se existirem em `brandbook/`) ou nenhuma, priorizando texto sóbrio.

**CTA:** nenhum.

---

### 4.6 Bifurcação de caminhos

**Objetivo:** converter confiança construída em decisão consciente de direção.

**Componentes:**
- Layout dividido em dois blocos de peso visual idêntico (split screen 50/50 em desktop), cada um com:
  - Imagem de apoio (uma para universo paciente, outra para universo aluno/profissional).
  - Frase de contexto curta.
  - Botão de CTA.
- Bloco esquerdo → paciente. Bloco direito → aluno (ou ordem inversa — decisão de UI a validar na Fase 4, mantendo simetria).

**Hierarquia:** simetria perfeita entre os dois blocos — nenhum CTA deve parecer primário/secundário nesta seção (reforça `strategy/conversion-strategy.md`, seção 1).

**Comportamento:** hover discreto (leve escurecimento/zoom de imagem) para indicar interatividade, sem efeitos chamativos.

**Imagens necessárias:** 2 imagens editoriais distintas, uma representando o universo clínico/paciente, outra o universo docente/profissional — ambas dentro do mesmo padrão fotográfico do Brand Book.

**CTA principal:** "Quero ser paciente".
**CTA secundário (mesmo peso visual):** "Quero aprender com a Dra."

---

### 4.7 Rodapé institucional

**Objetivo:** fechar a página com sobriedade, oferecer dados de contato/retorno sem reabrir a decisão de conversão.

**Componentes:**
- Logo/monograma reduzido.
- Dados de contato institucional essenciais.
- Links de navegação de retorno (se aplicável) — sem reabrir CTAs de conversão aqui.

**Hierarquia:** baixo contraste, discreto — não compete com a seção 6.

**Comportamento:** estático.

**CTA:** nenhum (o rodapé não repete os CTAs de conversão).

---

## 5. Componentes esperados (biblioteca da página)

- Navegação fixa minimalista.
- Bloco hero full-bleed com sobreposição tipográfica.
- Bloco de citação/promessa centralizada.
- Bloco bio dividido (imagem + texto).
- Grade de pilares (5 itens).
- Lista/faixa de prova de autoridade.
- Split-CTA de bifurcação (2 blocos simétricos).
- Rodapé institucional.
- Botão primário (estilo único, reutilizado nas 3 páginas — ver identidade visual `brandbook/CORES`).

## 6. Posicionamento dos CTAs

Único ponto de ação da página: seção 6 (Bifurcação de caminhos). Nenhum CTA aparece antes disso — inclusive a navegação do topo não deve conter botão de conversão, apenas o logo.

## 7. Comportamento responsivo

**Tablet (768–1279px):**
- Hero mantém full-bleed, texto sobreposto reduz escala proporcionalmente.
- Seção 4.3 (bio) passa de 2 colunas para empilhado (imagem acima, texto abaixo).
- Grade de pilares (4.4) passa de 5 colunas para 2–3 colunas.
- Split-CTA (4.6) pode manter lado a lado se houver espaço, ou empilhar mantendo simetria de altura.

**Mobile (< 768px):**
- Navegação vira apenas logo centralizado (sem menu hambúrguer, já que não há páginas extras a listar).
- Todas as seções em coluna única, com espaçamento vertical generoso preservado (não comprimir o "respiro" que sustenta a percepção premium).
- Grade de pilares (4.4) em lista vertical de 5 itens.
- Split-CTA (4.6) empilhado verticalmente, mantendo os dois blocos com altura e tratamento visual idênticos (nenhum vem "primeiro e maior").
- Imagens recortadas em proporção retrato, priorizando o rosto/composição central definida na fotografia oficial.

## 8. Observações de UX

- Nenhum elemento de escassez, contador ou pop-up em nenhuma etapa desta página (`knowledge/03-brand-rules.md`).
- Tempo de leitura estimado deve permanecer curto — a página não deve exigir rolagem excessiva antes da bifurcação; se o conteúdo crescer nas próximas fases, priorizar cortes de texto sobre adição de seções.
- Toda transição/animação deve ser sutil o suficiente para não competir com a sensação de serenidade definida em `knowledge/04-voice-and-tone.md`.
- Contraste de texto sobre imagem no hero deve ser validado para acessibilidade (WCAG AA) sem recorrer a overlays escuros pesados que destoem da paleta clara/rosé do Brand Book.
