# Módulo 12 — Worktree

## O que é?

**Worktree** — palavra em inglês para "árvore de trabalho" — é uma cópia isolada do seu projeto onde o Claude pode trabalhar sem afetar o que você está fazendo.

Imagine que você tem um projeto aberto e está no meio de uma tarefa. O Claude precisa testar algo arriscado — refatorar um arquivo, experimentar uma abordagem nova. Com Worktree, ele faz isso numa cópia separada. Se der errado, seu projeto original não foi tocado.

---

## Sem Worktree vs Com Worktree

```
Sem Worktree:
Você está trabalhando → Claude edita os mesmos arquivos → pode quebrar o que você tem

Com Worktree:
Você está trabalhando → Claude trabalha numa cópia isolada → seu projeto fica intacto
```

---

## Quando usar

- Tarefas arriscadas: refatorações grandes, mudanças estruturais
- Experimentos: testar uma abordagem antes de decidir se vale
- Subagentes paralelos: dois agentes trabalhando em partes diferentes sem conflito
- Revisão antes de aplicar: ver o resultado antes de tocar no projeto real

---

## Como funciona na prática

No Claude Code, você (ou um agente) aciona o Worktree e o Claude cria uma branch isolada automaticamente. Ele trabalha lá. Quando termina, você decide se aplica ou descarta.

É como um "rascunho" do projeto — separado, seguro, descartável.

---

## Worktree e Squads

Worktree é especialmente útil em squads: cada subagente pode ter seu próprio worktree, trabalhar em paralelo, e no final o orquestrador consolida tudo.

---

## Quando NÃO é necessário

Para projetos com arquivos simples e independentes (como documentos `.md`), Worktree não agrega muito. Se algo der errado, o Git já permite reverter facilmente. Worktree faz mais diferença em projetos com código real, arquivos interdependentes ou risco de conflito entre agentes.

---

## Exercício

Pense em uma tarefa no seu projeto que você hesitaria em pedir ao Claude por medo de estragar algo.

Responda:
1. Qual é a tarefa?
2. O que poderia dar errado sem isolamento?
3. Como o Worktree resolveria isso?
