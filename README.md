## 🎯 O que é o Fluxa?

O **Fluxa** é um SaaS financeiro full-stack desenvolvido para dar ao usuário total controle sobre suas finanças pessoais ou empresariais. A plataforma consolida em um único painel:

- **Visão geral financeira** — resumo em tempo real de gastos, receitas e tendências.
- **Gestão de despesas** — categorize, filtre e acompanhe cada centavo gasto.
- **Módulo comercial** — registre vendas, acompanhe receita por canal e ticket médio.
- **Carteira internacional** — gerencie moedas e criptoativos com cotações atualizadas.
- **Relatórios inteligentes** — exporte PDFs e CSVs prontos para análise.
- **Planos e billing** — assinaturas gerenciadas via Stripe com checkout seguro.
- **Painel administrativo** — gestão de usuários, planos, métricas e permissões.

> 💡 **Preparado para portfólio** — o projeto inclui um modo DEMO seguro com dados fictícios, permitindo que recrutadores e avaliadores testem a plataforma sem riscos.
<p align="center">
  <img src="docs/screenshots/inicio.png" alt="Fluxa — Landing Page" width="100%" />
  <br />
  <em>Landing page moderna e otimizada para SEO com foco em experiência do usuário</em>
</p>

---

## ✨ Funcionalidades

### 🔐 Autenticação & Segurança
| Recurso | Descrição |
|---------|-----------|
| Login por email/senha | Cadastro e login tradicionais com bcrypt |
| Google OAuth | Login social com um clique |
| Microsoft OAuth | Login corporativo via Passport.js |
| JWT + Refresh Token | Access token de curta duração + refresh token em cookie HTTP-only |
| Recuperação de senha | Fluxo completo de forgot/reset password por email |
| Upload de avatar | Imagem de perfil via Cloudinary |
| Rate limiting | Proteção contra brute-force em rotas de autenticação |
| Validação de origem | Middleware de Origin/Referer guard |
| API Keys | Credenciais `fxk_*` com escopos `read`/`write` para integrações |

<p align="center">
  <img src="docs/screenshots/login.png" alt="Fluxa — Login e Autenticação" width="100%" />
  <br />
  <em>Tela de login com autenticação por email/senha, Google e Microsoft</em>
</p>


---


### 📊 Dashboard Financeiro
| Recurso | Descrição |
|---------|-----------|
| KPIs em cards | Gasto do mês, gasto anual, categorias ativas, lançamentos |
| Comparativo mensal | Variação percentual vs. mês anterior |
| Gráfico de tendência mensal | Fluxo de despesas no período filtrado (Recharts) |
| Gráfico de tendência anual | Totais por ano com linha de média |
| Distribuição por categoria | Gráfico donut com proporções por categoria |
| Filtros interativos | Categoria, ano e mês com atualização em tempo real |
| Insights e movimentações | Ticket médio, top categorias e maior despesa |

<p align="center">
  <img src="docs/screenshots/visaoDesktop.png" alt="Fluxa — Dashboard Financeiro" width="100%" />
  <br />
  <em>Dashboard principal com KPIs, gráficos de tendência mensal/anual, distribuição por categoria e insights</em>
</p>


### 💰 Gestão de Despesas
| Recurso | Descrição |
|---------|-----------|
| CRUD de categorias | Crie, edite e exclua categorias personalizadas |
| CRUD de despesas | Registre despesas com valor, data, categoria e descrição |
| Filtros e busca | Filtre por período, categoria e texto |
| Resumo financeiro | Sumário consolidado via `/api/finance/summary` |

### 📈 Módulo Comercial (Vendas)
| Recurso | Descrição |
|---------|-----------|
| Gestão de pedidos | CRUD completo de orders com status e valores |
| Resumo de vendas | Receita total, ticket médio e métricas por canal |
| Análise por canal | Identifique canais de venda mais lucrativos |

### 🌍 Carteira Internacional
| Recurso | Descrição |
|---------|-----------|
| Gestão de ativos | Moedas fiduciárias e criptoativos |
| Movimentações | Registro de entradas e saídas com histórico |
| Evolução patrimonial | Acompanhe crescimento do portfólio ao longo do tempo |
| Cotações atualizadas | Market rates service para conversão de moedas |

