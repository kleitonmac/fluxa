# SQL Injection Hardening

## Escopo revisado

Backend Node.js/Express com PostgreSQL via `pg`.

## Risco identificado

O projeto ja usava parametros `$1`, `$2`, etc. na maior parte das queries. O ponto de maior risco era o painel admin, especialmente listagem de usuarios com filtros, busca e ordenacao. Mesmo com whitelist de colunas, a query ainda montava fragmentos SQL dinamicamente para `WHERE` e `ORDER BY`.

Se um campo de ordenacao, direcao ou filtro fosse relaxado no futuro, esse padrao poderia abrir caminho para SQL Injection em uma rota sensivel.

Severidade: Alta para rotas administrativas expostas em producao.

## Correcoes aplicadas

- Removida a montagem dinamica de `WHERE` e `ORDER BY` em `adminService.listUsers`.
- Query admin convertida para prepared statement nomeado `admin_list_users_safe_v1`.
- Filtros `search`, `role`, `plan`, `sort`, `direction`, `limit` e `offset` passam por whitelist/normalizacao.
- Busca `LIKE` escapa `%`, `_` e `\`.
- Ordenacao usa parametros e `CASE WHEN`, sem interpolar identificadores vindos da request.
- Logs de seguranca registram sinais comuns de SQL Injection sem retornar detalhes ao usuario.
- Pool PostgreSQL recebeu `statement_timeout`, `query_timeout` e `application_name`.

## Checklist aplicado

- Queries parametrizadas para inputs de usuario.
- Sem concatenacao de input direto em SQL.
- Whitelist para ordenacao e direcao.
- Whitelist para role e plan.
- Validacao de tamanho em busca textual.
- Escape seguro para `LIKE`.
- Tratamento generico de erro nas rotas.
- Logs de seguranca para payloads suspeitos.
- Timeouts de banco para reduzir abuso operacional.

## Hardening recomendado em producao

- Usar usuario PostgreSQL dedicado da aplicacao, sem permissoes administrativas.
- Conceder apenas `SELECT`, `INSERT`, `UPDATE`, `DELETE` nas tabelas necessarias.
- Remover permissoes de `CREATE`, `DROP`, `ALTER`, `TRUNCATE` do usuario da API.
- Rodar migrations com outro usuario, separado do usuario runtime.
- Ativar WAF no provedor de borda, como Cloudflare, AWS WAF ou equivalente.
- Habilitar logs de queries lentas e erros no PostgreSQL.
- Monitorar eventos `security.suspicious_input`.
- Configurar alertas para repeticao de payloads com `UNION`, `DROP`, `--`, `/*`, `OR 1=1`.
- Usar `sslmode=verify-full` no `DATABASE_URL` em producao quando o provedor suportar.
- Manter testes de seguranca para filtros, busca e ordenacao.

## Exemplo de menor privilegio no PostgreSQL

```sql
CREATE ROLE fluxa_app LOGIN PASSWORD 'senha-forte';

GRANT CONNECT ON DATABASE fluxa TO fluxa_app;
GRANT USAGE ON SCHEMA public TO fluxa_app;
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO fluxa_app;
ALTER DEFAULT PRIVILEGES IN SCHEMA public
  GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO fluxa_app;

REVOKE CREATE ON SCHEMA public FROM fluxa_app;
REVOKE ALL PRIVILEGES ON DATABASE fluxa FROM PUBLIC;
```

Use um usuario separado para migrations com permissoes de DDL.
