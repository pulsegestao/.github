<div align="center">

<br/>

<img src="https://img.shields.io/badge/Pulse-Gestão-0F766E?style=for-the-badge&logoColor=white" alt="Pulse Gestão" />

<br/><br/>

**Gestão completa para pequenos negócios brasileiros — PDV, estoque, relatórios, promoções e inteligência de negócios em tempo real.**

Simples. Rápido. Feito para o Brasil.

<br/>

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Go](https://img.shields.io/badge/Go-1.22-00ADD8?style=flat-square&logo=go&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb&logoColor=white)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-F59E0B?style=flat-square)

</div>

---

## O que é o Pulse Gestão?

O **Pulse Gestão** é uma plataforma SaaS voltada para micro e pequenas empresas brasileiras que precisam de uma solução completa para gerenciar seu negócio:

- **PDV integrado** — ponto de venda rápido com múltiplas formas de pagamento e aplicação automática de promoções
- **Controle de estoque** — visibilidade em tempo real, alertas de reposição, estoque mínimo e entrada por NF-e XML
- **Promoções** — criação de campanhas por produto ou categoria com vigência programada e wizard de configuração
- **Relatórios** — painel analítico completo com exportação em PDF com identidade visual
- **Pulsos (Insights)** — inteligência de negócios em tempo real via pipeline orientado a eventos: picos de venda, queda de receita, margem comprimida, produtos em alta e análise de promoções
- **Notificações** — alertas in-app gerados automaticamente pelos insights

---

## Repositórios

| Repositório | Descrição | Stack |
|---|---|---|
| [`pulse-frontend`](https://github.com/pulsegestao/pulse-frontend) | Interface web do produto | React 19 + Vite + React Router |
| [`pulse-backend`](https://github.com/pulsegestao/pulse-backend) | API, regras de negócio e pipeline de dados | Go 1.22 + Fiber v2 + MongoDB + NATS |

---

## Arquitetura geral

```
┌─────────────────────────────────────────────────┐
│                  Cliente (Browser)               │
│                                                  │
│  pulse-frontend                                  │
│  ├── /dashboard       (KPIs e visão geral)       │
│  ├── /pdv             (Ponto de venda)           │
│  ├── /gerir-estoque   (Gestão de produtos)       │
│  ├── /estoque/entrada (Entrada manual / NF-e)    │
│  ├── /relatorios      (Relatórios + export PDF)  │
│  ├── /promocoes       (Campanhas e descontos)    │
│  └── /pulsos          (Insights automáticos)     │
└───────────────────┬─────────────────────────────┘
                    │ HTTPS / REST
┌───────────────────▼─────────────────────────────┐
│  pulse-backend                                   │
│  ├── Auth (JWT RS256)                            │
│  ├── Produtos / Estoque / Categorias             │
│  ├── Vendas / PDV / Pagamentos                   │
│  ├── Promoções / Descontos                       │
│  ├── Relatórios / Métricas                       │
│  └── Scheduler (jobs periódicos)                 │
└───────────────────┬─────────────────────────────┘
                    │ Pub/Sub
┌───────────────────▼─────────────────────────────┐
│  NATS JetStream — Pipeline de Insights           │
│                                                  │
│  sale.created → Aggregation Worker               │
│             → Stats Worker (MA7/MA30, σ)         │
│             → Insight Worker (6 detectores)      │
│             → MongoDB (insights + TTL)           │
└─────────────────────────────────────────────────┘
```

---

## Começando

### Pré-requisitos

- Node.js `>= 20` e npm `>= 9`
- Go `>= 1.22`
- MongoDB Atlas (ou local)
- NATS Server com JetStream habilitado

### Frontend

```bash
git clone https://github.com/pulsegestao/pulse-frontend
cd pulse-frontend
npm install
npm run dev
# → http://localhost:5173
```

### Backend

```bash
git clone https://github.com/pulsegestao/pulse-backend
cd pulse-backend
# consulte o README do repositório para variáveis de ambiente
go run ./cmd/server
```

---

## Produto — telas disponíveis

| Tela | Rota | Status |
|---|---|---|
| Landing page | `/` | ✅ Completo |
| Cadastro / Onboarding | `/cadastro` | ✅ Completo |
| Login | `/login` | ✅ Completo |
| Dashboard | `/dashboard` | ✅ Completo |
| PDV | `/pdv` | ✅ Completo |
| Gerir estoque | `/gerir-estoque` | ✅ Completo |
| Entrada de estoque | `/estoque/entrada` | ✅ Completo |
| Relatórios + Export PDF | `/relatorios` | ✅ Completo |
| Pulsos (Insights) | `/pulsos` | ✅ Completo |
| Promoções | `/promocoes` | ✅ Completo |
| Notificações | (modal global) | ✅ Completo |

---

## Design system

O frontend usa um sistema de design próprio, sem CSS framework externo.

| Token | Valor | Uso |
|---|---|---|
| `blue` | `#0F766E` | Cor primária, CTAs (teal) |
| `green` | `#16A34A` | Sucesso, confirmações |
| `graphite` | `#1F2937` | Texto principal |
| `mid` | `#6B7280` | Texto secundário |

Fontes: **Plus Jakarta Sans** (corpo) · **Syne** (títulos)
Ícones: **Lucide React** — exclusivamente

---

<div align="center">

Feito com cuidado para o pequeno empreendedor brasileiro.

</div>
