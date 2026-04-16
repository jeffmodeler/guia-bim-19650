# ISO 19650 · Governança da Informação
## Guia Visual Interativo

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

---

## Funcionalidades

### 📋 Kanban de dependências
- Documentos organizados por fase do ciclo informacional
- Drag-and-drop entre fases
- Cards com acrônimo, norma, dependências coloridas e responsável
- Botão "Ver detalhes" com exemplos aplicados por documento
- Alternância entre **ISO 19650-1:2021** e **ISO 19650-2:2022**

### 📊 Gantt de desenvolvimento
- Cronograma com lógica de predecessoras reais (FS/SS)
- 20 períodos cobrindo o ciclo completo de um empreendimento
- Três visões: ISO-1 isolada · ISO-2 isolada · **visão integrada** com agrupamento temático

### 📖 Drawer normativo `?`
- **Fluxos normativos** — cadeia OIR→PIR→AIR→EIR→BEP→IDS→MIDP→AIM com pills clicáveis
- **Diagramas da norma** — 7 figuras oficiais da ABNT NBR ISO 19650-1:2021 em tamanho real

### 🔍 Modais de detalhe por documento
- Badge de parte normativa (ISO-1 / ISO-2 / IDS)
- Caixa "Apoia qual decisão?" — a questão de governança que o documento resolve
- Exemplos clicáveis: tabelas, blocos de código e narrativas

### 🏷️ Sistema de badges
| Badge | Significado |
|-------|-------------|
| `Norma` | Conceito normativo da ISO 19650 |
| `Exemplo` | Ilustração aplicada — caráter didático |
| `Implementação` | Referência de cenário específico |

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

---

## Tecnologia

- **HTML5 + CSS3 + JavaScript** puro — zero dependências
- Fontes: [Inter](https://fonts.google.com/specimen/Inter) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts
- Compatível com qualquer navegador moderno
- Funciona offline após o primeiro carregamento

---

## Notas editoriais

- Os exemplos têm **caráter ilustrativo**
- Expressões como "deve" e "obrigatório" nos exemplos referem-se ao **cenário descrito**, não à norma universal
- Validação final: consulte sempre a norma aplicável ao seu contexto

---

*Desenvolvido como material de apoio ao estudo e discussão da governança da informação — ISO 19650-1:2021 · ABNT NBR ISO 19650-2:2022*
