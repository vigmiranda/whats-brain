# Whats Brain — Pitch do Projeto

**Documento principal de produto**  
**Produto:** Whats Brain  
**Canal:** WhatsApp Business  
**Versão:** 1.0

> Documento irmão (engenharia): [Arquitetura técnica completa](./arquitetura-central-contato-whatsapp.md)

---

## 1. Em uma frase

**Whats Brain** é a central inteligente de contato via WhatsApp que combina automação, campanhas e agentes de IA com conhecimento interno da empresa — para responder mais rápido, vender melhor e escalar o atendimento sem perder o toque humano.

---

## 2. O problema que queremos resolver

Empresas brasileiras (e latam) concentram grande parte da conversa com o cliente no WhatsApp. Na prática, isso gera três dores recorrentes:

### 2.1 Atendimento que não escala

- Filas longas, horário comercial limitado e dependência de pessoas para perguntas repetitivas.
- Tempo de primeira resposta alto → abandono, reclamações e perda de venda.

### 2.2 Bots engessados × conhecimento disperso

- Menus e FAQs fixas quebram na primeira pergunta fora do script.
- O conhecimento real da empresa está em PDFs, Notion, Confluence, planilhas e na cabeça do time.
- Quando o produto muda, o bot continua desatualizado.

### 2.3 Marketing e operação desconectados

- Promoções no WhatsApp sem governança (opt-in, frequência, reputação do número).
- Campanhas sem atribuição clara.
- Inbox, CRM e base de conhecimento em silos — o cliente repete a mesma história a cada transferência.

**Resultado:** custo alto por conversa, qualidade inconsistente, risco de banimento do número e pouca inteligência acumulada sobre o que o cliente realmente pergunta.

---

## 3. A solução

Uma plataforma **multi-tenant** que transforma o WhatsApp em um canal de operação completo:

| Capacidade | O que entrega |
|---|---|
| **Inbox unificado** | Humanos, automações e IA no mesmo fio de conversa |
| **Respostas automáticas** | Saudação, menu, horário, regras e FAQ determinística |
| **Agentes de IA + RAG** | Respostas ancoradas na documentação interna da empresa |
| **Agentes pré-configurados** | Comercial, suporte, financeiro, onboarding — cada um com persona, tools e base própria |
| **Campanhas agendadas** | Promoções, lembretes e reativação com opt-in, throttle e métricas |
| **Knowledge loop** | Feedback e gaps de conversa viram melhoria da documentação |
| **Handoff inteligente** | Quando a confiança cai, a conversa sobe para um humano — sem o cliente recomeçar |

Não é “mais um chatbot”. É uma **central de contato** com cérebro (conhecimento) e braço operacional (automação + campanhas + humanos).

---

## 4. Como isso irá funcionar (visão do cliente)

```text
Cliente no WhatsApp
        │
        ▼
  Whats Brain (roteador)
        │
        ├─► Automação (menu, horário, FAQ)
        ├─► Agente de IA especializado (RAG + tools)
        └─► Fila humana (inbox do time)
                │
                ▼
     Feedback / correção
                │
                ▼
     Base de conhecimento atualizada
                │
                ▼
     Próximas respostas melhores
```

### 4.1 Jornada típica

1. **Cliente manda mensagem** no número da empresa.
2. **Whats Brain** identifica a organização (tenant), o contato e o contexto da conversa.
3. Se for primeira interação no horário comercial → **menu** (Comercial / Suporte / Financeiro).
4. O cliente escolhe ou descreve o problema em linguagem natural.
5. O **agente certo** responde com base nos documentos aprovados da empresa (RAG).
6. Se precisar consultar pedido, abrir ticket ou anotar no CRM → usa **tools** autorizadas.
7. Se a confiança for baixa ou o cliente pedir → **transfere para humano** com o histórico completo.
8. Feedback 👍/👎 e correções humanas alimentam o **backlog de conhecimento**.

### 4.2 Campanhas e promoções