<p align="center">
  <img src="docs/screenshots/carteira.png" alt="Fluxa — Dashboard Financeiro" width="100%" />
  <br />
  <em>Painel de controle de carteira internacional</em>
</p>

### 📄 Relatórios & Exportação
| Recurso | Descrição |
|---------|-----------|
| Relatório processado | Resumo financeiro consolidado via API |
| Exportação CSV | Dados financeiros em planilha |
| Exportação PDF | Relatório formatado via PDFKit |
| Exportação avulsa | Compra unitária de exportação via Stripe (R$ 2,00) |

<p align="center">
  <img src="docs/screenshots/relatorio.png" alt="Fluxa — Dashboard Financeiro" width="100%" />
  <br />
  <em>Relatório de exportação de dados financeiros</em>
</p>

### 💳 Billing (Stripe)
| Plano | Preço |
|-------|-------|
| Basic | R$ 9,99/mês |
| Premium | R$ 9,99/mês |
| Black | R$ 29,00/mês |
| Exportação avulsa | R$ 2,00/unidade |

- Checkout via Stripe Sessions
- Portal de gerenciamento de assinatura
- Webhook para sincronização de status
- Proteção contra chaves live em modo demo

### 🔔 Notificações
- Central de notificações em tempo real
- Alertas financeiros e de sistema

### ⚙️ Painel Admin
| Recurso | Descrição |
|---------|-----------|
| Overview | Métricas gerais do SaaS |
| Gestão de usuários | Lista, busca e filtro de todos os usuários |
| Controle de papéis | Alteração de role (user/admin) |
| Premium manual | Grant/remove premium para usuários |
| Bloqueio de conta | Block/unblock de contas |
| Reset de downloads | Reiniciar contadores de exportação |

<p align="center">
  <img src="docs/screenshots/admin.png" alt="Fluxa — Dashboard Financeiro" width="100%" />
  <br />
  <em>Painel administrativo</em>
</p>
---

## 🛡️ Segurança

O Fluxa implementa múltiplas camadas de segurança seguindo o checklist OWASP:

| Controle | Implementação |
|----------|---------------|
| Autenticação | JWT assinado + refresh token em cookie HTTP-only |
| Rate limiting | Por IP em auth + por usuário autenticado |
| Headers seguros | Helmet com CSP e headers de segurança |
| CORS | Allowlist configurável por origem |
| Proteção contra abuso | Detecção de payload suspeito + bloqueio temporário por IP |
| Validação de payload | Middleware `requireAllowedBodyFields` em todas as rotas |
| Validação de dados | UUID, valores monetários, textos e datas |
| Proteção Stripe | Bloqueio de chaves `sk_live_` em modo demo |
| Isolamento DEMO | Dados ficticios separados dos dados reais |
| API Keys | Hash SHA-256, escopos, revogação — admin bloqueado para API key |
| SQL Injection | Queries parametrizadas (documentado em `docs/security-sql-injection.md`) |
| Telemetria | Logs de acesso com método, path, status, duração, IP e usuário |

> 📖 Documentação completa de hardening em [`docs/security-saas-hardening.md`](docs/security-saas-hardening.md)

---

## 🔬 Modo DEMO (Portfólio)

O Fluxa possui um ambiente DEMO isolado, ideal para demonstrações em portfólio:

```env
DEMO_MODE=true
```

**O que acontece com `DEMO_MODE=true`:**

✅ Conta `demo@fluxa.com` autenticada por identidade controlada  
✅ Dados fictícios separados dos dados reais  
✅ Estado demo reinicia no login, logout e periodicamente  
✅ Painel admin retorna apenas métricas e usuários fictícios  
✅ Ações administrativas reais bloqueadas  
✅ Upload de avatar bloqueado  
✅ Respostas da API sanitizadas  
✅ Badge `Modo Demonstração` exibido no dashboard  
✅ Stripe opera apenas com chaves de teste (`sk_test_*`)  
✅ Checkout retorna sessão fake `cs_test_demo_*`  
✅ Nenhuma cobrança real é criada  

