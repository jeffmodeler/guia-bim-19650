# Release Notes — Graphite Blueprint

**Projeto**: Guia BIM 19650 — Governança da Informação
**Commit**: [`74e0ded`](https://github.com/jeffmodeler/guia-bim-19650/commit/74e0ded)
**Data**: 2026-04-21
**Arquivo comparado**: [`old/index_21-04.html`](old/index_21-04.html) → [`index.html`](index.html)
**Diff total**: +786 / −112 linhas

---

## Resumo executivo

Esta release é uma **reestilização visual + expansão normativa + acessibilidade**.
Nenhuma funcionalidade foi removida — só adicionada ou refinada.

| Categoria | Mudança principal |
|-----------|-------------------|
| 🎨 Paleta visual | Warm paper + Indigo → **Graphite Blueprint** (azul-pedra + terracota) |
| 🌗 Dark mode | **Novo** — toggle ☀️/🌙 com persistência em `localStorage` |
| 📌 Sticky footer | **Novo** — legenda e notas fixas no rodapé |
| 👤 Author card | **Novo** — botão `JB` com popover (LinkedIn, GitHub) |
| 📚 ISO 19650-3:2025 | **Nova aba** — Kanban e Gantt agora cobrem a Parte 3 |
| 💬 Tooltips normativos | **Novo** — `PHASE_TIPS` descreve cada fase ao passar o mouse |
| 🎯 Indicadores coloridos | **Novo** — `kbtab-dot` distingue abas por cor |
| 🔤 Encoding | UTF-8 limpo (anexo tinha caracteres corrompidos tipo `Ã§`) |

---

## 1. Paleta visual — "Graphite Blueprint"

### Antes (`warm paper`)
```css
--bg:#f7f7f4;           /* creme quente */
--accent:#4338ca;       /* indigo violeta */
--gold:#b08445;         /* dourado editorial */
--ink-warm:#1a1612;     /* preto quente */
```
Referência: papel editorial, tinta indigo, filete dourado.

### Depois (`graphite blueprint`)
```css
--bg:#d8dde3;           /* azul-pedra frio */
--accent:#1e40af;       /* deep blue engenharia */
--gold:#a85332;         /* terracota / cobre */
--ink-warm:#0f172a;     /* grafite azulado */
```
Referência: papel técnico de engenharia, tinta azul-marinho, cobre
como único acento quente.

**Por quê a mudança**: a paleta anterior era mais próxima de livro
editorial; a nova sinaliza "documento técnico normativo" de forma
mais imediata ao público de engenharia/construção.

---

## 2. Dark mode

Agora é possível alternar entre tema claro e escuro via botão ☀️/🌙
no header. Principais características:

- **Persistência**: preferência salva em `localStorage`
  (`bim19650-theme`)
- **Auto-aplicação**: ao recarregar a página, o tema é restaurado antes
  do render (evita flash)
- **Cobre todos os componentes**: cards, modais, código (ex-code),
  tabelas, sticky-footer, header
- **Paleta escura coerente**: azul frio escuro (`#111318`) com cobre
  claro de acento (`#d4a853`)

### Variáveis sobrescritas no modo escuro
```css
body.dark {
  --bg:#111318;
  --surface:#161920;
  --ink:#e8eaf2;
  --accent:#818cf8;       /* indigo mais claro para contraste */
  --gold:#d4a853;         /* cobre amarelado */
}
```

---

## 3. Sticky footer

A legenda "Como ler" (Norma / Exemplo) e as notas de uso agora ficam
**fixas no rodapé** enquanto você scrolla — antes eram estáticas
ao final da página.

```html
<div class="sticky-footer">
  <div class="method-legend">...</div>
  <div class="legend">...</div>
  <div class="footer-bar">...</div>
</div>
```

CSS:
```css
.sticky-footer{
  position:sticky;bottom:0;
  background:rgba(216,221,227,.96);
  backdrop-filter:blur(12px);
  border-top:1px solid var(--border2);
  box-shadow:0 -4px 20px rgba(13,15,26,.07);
}
```

---

## 4. Author card (novo)

Botão circular azul com iniciais **"JB"** no canto do header. Ao
clicar, abre popover com:

- Nome: **Jefferson Borges**
- Papel: **BIM Consultant · ISO 19650**
- Links: **LinkedIn** (`jeffersonborgesdelima`) + **GitHub** (`jeffmodeler/guia-bim-19650`)
- Ícones SVG inline (sem depender de fonts externas como FontAwesome)

---

## 5. ISO 19650-3:2025 — nova aba

A versão anterior cobria apenas **Parte 1 (2021)** e **Parte 2 (2022)**.
Agora o Kanban e o Gantt ganharam a **Parte 3:2025** (fase
operacional de ativos).

### Abas do Kanban — antes
- ISO 19650-1:2021
- ISO 19650-2:2022

### Abas do Kanban — depois
- ISO 19650-1:2021
- ISO 19650-2:2022
- **ISO 19650-3:2025** ← novo

Cada aba agora tem um **dot colorido** (`kbtab-dot`) para
identificação visual rápida:
- 🔵 Azul escuro → Parte 1
- 🟡 Ocre → Parte 2
- 🟢 Verde escuro → Parte 3

---

## 6. Tooltips normativos (PHASE_TIPS)

Um objeto `PHASE_TIPS` no JavaScript agora descreve cada fase ao
passar o mouse:

```js
const PHASE_TIPS = {
  'pre-bep': 'Definição dos requisitos de informação (OIR, AIR, EIR)...',
  'pre-contrato': 'Preparação do BEP e TIDP...',
  // ...
};
```

Cobre todas as fases ISO 19650-1 (`pre-bep`, `pre-contrato`,
`mobilizacao`, `producao`, `encerramento`) e todas as 8 subfases
ISO 19650-2 (`§5.1` a `§5.8`).

**Impacto pedagógico**: o leitor consegue entender o propósito de
cada coluna sem abrir modal — ideal para primeira leitura.

---

## 7. Indicadores de cor nas abas

```css
.kbtab-dot{
  display:inline-block;
  width:8px;height:8px;
  border-radius:2px;
  margin-right:6px;
  opacity:.85;
}
.kbtab.active .kbtab-dot{
  opacity:1;
  filter:brightness(1.6);
}
```

Pequeno quadrado colorido antes do texto da aba. Ajuda a conectar
visualmente a aba com os cards do Kanban (que usam as mesmas cores).

---

## 8. Encoding corrigido

O arquivo anterior (`old/index_21-04.html`) estava salvo em
codificação incorreta, resultando em caracteres como:

```
Ã§Ã£o  → ção
Ã©     → é
â      → —
Â§     → §
```

A versão nova está em **UTF-8 limpo**, sem quebras de caractere.

---

## O que foi preservado (sem mudança)

Para evitar dúvidas, **estes elementos não mudaram**:

- ✅ Google Analytics (`G-PW2N7GF7N7`) — mesma tag, mesmas linhas 4-10
- ✅ Estrutura dos documentos (`DOCS` array) — mesmos 40+ entregáveis
- ✅ Exemplos (`EXAMPLES`) — mesmos conteúdos didáticos
- ✅ Diagramas SVG (`DIAG_SVG`) — 7 diagramas normativos idênticos
- ✅ Fluxos normativos — OIR → AIR → EIR → BEP → IDS → MIDP → AIM → PIR
- ✅ Fontes — Inter + JetBrains Mono + Sora (sem mudança)
- ✅ Comportamento de drag-drop no Kanban

---

## Como ver as mudanças em produção

Se GitHub Pages está ativado no repo:
- URL: https://jeffmodeler.github.io/guia-bim-19650/
- Atualização: geralmente em 1-2 minutos após o push

Para ver versões em paralelo:
- **Atual**: [`index.html`](index.html)
- **Anterior**: [`old/index_21-04.html`](old/index_21-04.html)

---

## Próximos passos possíveis

Ideias para a próxima release (não implementadas):

- [ ] Atalho de teclado para dark mode (ex: `Shift+D`)
- [ ] Preferência automática de tema via `prefers-color-scheme`
- [ ] Versão imprimível (`@media print`) otimizada
- [ ] Exportação de Kanban/Gantt como imagem PNG
- [ ] Filtro de documentos por responsável (contratante / LAP / AP)
- [ ] Aba dedicada para ISO 19650-4:2025 (Troca de informação)