1. Time monta audiência (segmento + opt-in).
2. Escolhe template aprovado pela Meta.
3. Agenda envio (único ou recorrente).
4. Plataforma envia com rate limit, respeitando reputação do número.
5. Relatório de entrega, leitura, resposta e conversão.

### 4.3 Evolução do “cérebro”

Documentação deixa de ser arquivo morto:

- upload / sync (Markdown, PDF, Notion, Confluence, Drive)
- versionamento e aprovação
- indexação automática para os agentes
- detecção de perguntas sem boa resposta → sugestão de novos docs

Quanto mais a operação usa, **mais inteligente e alinhada** a plataforma fica — sem treinar um modelo próprio do zero.

---

## 5. Para quem é

### Personas principais

| Persona | Dor | Valor Whats Brain |
|---|---|---|
| **Fundador / Head de Ops** | Atendimento caro e caótico no Whats | Escala com qualidade e custo previsível |
| **Supervisor de CS** | Filas, SLA e inconsistência entre agentes | Roteamento, handoff e métricas claras |
| **Time comercial** | Lead esfria no Whats | Agente comercial + campanhas com governança |
| **Knowledge / Produto** | Docs desatualizados | Pipeline de publicação → impacto direto no bot |
| **TI / Eng** | Integrações frágeis e risco LGPD/Meta | Arquitetura sólida (Go, multi-tenant, auditoria) |

### Perfis de empresa (ICP inicial)

- Empresas que **já atendem e vendem pelo WhatsApp**
- Operações com **5 a 200 atendentes** (ou aspirando a isso sem contratar na mesma proporção)
- Negócios com **catálogo, políticas e runbooks** que mudam com frequência
- Times que precisam de **multi-unidade / multi-marca** (multi-tenant)

---

## 6. Proposta de valor

### Para o negócio

- **Mais conversas resolvidas sem humano**, sem parecer robô genérico.
- **Menor tempo de resposta** e menos abandono.
- **Campanhas no Whats** com menos risco de spam/ban.
- **Conhecimento institucional** vira ativo operacional, não só wiki.

### Para o cliente final

- Resposta rápida, no canal que ele já usa.
- Menos “digite 1”, mais conversa útil.
- Continuidade ao falar com humano (histórico preservado).

### Diferenciais

1. **IA groundada** em docs versionados (RAG), não alucinação solta.
2. **Agentes especializados** pré-configurados, não um bot único genérico.
3. **Ciclo de aprendizado operacional** (feedback → documentação → melhor resposta).
4. **Automação + IA + humano** no mesmo produto, com políticas e compliance (LGPD / Meta).
5. **Base técnica em Go**, event-driven, multi-tenant — pronta para escala SaaS.

---

## 7. O que o produto entrega (escopo de valor)

### MVP (primeiro valor tangível)

- Número WhatsApp conectado (Cloud API)
- Inbox web para o time
- Automações básicas (saudação, menu, horário)
- 1 agente de IA com RAG sobre FAQ/docs reais
- Handoff humano ↔ IA
- Campanha agendada com template
- Isolamento multi-tenant desde o início

### Evolução natural (v1)

- Catálogo de agentes (comercial, suporte, financeiro, onboarding)
- Workflow de aprovação de conhecimento
- Detecção de gaps (“perguntas que a IA não sabe”)
- Segmentação e A/B de campanhas
- Analytics (contenção da IA, CSAT, custo por conversa resolvida)
- Integrações CRM/ERP via tools e webhooks

---

## 8. Como medimos sucesso

| Métrica | Direção | Alvo sugerido (após ramp-up) |
|---|---|---|
| Tempo de primeira resposta (bot/IA) | ↓ | P50 < 5s |
| Taxa de resolução sem humano | ↑ | ≥ 40% |
| CSAT nas conversas com IA | ↑ | ≥ 4.2 / 5 |
| Taxa de handoff por baixa confiança | monitorar | saudável e explicável |
| Tempo doc publicado → disponível no agente | ↓ | ≤ 7 dias (ideal: horas) |
| Opt-out / block rate em campanhas | ↓ | dentro de limiares Meta |
| Custo por conversa resolvida | ↓ | previsível por tenant |