---

## 🏗️ Arquitetura

```
dashboard/
├── backend/
│   ├── api/index.js                    # Entry point (Vercel)
│   ├── migrations/                     # Database migrations
│   └── src/
│       ├── app.js                      # Express app setup
│       ├── server.js                   # Server bootstrap
│       ├── config/
│       │   ├── db.js                   # PostgreSQL connection pool
│       │   ├── env.js                  # Environment validation
│       │   └── passport.js             # OAuth strategies
│       ├── controllers/                # Request handlers
│       ├── middleware/
│       │   ├── authMiddleware.js        # JWT + rate limit por usuário
│       │   ├── adminMiddleware.js       # Proteção de rotas admin
│       │   ├── premiumMiddleware.js     # Gate de plano premium
│       │   ├── abuseProtectionMiddleware.js  # Detecção de abuso
│       │   ├── originGuardMiddleware.js      # Origin/Referer guard
│       │   ├── payloadValidationMiddleware.js # Whitelist de campos
│       │   └── accessTelemetryMiddleware.js  # Logging de acesso
│       ├── models/                     # Data models
│       ├── repositories/               # Database queries
│       ├── routes/                     # API route definitions
│       ├── services/
│       │   ├── authService.js           # Autenticação completa
│       │   ├── billingService.js        # Stripe integration
│       │   ├── demoService.js           # Lógica do modo DEMO
│       │   ├── financeService.js        # Despesas e categorias
│       │   ├── salesService.js          # Módulo comercial
│       │   ├── reportService.js         # Relatórios e exportação
│       │   ├── internationalWalletService.js # Carteira multi-moeda
│       │   ├── notificationService.js   # Central de notificações
│       │   ├── adminService.js          # Painel administrativo
│       │   ├── apiKeyService.js         # API keys para integrações
│       │   ├── marketRatesService.js    # Cotações de moedas
│       │   ├── emailService.js          # Envio de emails
│       │   └── cloudinaryService.js     # Upload de imagens
│       ├── docs/swagger.yaml           # API documentation
│       └── utils/                      # Helpers e utilitários
│
├── frontend/
│   ├── public/                         # Static assets
│   └── src/
│       ├── assets/                     # Imagens e ícones
│       ├── components/
│       │   ├── sidebar/                # Menu lateral
│       │   ├── navbar/                 # Navegação topo
│       │   ├── header/                 # Header do dashboard
│       │   ├── chart/                  # Componentes de gráfico
│       │   ├── notifications/          # Central de notificações
│       │   ├── finance/                # Componentes financeiros
│       │   ├── premium/                # Gating premium
│       │   ├── home/                   # Landing page
│       │   ├── layout/                 # Layout base
│       │   ├── admin-route/            # Proteção admin
│       │   ├── protected-route/        # Proteção de rota
│       │   └── cookie-consent-gate/    # Consentimento de cookies
│       ├── contexts/                   # React Context providers
│       ├── hooks/                      # Custom hooks
│       ├── layouts/                    # Layout wrappers
│       ├── pages/
│       │   ├── auth/                   # Login, Register, Forgot/Reset
│       │   ├── dashboard/
│       │   │   ├── Dashboard/          # Visão geral
│       │   │   ├── Expenses/           # Gestão de despesas
│       │   │   ├── Categories/         # Gestão de categorias
│       │   │   ├── Sales/              # Módulo comercial
│       │   │   ├── Wallet/             # Carteira internacional
│       │   │   ├── Reports/            # Relatórios
│       │   │   ├── Insights/           # Insights financeiros
│       │   │   ├── Currency/           # Conversão de moedas
│       │   │   ├── Admin/              # Painel administrativo
│       │   │   ├── Apps/               # Integrações
│       │   │   └── ExportAction/       # Exportação de dados
│       │   ├── PremiumPage/            # Página de planos
│       │   ├── misc/                   # Páginas auxiliares
│       │   └── shared/                 # Componentes compartilhados
│       ├── routes/                     # Definição de rotas
│       ├── services/                   # API service layer
│       ├── parsers/                    # Data parsers
│       ├── categorization/             # Categorização automática
│       ├── detectors/                  # Feature detection
│       ├── types/                      # Type definitions
│       └── utils/                      # Funções utilitárias
│
└── docs/
    ├── screenshots/                    # Capturas de tela
    ├── security-saas-hardening.md      # Documentação de hardening
    └── security-sql-injection.md       # Proteção contra SQL injection
```

