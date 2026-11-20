# Agentes, harness e skills

## Harness
Todos os agentes operaram no **Claude Code** (harness agêntico da Anthropic, executado via Claude Agent SDK), com o modelo **Claude Sonnet 5.5**. Um agente orquestrador criou o contrato (`docs/API.md`, schema D1, definições de agentes e skills) e delegou o trabalho a subagentes com contexto isolado. Cada subagente tem definição em `.claude/agents/` e uma skill em `.claude/skills/`.

## Agentes
| # | Agente | Papel | Arquivo | Skill usada |
|---|---|---|---|---|
| 1 | `backend-agent` | Functions, D1, OAuth2 Discord, regras de negócio no servidor | `.claude/agents/backend-agent.md` | `cloudflare-pages-d1` |
| 2 | `frontend-agent` | Interface HTML5/CSS3/Vanilla JS, grade, filtros, formulário | `.claude/agents/frontend-agent.md` | `vanilla-frontend` |
| 3 | `qa-agent` | **Teste e validação**: testes automatizados, auditoria de segurança e de conformidade com a rubrica | `.claude/agents/qa-agent.md` | `qa-validation` |

## Skills
- `.claude/skills/cloudflare-pages-d1/SKILL.md`
- `.claude/skills/vanilla-frontend/SKILL.md`
- `.claude/skills/qa-validation/SKILL.md`

## Fluxo
1. Orquestrador → contrato (`API.md`, `migrations/0001_init.sql`, `wrangler.toml`).
2. `backend-agent` e `frontend-agent` em paralelo, cada um restrito à sua pasta.
3. `qa-agent` valida a integração, escreve testes, corrige falhas mínimas e registra em `docs/RELATORIO-QA.md`.

## Observação
Os agentes são assistentes de desenvolvimento; o autor revisou o resultado e responde pelo projeto.
