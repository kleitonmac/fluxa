````md
# 🚀 Fluxa Financeiro

<p align="center">
  <strong>
    Plataforma SaaS completa para gestão financeira, controle de despesas, vendas,
    carteira internacional, relatórios inteligentes e billing integrado com Stripe.
  </strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-Backend-339933?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Express%205-Framework-000000?style=for-the-badge&logo=express&logoColor=white" />
  <img src="https://img.shields.io/badge/React%2019-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Vite%208-Bundler-646CFF?style=for-the-badge&logo=vite&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Stripe-Payments-635BFF?style=for-the-badge&logo=stripe&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/status-production--ready-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/deploy-Vercel-black?style=flat-square&logo=vercel" />
</p>

---

## 📸 Preview

### Landing Page

<p align="center">
  <img src="docs/screenshots/inicio.png" alt="Fluxa — Landing Page" width="100%" />
</p>

<p align="center">
  <em>Landing page moderna, responsiva e otimizada para SEO.</em>
</p>

---

### Autenticação

<p align="center">
  <img src="docs/screenshots/login.png" alt="Fluxa — Login e Autenticação" width="100%" />
</p>

<p align="center">
  <em>Login com email/senha, Google OAuth e Microsoft OAuth.</em>
</p>

---

### Dashboard Financeiro

<p align="center">
  <img src="docs/screenshots/visaoDesktop.png" alt="Fluxa — Dashboard Financeiro" width="100%" />
</p>

<p align="center">
  <em>Dashboard com KPIs, gráficos, tendências financeiras e insights estratégicos.</em>
</p>

---

## 🎯 Sobre o Projeto

O **Fluxa Financeiro** é uma plataforma SaaS full-stack criada para centralizar a gestão financeira de pessoas e pequenos negócios.

A aplicação permite controlar despesas, vendas, categorias, carteira internacional, relatórios e assinaturas premium em uma experiência moderna, segura e responsiva.

O projeto também possui um **modo demonstração**, ideal para portfólio, permitindo que recrutadores e avaliadores testem o sistema com dados fictícios, sem afetar informações reais.

---

## ✨ Funcionalidades

### 🔐 Autenticação e Segurança

- Cadastro e login com email e senha
- Login com Google OAuth
- Login com Microsoft OAuth
- JWT Access Token
- Refresh Token em cookie HTTP-only
- Recuperação de senha
- Upload de avatar com Cloudinary
- Rate limiting
- Helmet Security
- Validação de origem
- Proteção contra abuso
- API Keys com escopos de acesso

---

### 📊 Dashboard Financeiro

- Cards com KPIs financeiros
- Gasto mensal
- Gasto anual
- Categorias ativas
- Total de lançamentos
- Comparativo com mês anterior
- Gráficos de tendência mensal
- Gráficos de tendência anual
- Distribuição por categoria
- Ranking de maiores despesas
- Insights financeiros

---

### 💰 Gestão de Despesas

- CRUD de despesas
- CRUD de categorias
- Filtros por período
- Filtros por categoria
- Busca por descrição
- Resumo financeiro consolidado
- Exportação CSV

---

### 📈 Módulo Comercial

- Cadastro de vendas
- Gestão de pedidos
- Receita total
- Ticket médio
- Análise por canal de venda
- Resumo comercial

---

### 🌍 Carteira Internacional

- Controle de moedas
- Controle de criptoativos
- Registro de movimentações
- Histórico patrimonial
- Conversão de moedas
- Serviço de cotações

---

### 📄 Relatórios

- Relatórios financeiros processados
- Exportação em PDF
- Exportação em CSV
- Relatório executivo
- Compra avulsa de exportação

---

### 💳 Billing com Stripe

- Checkout Stripe
- Portal do cliente
- Webhook de assinatura
- Planos premium
- Controle automático de status
- Bloqueio de chaves live no modo demo

---

### ⚙️ Painel Administrativo

- Overview geral do SaaS
- Gestão de usuários
- Controle de roles
- Concessão manual de premium
- Bloqueio de contas
- Reset de downloads
- Métricas administrativas

---

## 🛡️ Segurança

O Fluxa implementa práticas de segurança modernas para aplicações SaaS:

| Controle | Implementação |
|---|---|
| Autenticação | JWT + Refresh Token |
| Senhas | Hash com bcrypt |
| Cookies | HTTP-only |
| Headers | Helmet |
| CORS | Allowlist por origem |
| Rate Limit | Proteção contra brute-force |
| SQL Injection | Queries parametrizadas |
| Stripe | Webhook seguro |
| API Keys | Hash SHA-256 e escopos |
| Logs | Telemetria de acesso |

