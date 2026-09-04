# Whats Brain

Central inteligente de contato via WhatsApp: automação, campanhas, agentes de IA com RAG e evolução contínua do conhecimento interno da empresa.

## Documento principal (pitch)

**[docs/pitch-whats-brain.md](./docs/pitch-whats-brain.md)** — o que queremos resolver, como funciona, para quem é, proposta de valor, métricas e roadmap de negócio.

## Documento técnico

**[docs/arquitetura-central-contato-whatsapp.md](./docs/arquitetura-central-contato-whatsapp.md)** — arquitetura completa (Go), modelo de dados, WhatsApp Cloud API, RAG, cloud (GCP/AWS), LGPD, APIs e plano de implementação.

## Leitura recomendada

1. Comece pelo **pitch** (visão de produto).
2. Em seguida a **arquitetura** (como construir).
3. Valide ADRs e quebre as Fases 0–2 em épicos.

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

Especificação de produto + arquitetura técnica. Implementação de código parte das Fases 0–2 do documento de arquitetura.

## Licença

Uso interno / conforme definido pelo time dono do projeto.
