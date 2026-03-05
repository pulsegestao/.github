<div align="center">

<br/>

<img src="https://img.shields.io/badge/Pulse-Gestão-1E3A8A?style=for-the-badge&logoColor=white" alt="Pulse Gestão" />

<br/><br/>

**Controle de estoque, PDV integrado e inteligência artificial para pequenos negócios brasileiros.**

Simples. Rápido. Feito para o Brasil.

<br/>

![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?style=flat-square&logo=vite&logoColor=white)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-F59E0B?style=flat-square)

</div>

---

## O que é o Pulse Gestão?

O **Pulse Gestão** é uma plataforma SaaS voltada para micro e pequenas empresas brasileiras que precisam de uma solução completa para:

- **Controle de estoque** — visibilidade em tempo real, alertas de reposição e histórico de movimentações
- **PDV integrado** — ponto de venda rápido e direto, sem complicação
- **Inteligência artificial** — sugestões de compra automáticas, detecção de anomalias e previsão de demanda
- **Dashboard de gestão** — métricas do dia, produtos mais vendidos e visão geral do negócio

---

## Repositórios

| Repositório | Descrição | Stack |
|---|---|---|
| [`pulse-frontend`](../pulse-frontend) | Interface web do produto | React 19 + Vite + React Router |
| [`pulse-backend`](../pulse-backend) | API e regras de negócio | — |

---

## Arquitetura geral

```
┌─────────────────────────────────────────────────┐
│                  Cliente (Browser)               │
│                                                  │
│  pulse-frontend                                  │
│  ├── / (Landing Page)                            │
│  ├── /cadastro (Onboarding 2 etapas)             │
│  └── /dashboard (Painel de gestão)               │
└───────────────────┬─────────────────────────────┘
                    │ HTTPS / REST
┌───────────────────▼─────────────────────────────┐
│  pulse-backend                                   │
│  ├── Auth (JWT)                                  │
│  ├── Estoque                                     │
│  ├── Vendas / PDV                                │
│  └── IA / Sugestões                             │
└─────────────────────────────────────────────────┘
```

---

## Começando

### Pré-requisitos

- Node.js `>= 20`
- npm `>= 9`

### Frontend

```bash
git clone https://github.com/pulse-gestao/pulse-frontend
cd pulse-frontend
npm install
npm run dev
# → http://localhost:5173
```

### Backend

```bash
git clone https://github.com/pulse-gestao/pulse-backend
cd pulse-backend
# consulte o README do repositório
```

---

## Produto — telas disponíveis

| Tela | Rota | Status |
|---|---|---|
| Landing page | `/` | ✅ Completo |
| Cadastro (2 etapas) | `/cadastro` | ✅ Completo |
| Dashboard | `/dashboard` | ✅ Interface (mock) |
| Login | `/login` | 🔧 Planejado |
| PDV | `/pdv` | 🔧 Planejado |
| Estoque | `/estoque` | 🔧 Planejado |
| Relatórios | `/relatorios` | 🔧 Planejado |

---

## Design system

O frontend usa um sistema de design próprio, sem CSS framework externo.

| Token | Valor | Uso |
|---|---|---|
| `blue` | `#1E3A8A` | Cor primária, CTAs |
| `green` | `#16A34A` | Sucesso, confirmações |
| `graphite` | `#1F2937` | Texto principal |
| `mid` | `#6B7280` | Texto secundário |

Fontes: **Plus Jakarta Sans** (corpo) · **Syne** (títulos)
Ícones: **Lucide React** — exclusivamente

---

<div align="center">

Feito com cuidado para o pequeno empreendedor brasileiro.

</div>