---

## 🔬 Modo Demonstração

O projeto possui um modo seguro para portfólio:

```env
DEMO_MODE=true
````

Com o modo demo ativo:

* Dados reais não são afetados
* Conta demo controlada
* Métricas fictícias
* Admin protegido
* Uploads bloqueados
* Stripe usa apenas modo teste
* Nenhuma cobrança real é criada
* Estado demo pode ser reiniciado automaticamente

---

## 🏗️ Arquitetura do Projeto

```txt
dashboard/
├── backend/
│   ├── api/
│   │   └── index.js
│   ├── migrations/
│   └── src/
│       ├── app.js
│       ├── server.js
│       ├── config/
│       ├── controllers/
│       ├── middleware/
│       ├── models/
│       ├── repositories/
│       ├── routes/
│       ├── services/
│       ├── docs/
│       └── utils/
│
├── frontend/
│   ├── public/
│   └── src/
│       ├── assets/
│       ├── components/
│       ├── contexts/
│       ├── hooks/
│       ├── layouts/
│       ├── pages/
│       ├── routes/
│       ├── services/
│       ├── types/
│       └── utils/
│
└── docs/
    ├── screenshots/
    ├── security-saas-hardening.md
    └── security-sql-injection.md
```

---

## 🛠️ Stack Tecnológica

### Backend

| Tecnologia  | Finalidade             |
| ----------- | ---------------------- |
| Node.js     | Runtime JavaScript     |
| Express 5   | Framework HTTP         |
| PostgreSQL  | Banco de dados         |
| JWT         | Autenticação           |
| bcryptjs    | Hash de senhas         |
| Passport.js | OAuth Google/Microsoft |
| Stripe      | Pagamentos             |
| PDFKit      | Relatórios PDF         |
| Cloudinary  | Upload de imagens      |
| Helmet      | Segurança HTTP         |
| Swagger     | Documentação da API    |

---

### Frontend

| Tecnologia   | Finalidade          |
| ------------ | ------------------- |
| React 19     | Interface           |
| Vite 8       | Build tool          |
| React Router | Rotas SPA           |
| Axios        | Requisições HTTP    |
| Recharts     | Gráficos            |
| ApexCharts   | Visualizações       |
| React Icons  | Ícones              |
| React Select | Selects avançados   |
| CSS Modules  | Estilização modular |

---

## 🚀 Como Rodar Localmente

### Pré-requisitos

* Node.js 18+
* PostgreSQL
* Conta Stripe em modo teste

---

### Instalação

```bash
# Instalar dependências principais
npm install

# Instalar dependências do backend
npm install --prefix backend

# Instalar dependências do frontend
npm install --prefix frontend
```

---

### Variáveis de Ambiente — Backend

Crie o arquivo `backend/.env`:

```env
NODE_ENV=development
DEMO_MODE=true

PORT=3000
FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:3000
DATABASE_URL=postgresql://usuario:senha@host/banco?sslmode=require

ACCESS_TOKEN_SECRET=sua_access_token_secret
REFRESH_TOKEN_SECRET=sua_refresh_token_secret
ACCESS_TOKEN_EXPIRES_IN=15m
REFRESH_TOKEN_EXPIRES_IN=7d
SESSION_SECRET=sua_session_secret

STRIPE_SECRET_KEY=sk_test_xxx
STRIPE_PUBLISHABLE_KEY=pk_test_xxx
STRIPE_WEBHOOK_SECRET=whsec_xxx

PREMIUM_MONTHLY_AMOUNT=999
BASIC_MONTHLY_AMOUNT=999
BLACK_MONTHLY_AMOUNT=2900
EXPORT_SINGLE_AMOUNT=200
```

---

### Variáveis de Ambiente — Frontend

Crie o arquivo `frontend/.env`:

```env
VITE_API_BASE_URL=http://localhost:3000/api
VITE_GOOGLE_CLIENT_ID=seu_google_client_id
```

> Nunca coloque segredos no frontend. Variáveis sensíveis como Stripe Secret, JWT Secret, banco de dados e SMTP devem ficar apenas no backend.

---

### Executar o Projeto

```bash
# Rodar frontend e backend juntos
npm run dev

# Rodar backend separadamente
npm run dev:backend

