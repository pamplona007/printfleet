# PrintFleet

Plataforma open source para gerenciar farms de impressão 3D de forma (quase) automática:
fila, agendamento automático, inventário de filamento, custo, IA de falha e automação.

O PrintFleet existe porque as ferramentas atuais de mercado (OctoEverywhere, Obico) são
excelentes em acesso remoto e detecção de falha, mas rasas em gestão de farm: pouca ou
nenhuma fila multi-impressora, scheduler, inventário de filamento, custo e políticas de
material.

## Modos de entrega

- **Self-host**: um comando (`docker compose up` ou binário único) sobe o sistema completo,
  sem cloud obrigatório.
- **SaaS multi-tenant**: o mesmo código, com isolamento por tenant desde o schema.

## Estado do projeto

Construção por estágios. O estágio 1 (fundação: monorepo, ADRs, schema, `farmctl`,
docker-compose e CI) está em andamento — ver `docs/adr/` e o histórico de commits.

| Estágio | Escopo |
|---|---|
| 1 | Fundação: monorepo, ADRs, schema, docker-compose, CI, `farmctl` |
| 2 | Registro de impressoras, adapter Moonraker, inventário de filamento |
| 3 | Fila de jobs, políticas, auto-dispatch, preempção, throughput |
| 4 | Dashboard operacional da farm e design system |
| 5 | Self-host em um comando: instalador, backup/restore, docs de operação |
| 6 | Detecção de falha por IA, auto-recovery e alertas |
| 7 | Modo hospedado multi-tenant com edge agent na LAN |
| 8 | Slicing (OrcaSlicer headless), catálogo de produtos, planejamento de lote |

## Stack

Backend em Go (monólito modular, SPA React embutida no binário), React + TypeScript + Vite
no frontend, PostgreSQL, WebSocket próprio para realtime. Decisões detalhadas e alternativas
em `docs/adr/`.

## Licença

AGPLv3 (core) — a licença definitiva é registrada no ADR-002 e pode mudar para open-core
conforme decisão do projeto.

## Contato

Issues e discussions no tracker do workspace.
