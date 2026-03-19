# .github — Pulse Gestão

Repositório especial da organização **Pulse Gestão** no GitHub.

## O que este repositório contém

| Caminho | Finalidade |
|---|---|
| `profile/README.md` | Perfil público da organização (exibido na página da org no GitHub) |
| `ISSUE_TEMPLATE/` | Templates de issues para os repositórios da org *(a adicionar)* |
| `PULL_REQUEST_TEMPLATE.md` | Template padrão para Pull Requests *(a adicionar)* |
| `CODEOWNERS` | Definição de responsáveis por áreas do código *(a adicionar)* |

## Sobre a organização

A **Pulse Gestão** desenvolve uma plataforma SaaS de gestão para micro e pequenas empresas brasileiras — com PDV, controle de estoque, relatórios, promoções e inteligência de negócios em tempo real.

Repositórios do produto:

- [`pulse-frontend`](https://github.com/pulsegestao/pulse-frontend) — Interface web (React 19 + Vite)
- [`pulse-backend`](https://github.com/pulsegestao/pulse-backend) — API e regras de negócio (Go + Fiber + MongoDB)

## Módulos do produto

### PDV — Ponto de Venda
Registro de vendas com suporte a múltiplas formas de pagamento (dinheiro, débito, crédito, PIX, a prazo). Aplicação de descontos e promoções automáticas no momento da venda.

### Estoque
Gestão completa de produtos com estoque mínimo configurável. Entrada de estoque por lançamento manual ou importação via **NF-e XML**. Alertas automáticos de estoque baixo e produtos parados.

### Promoções
Criação de promoções por produto ou categoria, com vigência por data e hora. Fluxo de configuração em etapas (wizard) com aplicação automática no PDV.

### Relatórios
Painel analítico com dados do período selecionado (semana / mês / ano):
- Resumo consolidado: receita, custo, lucro bruto, margem, ticket médio e variação vs. período anterior
- Evolução do faturamento ao longo do tempo
- Desempenho por produto e por categoria
- Distribuição por forma de pagamento
- Produtos sem giro (estoque parado)
- Estoque abaixo do mínimo
- Recebíveis a prazo em aberto

Exportação de relatórios em **PDF com identidade visual** (por card ou relatório completo).

### Pulsos — Insights Automáticos
Pipeline de inteligência de negócios orientado a eventos:

```
Venda → NATS JetStream → Aggregation Worker → Stats Worker → Insight Worker → MongoDB
```

Detectores ativos: pico de vendas, queda de vendas, estoque baixo/zerado, margem comprimida, produto em alta e análise de promoções (alta performance, baixa adesão, risco de estoque, sugestões).

Os insights têm deduplicação por janela de 24h e expiração automática via TTL.

### Notificações
Sistema de notificações in-app geradas pelos insights, com marcação de leitura e histórico.

## Stack técnica

| Camada | Tecnologia |
|---|---|
| Frontend | React 19, Vite, React Router, lucide-react |
| Backend | Go 1.22, Fiber v2, mongo-driver v2 |
| Banco de dados | MongoDB Atlas |
| Mensageria | NATS JetStream |
| Infra | AWS (backend), Vercel (frontend) |
| Auth | JWT (RS256) |

## Como o perfil da org funciona

O arquivo `profile/README.md` é renderizado automaticamente pelo GitHub na página principal da organização em `github.com/pulsegestao`. Edite esse arquivo para atualizar o que aparece publicamente no perfil.

> Documentação oficial: [Customizing your organization's profile](https://docs.github.com/en/organizations/collaborating-with-groups-in-organizations/customizing-your-organizations-profile)