# Rodar frontend separadamente
npm run dev:frontend
```

---

## 🔗 URLs Locais

| Serviço      | URL                            |
| ------------ | ------------------------------ |
| Frontend     | http://localhost:5173          |
| Backend      | http://localhost:3000          |
| Health Check | http://localhost:3000/health   |
| Swagger Docs | http://localhost:3000/api/docs |

---

## 📡 Principais Endpoints

### Auth

| Método | Endpoint                    | Descrição       |
| ------ | --------------------------- | --------------- |
| POST   | `/api/auth/register`        | Criar conta     |
| POST   | `/api/auth/login`           | Login           |
| POST   | `/api/auth/refresh`         | Renovar token   |
| POST   | `/api/auth/logout`          | Logout          |
| POST   | `/api/auth/forgot-password` | Solicitar reset |
| POST   | `/api/auth/reset-password`  | Redefinir senha |
| POST   | `/api/auth/google`          | Login Google    |
| GET    | `/api/auth/microsoft`       | Login Microsoft |

---

### Financeiro

| Método | Endpoint                      | Descrição         |
| ------ | ----------------------------- | ----------------- |
| GET    | `/api/finance/categories`     | Listar categorias |
| POST   | `/api/finance/categories`     | Criar categoria   |
| PUT    | `/api/finance/categories/:id` | Editar categoria  |
| DELETE | `/api/finance/categories/:id` | Excluir categoria |
| GET    | `/api/finance/expenses`       | Listar despesas   |
| POST   | `/api/finance/expenses`       | Criar despesa     |
| PUT    | `/api/finance/expenses/:id`   | Editar despesa    |
| DELETE | `/api/finance/expenses/:id`   | Excluir despesa   |
| GET    | `/api/finance/summary`        | Resumo financeiro |
| GET    | `/api/finance/export/csv`     | Exportar CSV      |

---

### Vendas

| Método | Endpoint                | Descrição        |
| ------ | ----------------------- | ---------------- |
| GET    | `/api/sales/orders`     | Listar pedidos   |
| POST   | `/api/sales/orders`     | Criar pedido     |
| PUT    | `/api/sales/orders/:id` | Editar pedido    |
| DELETE | `/api/sales/orders/:id` | Excluir pedido   |
| GET    | `/api/sales/summary`    | Resumo de vendas |

---

### Billing

| Método | Endpoint                        | Descrição            |
| ------ | ------------------------------- | -------------------- |
| GET    | `/api/billing/me`               | Status da assinatura |
| POST   | `/api/billing/checkout/premium` | Checkout premium     |
| POST   | `/api/billing/checkout/export`  | Exportação avulsa    |
| POST   | `/api/billing/portal`           | Portal Stripe        |
| POST   | `/api/billing/webhook`          | Webhook Stripe       |

---

### Admin

| Método | Endpoint                             | Descrição        |
| ------ | ------------------------------------ | ---------------- |
| GET    | `/api/admin/overview`                | Métricas gerais  |
| GET    | `/api/admin/users`                   | Listar usuários  |
| PATCH  | `/api/admin/users/:id/role`          | Alterar role     |
| POST   | `/api/admin/users/:id/grant-premium` | Conceder premium |
| POST   | `/api/admin/users/:id/block`         | Bloquear conta   |
| DELETE | `/api/admin/users/:id`               | Excluir conta    |

---

## ☁️ Deploy

O projeto está preparado para deploy na Vercel.

### Recomendações

| Item     | Recomendação                      |
| -------- | --------------------------------- |
| Demo     | Use `DEMO_MODE=true`              |
| Stripe   | Use apenas chaves de teste        |
| Cookies  | Use `COOKIE_SECURE=true` em HTTPS |
| CORS     | Configure origens permitidas      |
| Banco    | Use Neon PostgreSQL               |
| Segredos | Nunca publique `.env`             |

---

## 📌 Diferenciais Técnicos

* Projeto full-stack em produção
* Estrutura SaaS real
* Autenticação robusta
* Billing com Stripe
* Dashboard profissional
* API documentada
* Modo demo seguro
* Arquitetura escalável
* Design responsivo
* Segurança aplicada em múltiplas camadas

---

## 👨‍💻 Desenvolvedor

**Kleiton Santos Macedo**

Desenvolvedor Full Stack com foco em aplicações modernas, escaláveis e seguras utilizando React, Node.js, PostgreSQL e integrações com APIs.

* Portfólio: https://kleitondev.vercel.app
* GitHub: https://github.com/kleitonmac
* Projeto: https://fluxafinancas.vercel.app

---

## 📜 Licença

Este projeto utiliza a licença **MIT** com restrição de uso comercial.

Consulte o arquivo [`LICENSE`](LICENSE) para mais detalhes.

---

<p align="center">
  Desenvolvido com dedicação por <strong>Kleiton Santos Macedo</strong>
</p>
```
