# Changelog

Todas as alterações relevantes deste projeto estão documentadas aqui.
Formato baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/).

---

## [Não publicado]

### Adicionado
- ISO 19650-4:2025 — Troca de informação: fluxo SVG interativo baseado nas Figuras 1 e 3 da norma + grade de critérios §7.1–§7.7
- ISO 19650-5:2025 — Abordagem voltada à segurança: Kanban com processos §4–§6 e modais de detalhe
- Banners informativos centralizados por seção normativa
- Exemplos detalhados em todos os modais de popup

---

## [2.0.0] — 2025-04

### Adicionado
- **ISO 19650-3:2025** — Fase operacional de ativos: bloco Kanban completo com 8 colunas (§5.1–§5.8), cards, modais e integração com Gantt
- Melhorias visuais nos SVG: gradientes, sombras, labels de atores e legendas
- Banners informativos centralizados
- Exemplos aprofundados em todos os modais

### Corrigido
- Problema de cache do browser diagnosticado e documentado (não era bug de dados)

---

## [1.1.0] — 2025-03

### Adicionado
- **ISO 19650-2:2022** — Fase de entrega completa: 27 processos §5.1 a §5.8
- Kanban com 8 colunas para a Parte 2
- Fluxos normativos no drawer `?` cobrindo §5.1–§5.8
- Gantt integrado ISO-1 + ISO-2 com visão consolidada
- Modais com campo "Apoia qual decisão?" em cada documento

---

## [1.0.0] — 2025-01

### Adicionado
- **ISO 19650-1:2021** — Conceitos e princípios: cadeia OIR→AIR→EIR→BEP→IDS→MIDP→AIM→PIR
- Kanban com drag-and-drop entre fases
- Gantt com lógica de predecessoras (FS/SS) — 20 períodos
- Drawer `?` com fluxos normativos e 7 diagramas da norma
- Modais de detalhe com exemplos clicáveis (tabelas, código, narrativas)
- Sistema de badges: Norma / Exemplo / Implementação
- Zero dependências — HTML + CSS + JS puro
