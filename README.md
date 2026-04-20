# ISO 19650 · Governança da Informação
## Guia Visual Interativo

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-live-brightgreen?style=flat-square&logo=github)](https://jeffmodeler.github.io/guia-bim-19650/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)
[![Normas cobertas](https://img.shields.io/badge/Normas-ISO%2019650%20(1%E2%80%935)-orange?style=flat-square)](https://jeffmodeler.github.io/guia-bim-19650/)

> **Artefato de apoio ao estudo e discussão da governança da informação em BIM.**
> Interpretativo e didático — não substitui a leitura das normas aplicáveis ao contexto.

🔗 **[Acessar o guia](https://jeffmodeler.github.io/guia-bim-19650/)**

---

## O que é este projeto

Um **guia visual interativo** em HTML puro — sem servidor, sem banco de dados — que organiza e conecta os documentos, processos e fluxos da **ISO 19650** de forma navegável e com exemplos aplicados.

Transforma uma norma técnica densa em uma experiência de consulta e aprendizagem.

---

## Por que a ISO 19650 importa

A **ISO 19650** é a principal norma internacional para **gestão da informação usando BIM**. Adotada no Brasil como **ABNT NBR ISO 19650**, ela define:

- Como formular e comunicar requisitos de informação
- Como planejar, produzir, revisar e entregar informação em BIM
- Como operar ambientes comuns de dados (CDE)
- Como estruturar contratos e responsabilidades de informação

Sem ISO 19650, projetos BIM frequentemente produzem **modelos sem governança** — ricos em geometria, pobres em dados utilizáveis para operação e gestão do ativo.

---

## Normas cobertas

### ISO 19650-1:2021 — Conceitos e princípios

| Doc | Nome | Descrição |
|-----|------|-----------|
| **OIR** | Organizational Information Requirements | Requisitos estratégicos permanentes da organização |
| **AIR** | Asset Information Requirements | O que é necessário para operar e manter o ativo |
| **EIR** | Exchange Information Requirements | Base contratual do que será exigido das equipes |
| **BEP** | BIM Execution Plan | Resposta da equipe ao EIR — pré-contratual e definitivo |
| **IDS** | Information Delivery Specification | Verificação formal automática dos requisitos |
| **TIDP** | Task Information Delivery Plan | Plano de entrega por disciplina |
| **MIDP** | Master Information Delivery Plan | Consolidação geral das entregas |
| **AIM** | Asset Information Model | Modelo final para operação do ativo |
| **PIR** | Post-Implementation Review | Avaliação após entrega |

### ABNT NBR ISO 19650-2:2022 — Fase de entrega

27 processos cobrindo §5.1 a §5.8:

| Seção | Processo |
|-------|----------|
| **§5.1** | Determinação das necessidades — 8 documentos (GRI → PRI) |
| **§5.2** | Convite à licitação — EIR para licitação |
| **§5.3** | Resposta à licitação — BEP pré-contratual, competência, mobilização |
| **§5.4** | Contratação — BEP definitivo, RACI, TIDP, MIDP, contratos |
| **§5.5** | Mobilização — recursos, TI, testes de workflow |
| **§5.6** | Produção colaborativa — geração, verificação, revisão e aprovação |
| **§5.7** | Entrega do modelo de informação — autorização e aceite |
| **§5.8** | Encerramento — arquivo e lições aprendidas |

### ISO 19650-3:2025 — Fase operacional de ativos

Processos de gestão da informação para operação e manutenção do ativo construído (AIM). Cobre o ciclo completo pós-entrega: §5.1 Gatilho → §5.8 Encerramento da fase operacional.

### ISO 19650-4:2025 — Troca de informação

Especifica como a informação deve ser trocada entre partes ao longo do ciclo de vida. Implementado como fluxograma SVG interativo baseado nas Figuras 1 e 3 da norma, com grade de critérios §7.1–§7.7.

### ISO 19650-5:2025 — Abordagem voltada à segurança

Requisitos de segurança para gestão de informação sensível de ativos construídos. Cobre avaliação de risco, plano de segurança, acordos e triagem de partes envolvidas.

---

## Funcionalidades

### 📋 Kanban de dependências
- Documentos organizados por fase do ciclo informacional
- Drag-and-drop entre fases
- Cards com acrônimo, norma, dependências coloridas e responsável
- Botão "Ver detalhes" com exemplos aplicados por documento
- Alternância entre ISO 19650-1, -2, -3, -4 e -5

### 📊 Gantt de desenvolvimento
- Cronograma com lógica de predecessoras reais (FS/SS)
- 20 períodos cobrindo o ciclo completo de um empreendimento
- Três visões: ISO-1 isolada · ISO-2 isolada · visão integrada com agrupamento temático

### 📖 Drawer normativo `?`
- **Fluxos normativos** — cadeia OIR→PIR→AIR→EIR→BEP→IDS→MIDP→AIM com pills clicáveis
- **Diagramas da norma** — 7 figuras da ABNT NBR ISO 19650-1:2021 em tamanho real

### 🔍 Modais de detalhe por documento
- Badge de parte normativa (ISO-1 / ISO-2 / ISO-3 / ISO-4 / ISO-5 / IDS)
- Caixa "Apoia qual decisão?" — a questão de governança que o documento resolve
- Exemplos clicáveis: tabelas, blocos de código e narrativas

### 🏷️ Sistema de badges
| Badge | Significado |
|-------|-------------|
| `Norma` | Conceito normativo da ISO 19650 |
| `Exemplo` | Ilustração aplicada — caráter didático |
| `Implementação` | Referência de cenário específico |

---

## Arquitetura interna

O projeto é um **single-file HTML app** — toda a lógica, dados e estilos estão em `index.html`.

```
index.html
├── <style>          CSS com variáveis (design tokens)
├── PHASES{}         Mapeamento fase → cor por seção normativa
├── EXAMPLES{}       Exemplos por documento (tabela / código / narrativa)
├── DOCS[]           Array principal — todos os documentos das 5 partes
├── buildKanban()    Renderiza o board Kanban (ISO-1, -2, -3)
├── buildGantt()     Renderiza o Gantt com predecessoras
├── buildFluxoP4()   Renderiza o fluxograma SVG interativo da ISO 19650-4
├── buildFluxoP5()   Renderiza o Kanban da ISO 19650-5
├── buildChain()     Renderiza a cadeia síntese no header
├── openModal()      Abre modal de detalhe de documento
└── openExample()    Abre pop-up de exemplo
```

**Padrão de extensão:** novas seções normativas adicionam entradas a `DOCS[]` e `EXAMPLES{}`, e uma nova função `build*` invocada via `setKbTab()`.

---

## Cadeia síntese

```
OIR ──→ AIR ──→ EIR ──→ BEP ──→ IDS ──→ MIDP ──→ AIM ──→ PIR
 ↑                ↑                                        ↓
Permanente    Contratual                              Realimenta OIR
```

A cadeia começa nos **requisitos organizacionais** (OIR), passa pelos **requisitos contratuais** (EIR), estrutura a **produção** (BEP + IDS + MIDP) e culmina no **modelo operacional do ativo** (AIM) — avaliado pelo PIR para realimentar o próximo ciclo.

---

## Como usar

1. Clone ou baixe o repositório
2. Abra `index.html` no navegador — sem servidor necessário
3. Use os tabs **Kanban** / **Gantt** para navegar
4. Clique em qualquer card para ver detalhes e exemplos
5. Use o botão **`?`** no header para fluxos e diagramas da norma

> **Nota de cache:** após atualizar o arquivo, faça hard refresh (`Ctrl+Shift+R` / `Cmd+Shift+R`) ou desative o cache no DevTools para garantir que o navegador carregue a versão mais recente.

---

## Tecnologia

- **HTML5 + CSS3 + JavaScript** puro — zero dependências
- Fontes: [Inter](https://fonts.google.com/specimen/Inter) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts
- Compatível com qualquer navegador moderno
- Funciona offline após o primeiro carregamento

---

## Contributing

Sugestões são bem-vindas. Formas de contribuir:

- **Erros normativos:** abra uma [Issue](https://github.com/jeffmodeler/guia-bim-19650/issues) descrevendo o ponto da norma e a seção afetada
- **Novos exemplos:** sugestões de exemplos aplicados para documentos existentes
- **Novas partes da norma:** seguir o padrão — adicionar entradas em `DOCS[]` + `EXAMPLES{}` + nova função `build*()`

> Os exemplos têm **caráter ilustrativo**. Expressões como "deve" e "obrigatório" referem-se ao cenário descrito, não à norma universal. Validação final: norma aplicável ao contexto.

---

## Notas editoriais

- Os exemplos têm **caráter ilustrativo**
- Expressões como "deve" e "obrigatório" nos exemplos referem-se ao **cenário descrito**, não à norma universal
- Validação final: consulte sempre a norma aplicável ao seu contexto

---

*Desenvolvido como material de apoio ao estudo e discussão da governança da informação.*
*ISO 19650-1:2021 · ABNT NBR ISO 19650-2:2022 · ISO 19650-3:2025 · ISO 19650-4:2025 · ISO 19650-5:2025*
