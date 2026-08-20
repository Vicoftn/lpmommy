# Sitemap — Dra. Ana Carolina Nogueira

Base: `strategy/information-architecture.md`, `strategy/conversion-strategy.md`, `knowledge/01-project-goals.md`.

---

## 1. Páginas do projeto

```
/                    → Portfolio (institucional, ponto de entrada padrão)
/paciente            → Página Paciente (conversão para avaliação)
/aluno                → Página Aluno (conversão para turma/formação)
```

Nomenclatura de rotas é uma sugestão inicial — pode ser ajustada na Fase 4 (Desenvolvimento) sem impacto na estratégia, desde que a lógica de três páginas independentes seja preservada.

## 2. Relação entre páginas

- As três páginas são **independentes**, mas conectadas pela mesma narrativa e identidade visual (Decisão 001 do `knowledge/05-decision-log.md`).
- Cada página deve fazer sentido mesmo se acessada como primeira página (tráfego direto, campanha, indicação) — nenhuma depende estruturalmente das outras para cumprir seu objetivo, embora a jornada ideal comece pelo Portfolio.

## 3. Navegação entre páginas

| De | Para | Elemento de navegação |
|---|---|---|
| Portfolio | Paciente | CTA principal "Quero ser paciente" |
| Portfolio | Aluno | CTA secundário "Quero aprender com a Dra." |
| Paciente | Portfolio | Link discreto de marca/logo (retorno, não CTA) |
| Aluno | Portfolio | Link discreto de marca/logo (retorno, não CTA) |
| Paciente | Aluno | Não recomendado como caminho direto — ver seção 4 |
| Aluno | Paciente | Não recomendado como caminho direto — ver seção 4 |

## 4. Por que não cruzar Paciente ↔ Aluno diretamente

Misturar os dois públicos dentro da mesma página de conversão dilui a especificidade da mensagem (paciente busca segurança pessoal; profissional busca método e autoridade). Se necessário, um link discreto no rodapé pode existir ("É profissional da área? Conheça a formação"), mas nunca como CTA de mesmo peso dentro do fluxo principal de conversão.

## 5. Elementos globais (presentes nas três páginas)

- Identidade de marca (logo "ACN", paleta oficial — `brandbook/CORES`, tipografia oficial — `brandbook/TIPOGRAFIA`).
- Rodapé institucional com dados de contato/atendimento e links de retorno ao Portfolio.
- Consistência de tom de voz (`knowledge/04-voice-and-tone.md`) independentemente da página.

## 6. Fora de escopo nesta fase

- Blog, área de conteúdo, loja de produtos, área de aluno logada — não fazem parte do escopo definido em `prompt_inicial.txt` e `knowledge/01-project-goals.md`. Caso surjam, exigem nova decisão registrada em `knowledge/05-decision-log.md` antes de qualquer produção.