---

## 🛠️ Stack Tecnológica

### Backend
| Tecnologia | Finalidade |
|------------|-----------|
| **Node.js** | Runtime |
| **Express 5** | Framework HTTP |
| **PostgreSQL** + `pg` | Banco de dados relacional |
| **JWT** + `bcryptjs` | Autenticação e hash de senhas |
| **Passport.js** | Google OAuth + Microsoft OAuth |
| **Stripe API** | Pagamentos e assinaturas |
| **PDFKit** | Geração de relatórios PDF |
| **Cloudinary** | Upload e armazenamento de imagens |
| **Nodemailer** / EmailJS | Envio de emails transacionais |
| **Helmet** | Headers de segurança |
| **express-rate-limit** | Rate limiting |
| **Swagger UI** | Documentação interativa da API |
| **Multer** | Upload de arquivos |

### Frontend
| Tecnologia | Finalidade |
|------------|-----------|
| **React 19** | UI framework |
| **Vite 8** | Build tool e dev server |
| **React Router 7** | Navegação SPA |
| **Axios** | HTTP client |
| **Recharts** + **ApexCharts** | Gráficos e visualizações |
| **React Icons** | Ícones |
| **React Select** | Selects avançados |
| **jsPDF** | Geração de PDF no client |
| **CSS Modules** | Estilos encapsulados |

---

## 🚀 Como rodar localmente

### Pré-requisitos

- Node.js 18+
- PostgreSQL
- Conta Stripe (modo teste)

### Instalação

```bash
# Instalar dependências do workspace
npm install

# Instalar dependências do backend
npm install --prefix backend

# Instalar dependências do frontend
npm install --prefix frontend
```

### Configuração

Crie `backend/.env` a partir de `backend/.env.example`:

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

Crie `frontend/.env` a partir de `frontend/.env.example`:

```env
VITE_API_BASE_URL=http://localhost:3000/api
VITE_GOOGLE_CLIENT_ID=seu_google_client_id
```

> ⚠️ Somente variáveis iniciadas com `VITE_` ficam disponíveis no frontend. **Nunca** coloque segredos Stripe, JWT, banco, SMTP ou Cloudinary no frontend.

### Executar

```bash
# Rodar tudo (backend + frontend) simultaneamente
npm run dev

# Ou separadamente:
npm run dev:backend    # Backend em http://localhost:3000
npm run dev:frontend   # Frontend em http://localhost:5173
```

### URLs

| Serviço | URL |
|---------|-----|
| Frontend | `http://localhost:5173` |
| Backend API | `http://localhost:3000` |
| Health Check | `http://localhost:3000/health` |
| Swagger Docs | `http://localhost:3000/api/docs` |

> 💡 No Windows PowerShell, se `npm` for bloqueado pela execution policy, use `npm.cmd`.

---

## 📡 API Endpoints

Rotas protegidas exigem:
```
Authorization: Bearer <accessToken>
```

<details>
<summary><strong>🔐 Auth</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `POST` | `/api/auth/register` | Criar conta |
| `POST` | `/api/auth/login` | Login com email/senha |
| `POST` | `/api/auth/google` | Login com Google |
| `POST` | `/api/auth/google/access-token` | Google access token |
| `GET` | `/api/auth/microsoft` | Iniciar OAuth Microsoft |
| `GET` | `/api/auth/microsoft/callback` | Callback Microsoft |
| `POST` | `/api/auth/refresh` | Renovar access token |
| `POST` | `/api/auth/logout` | Logout |
| `POST` | `/api/auth/forgot-password` | Solicitar reset de senha |
| `POST` | `/api/auth/reset-password` | Resetar senha |
| `POST` | `/api/auth/avatar` | Upload de avatar |

</details>

