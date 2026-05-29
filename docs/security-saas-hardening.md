# SaaS API Hardening

## Escopo

Auditoria e hardening do backend Node.js/Express do Fluxa Financas contra abuso de API, engenharia reversa operacional, scraping massivo, uso nao autorizado e clonagem de fluxos sensiveis.

## Vulnerabilidades e riscos

### Abuso de API e scraping

Risco: Alto.

Antes havia rate limit forte no login, mas as rotas autenticadas dependiam principalmente do token valido. Um usuario autenticado ou token roubado poderia fazer volume alto de requisicoes ate atingir limites externos de infraestrutura.

Correcao:

- Rate limit por usuario autenticado dentro do `authMiddleware`.
- Detecao de payload suspeito por IP.
- Bloqueio temporario em memoria para payloads repetidamente suspeitos.
- Telemetria estruturada de acesso.

### Engenharia reversa de endpoints

Risco: Medio.

Endpoints retornavam mensagens seguras em geral, mas faltava uma camada central de origem e telemetria. Isso facilitava enumeracao automatizada por clientes externos.

Correcao:

- `originGuardMiddleware` valida `Origin` e `Referer` quando presentes.
- CORS mantem allowlist.
- Logs de acesso registram metodo, path, status, duracao, IP e usuario.
- Erros continuam genericos para o usuario final.

### Uso nao autorizado por integracoes

Risco: Alto.

O sistema tinha JWT/refresh token, mas nao havia credencial de API por cliente. Integracoes tenderiam a reutilizar JWT de usuario, dificultando revogacao e auditoria.

Correcao:

- Tabela `api_keys`.
- API keys geradas como `fxk_*`.
- Hash SHA-256 persistido; a chave bruta e exibida uma unica vez.
- Rotas de criacao/listagem/revogacao.
- Escopos `read` e `write`.
- API key nao pode acessar painel admin.

### Payloads inesperados

Risco: Medio.

Rotas validavam campos principais, mas campos extras eram ignorados. Isso aumenta superficie de abuso e dificulta auditoria.

Correcao:

- Middleware `requireAllowedBodyFields`.
- Aplicado em auth, finance, sales, billing e admin.
- Campos inesperados retornam `400`.

## Controles implementados

- JWT para sessoes interativas.
- Refresh token com rotacao ja existente.
- API key por usuario/cliente.
- Rate limit por IP em auth.
- Rate limit por usuario autenticado.
- Bloqueio temporario por IP para payloads suspeitos.
- Validacao de origem.
- Telemetria de acesso.
- Payload whitelist.
- Admin bloqueado para API key.
- SQL parametrizado e hardening documentado em `docs/security-sql-injection.md`.

## Checklist OWASP aplicado

- A01 Broken Access Control: rotas protegidas exigem JWT ou API key valida; admin exige sessao interativa.
- A02 Cryptographic Failures: API key armazenada somente como hash.
- A03 Injection: queries parametrizadas e payloads suspeitos logados.
- A04 Insecure Design: separacao entre credenciais de usuario e credenciais de integracao.
- A05 Security Misconfiguration: CORS e Origin guard com allowlist.
- A07 Identification and Authentication Failures: expiracao/rotacao de JWT e revogacao de API keys.
- A09 Security Logging and Monitoring Failures: telemetria de acesso e logs de eventos suspeitos.

## Hardening recomendado para producao

- Persistir bloqueios de abuso em Redis para ambientes multi-instancia.
- Enviar logs de seguranca para SIEM ou provedor como Datadog, Sentry, CloudWatch ou Grafana Loki.
- Usar WAF na borda, como Cloudflare, AWS WAF ou Vercel Firewall.
- Configurar regras WAF para `UNION SELECT`, path scanning, brute force e scraping.
- Implementar plano de quotas por cliente/tenant.
- Versionar API publica (`/api/v1`) antes de expor integracoes externas.
- Assinar licencas de clientes com uma API central separada, caso o produto seja distribuido white-label.
- Usar usuario do banco com privilegios minimos no runtime.
- Manter migrations fora do usuario runtime.
- Configurar alertas para picos de 401, 403, 429 e 5xx.
- Habilitar `sslmode=verify-full` no banco quando suportado pelo provedor.
