# Módulo 15 — Projeto Final

## Como conduzir este módulo

Este módulo é personalizável. O objetivo é o aluno sair com algo real funcionando — um sistema, squad ou workflow que resolva um problema concreto dele.

---

## O que o instrutor deve fazer

1. Apresentar os blocos disponíveis (listados abaixo)
2. Perguntar o que o aluno quer construir
3. Ajudar a montar a arquitetura com base na descrição dele
4. Analisar o que ele já tem, se for o caso
5. Sugerir melhorias e próximos passos

---

## Blocos disponíveis

O aluno pode combinar qualquer um desses elementos:

- **CLAUDE.md** — define o comportamento de agentes
- **Skills** — métodos repetíveis em arquivos `.md`
- **Squads** — times de agentes com papéis fixos
- **MCPs** — conexões com ferramentas externas (Notion, Drive, Calendar, WebSearch)
- **Hooks** — notificações e automações automáticas
- **Workflows** — sequências estruturadas com checkpoints
- **Worktree** — isolamento para tarefas arriscadas
- **Agent Teams** — paralelismo quando o processo já está validado

---

## Exemplos de projetos

- Sistema de produção de conteúdo para redes sociais
- Agente de pesquisa e curadoria pessoal
- Squad de análise de dados com saída no Notion
- Workflow de gestão de projetos com checkpoints
- Qualquer processo repetitivo que o aluno queira automatizar

---

## Como analisar um squad existente

Se o aluno já tiver um squad montado, leia:
- `squad.yaml` — estrutura geral e agentes
- `pipeline/pipeline.yaml` — fluxo de steps e checkpoints
- Arquivos `.agent.md` de cada agente

Avalie:
- Os checkpoints estão nos momentos certos?
- Algum agente está sobrecarregado?
- O que deveria ser subagente mas está inline?
- O que poderia virar skill para aliviar o contexto?