---

## 9. Modelo de negócio (direção)

Hipótese inicial (ajustável):

- **SaaS multi-tenant** por organização
- Cobrança por **assentos** (agentes humanos) + **uso** (mensagens / tokens de IA) ou faixas de conversas
- Add-ons: números extras, campanhas avançadas, conectores de conhecimento, SLA enterprise

O desenho técnico (multi-tenant, budgets de LLM por tenant, auditoria) já antecipa esse modelo.

---

## 10. Por que agora

- WhatsApp é o canal dominante de conversa B2C/B2B leve no Brasil.
- LLMs + RAG tornaram viável um atendimento “com conhecimento de verdade”, sem fine-tune caro.
- A Meta exige (e pune) má governança de marketing — quem tiver plataforma correta ganha vantagem.
- Times querem **menos ferramenta fragmentada** e mais operação em um só lugar.

---

## 11. O que não somos (de propósito)

- Não somos só disparador de mensagem em massa.
- Não somos um LLM genérico colado no WhatsApp sem governança.
- Não dependemos de APIs não oficiais / risco de ban permanente.
- Não começamos como “plataforma omnichannel infinita” — **Whats primeiro**, arquitetura preparada para expandir.

---

## 12. Narrativa de demo (2 minutos)

1. Cliente pergunta no Whats: *“Qual o prazo de troca do produto X?”*
2. Agente de Suporte responde citando a política interna publicada ontem.
3. Cliente: *“E o status do pedido 12345?”* → tool consulta o ERP → resposta objetiva.
4. Cliente: *“Quero falar com alguém”* → handoff instantâneo; humano vê o transcript.
5. Supervisor marca 👎 numa resposta fraca → abre draft de doc → publica → próxima pergunta similar já sai certa.
6. No painel, agenda campanha de reativação para opt-ins do segmento “carrinho abandonado”.

**Punchline da demo:** *o WhatsApp da empresa passa a ter memória, especialização e operação — não só chat.*

---

## 13. Roadmap em linguagem de negócio

| Fase | Entrega perceptível |
|---|---|
| **0 – Ligar o canal** | Mensagens entrando/saindo com inbox mínimo |
| **1 – Aliviar a fila** | Menu, horário, FAQ e handoff humano |
| **2 – Colocar o cérebro** | IA com RAG + feedback |
| **3 – Crescer receita** | Campanhas com governança e métricas |
| **4 – Especializar** | Multi-agentes + knowledge ops |
| **5 – Endurecer** | Escala, compliance avançado, integrações profundas |

Detalhamento técnico de cada fase: ver [documento de arquitetura](./arquitetura-central-contato-whatsapp.md).

---

## 14. Pedido / próximo passo

Validar este pitch com stakeholders e, em seguida:

1. Congelar ICP e métricas do piloto.
2. Escolher cloud default (recomendação técnica: GCP Cloud Run) e WABA de teste.
3. Quebrar Fases 0–2 em épicos de implementação.
4. Rodar piloto com **um número**, **um agente Concierge/Suporte** e uma **KB real pequena**.

---

## 15. Resumo executivo

| | |
|---|---|
| **Nome** | Whats Brain |
| **Problema** | WhatsApp central no relacionamento, mas operação manual, bot frágil e conhecimento disperso |
| **Solução** | Central de contato com automação, IA+RAG, campanhas e humanos no mesmo fluxo |
| **Como funciona** | Mensagem → roteamento → automação/IA especializada/humano → feedback → docs melhores |
| **Diferencial** | Grounding em conhecimento versionado + multi-agentes + loop de evolução + base SaaS multi-tenant |
| **Stack** | Go no core, WhatsApp Cloud API, Postgres/pgvector, console web |
| **Doc técnico** | [arquitetura-central-contato-whatsapp.md](./arquitetura-central-contato-whatsapp.md) |