<details>
<summary><strong>📊 Dashboard</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/dashboard/me` | Dados do painel do usuário |

</details>

<details>
<summary><strong>💰 Financeiro</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/finance/categories` | Listar categorias |
| `POST` | `/api/finance/categories` | Criar categoria |
| `PUT` | `/api/finance/categories/:id` | Editar categoria |
| `DELETE` | `/api/finance/categories/:id` | Excluir categoria |
| `GET` | `/api/finance/expenses` | Listar despesas |
| `POST` | `/api/finance/expenses` | Criar despesa |
| `PUT` | `/api/finance/expenses/:id` | Editar despesa |
| `DELETE` | `/api/finance/expenses/:id` | Excluir despesa |
| `GET` | `/api/finance/summary` | Resumo financeiro |
| `GET` | `/api/finance/export/csv` | Exportar CSV |

</details>

<details>
<summary><strong>📈 Vendas</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/sales/orders` | Listar pedidos |
| `POST` | `/api/sales/orders` | Criar pedido |
| `PUT` | `/api/sales/orders/:id` | Editar pedido |
| `DELETE` | `/api/sales/orders/:id` | Excluir pedido |
| `GET` | `/api/sales/summary` | Resumo de vendas |

</details>

<details>
<summary><strong>🌍 Carteira Internacional</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/wallet/international` | Visão geral da carteira |
| `POST` | `/api/wallet/international/assets` | Adicionar ativo |
| `PUT` | `/api/wallet/international/assets/:id` | Editar ativo |
| `DELETE` | `/api/wallet/international/assets/:id` | Remover ativo |
| `GET` | `/api/wallet/international/movements` | Listar movimentações |
| `POST` | `/api/wallet/international/movements` | Registrar movimentação |
| `GET` | `/api/wallet/international/evolution` | Evolução patrimonial |

</details>

<details>
<summary><strong>📄 Relatórios</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/reports/processed-summary` | Relatório processado |
| `GET` | `/api/reports/export/pdf` | Exportar PDF |

</details>

<details>
<summary><strong>💳 Billing</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/billing/me` | Status da assinatura |
| `POST` | `/api/billing/checkout/premium` | Checkout premium |
| `POST` | `/api/billing/create-subscription` | Criar assinatura |
| `POST` | `/api/billing/checkout/export` | Comprar exportação avulsa |
| `POST` | `/api/billing/portal` | Portal do cliente Stripe |
| `POST` | `/api/billing/webhook` | Webhook Stripe |

</details>

<details>
<summary><strong>⚙️ Admin</strong></summary>

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/admin/overview` | Métricas gerais |
| `GET` | `/api/admin/users` | Listar usuários |
| `PATCH` | `/api/admin/users/:id/role` | Alterar role |
| `POST` | `/api/admin/users/:id/grant-premium` | Conceder premium |
| `POST` | `/api/admin/users/:id/remove-premium` | Remover premium |
| `POST` | `/api/admin/users/:id/reset-downloads` | Reset downloads |
| `POST` | `/api/admin/users/:id/block` | Bloquear conta |
| `DELETE` | `/api/admin/users/:id` | Excluir conta |

> No modo demo, endpoints admin de leitura retornam dados fictícios e mutações reais ficam bloqueadas.

</details>

---

## ☁️ Deploy

O projeto possui configuração pronta para **Vercel** (`backend/vercel.json` + `frontend/vercel.json`).

### Recomendações para deploy público

| Item | Recomendação |
|------|-------------|
| Modo demo | Use `DEMO_MODE=true` no ambiente de portfólio |
| Stripe | Configure somente chaves de teste |
| Cookies | Use `COOKIE_SECURE=true` em HTTPS |
| URLs | Configure `FRONTEND_URL`, `BACKEND_URL` e `CORS_ORIGINS` |
| Segredos | **Nunca** publique `.env` |
| Banco | Não use banco de produção com dados reais para portfólio |

---

## 📜 Licença

Este projeto usa a licença **MIT** com restrição de uso comercial.  
Consulte o arquivo [`LICENSE`](LICENSE) para mais detalhes.

---

<p align="center">
  Feito com ☕ e dedicação — <strong>Fluxa Financeiro</strong>
</p>
