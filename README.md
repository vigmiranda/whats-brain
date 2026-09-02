# Central de Contato WhatsApp — Arquitetura Técnica

Documentação de referência para desenvolvimento de uma **central de contato com clientes via WhatsApp**, com respostas automáticas, campanhas agendadas, agentes de IA, RAG e evolução contínua da base de conhecimento.

## Documento principal

O documento completo está em:

**[docs/arquitetura-central-contato-whatsapp.md](./docs/arquitetura-central-contato-whatsapp.md)**

Ele cobre, entre outros temas:

- Visão, escopo e requisitos (funcionais e não funcionais)
- Arquitetura de referência (diagramas C4 / sequências / ER)
- Integração WhatsApp Cloud API (Meta)
- Automações, roteamento e handoff humano ↔ IA
- Schedules e campanhas promocionais
- Agentes de IA + RAG híbrido
- Pipeline de documentação interna e governança de conhecimento
- Agentes pré-configurados (comercial, suporte, financeiro, etc.)
- Modelo de dados (PostgreSQL / Redis / object storage)
- APIs, eventos e estrutura de monorepo em **Go**
- Comparativo e recomendação de cloud (**GCP Cloud Run** vs **AWS**)
- Segurança, LGPD, observabilidade, custos, roadmap e ADRs

## Stack recomendada (resumo)

| Camada | Escolha |
|--------|---------|
| Backend | Go (modular monolith + workers) |
| Console | Next.js + TypeScript + Tailwind + shadcn/ui |
| Banco | PostgreSQL + pgvector |
| Fila | Pub/Sub (GCP) ou SQS (AWS) |
| Cache | Redis |
| Deploy | Cloud Run (default) ou ECS Fargate |
| LLM | Multi-provider (Vertex / Bedrock / OpenAI) |

## Status do repositório

Este repositório contém a **especificação técnica completa**. A implementação de código (serviços Go, console e IaC) pode partir das Fases 0–2 descritas no documento.

## Como usar este material

1. Leia o documento de arquitetura de ponta a ponta.
2. Valide ADRs (especialmente cloud e modular monolith).
3. Quebre as fases do roadmap em épicos/tarefas.
4. Comece pelo path crítico: webhook Meta → fila → orchestrator → envio.

## Licença

Uso interno / conforme definido pelo time dono do projeto.
