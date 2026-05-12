# Módulo 14 — Agent Teams

## O que é?

Agent Teams é uma funcionalidade nativa do Claude Code que permite rodar **múltiplos agentes em paralelo**, de forma coordenada, dentro de uma mesma sessão.

É diferente de um squad — Agent Teams é algo que o próprio Claude Code gerencia internamente, sem você precisar montar manualmente os agentes.

---

## Diferença: Squad vs Agent Teams

| | Squad | Agent Teams |
|---|---|---|
| O que é | Você monta manualmente com CLAUDE.md e arquivos | Funcionalidade nativa do Claude Code |
| Coordenação | Você define no CLAUDE.md do orquestrador | Claude Code gerencia automaticamente |
| Paralelo? | Sim, via subagentes | Sim, nativamente |
| Nível | Intermediário | Avançado |

---

## Quando usar Agent Teams

A diferença prática está no volume e no paralelismo:

**Com Squad:**
O orquestrador processa uma tarefa, termina, passa para a próxima. Uma por vez.

**Com Agent Teams:**
O Claude divide o trabalho entre agentes que rodam ao mesmo tempo. Tudo em paralelo. O resultado chega muito mais rápido.

**Exemplo concreto:**
Você quer analisar 20 vídeos de uma vez — público, keyword, título, thumbnail. Com Squad, são 20 rodadas sequenciais. Com Agent Teams, todos os 20 rodam ao mesmo tempo.

---

## Squad dentro do Agent Teams

Agent Teams não substitui o Squad — ele coordena múltiplos squads rodando em paralelo. A lógica interna de cada tarefa continua sendo um squad. O Agent Teams só escala o volume.

---

## A sequência certa

1. **Squad** — monta o processo, testa, ajusta, valida
2. **Agent Teams** — quando o processo já está provado, escala com paralelismo

Não faz sentido escalar um processo que você ainda não sabe se funciona bem. Squad primeiro, sempre.

---

## Limitação honesta

Agent Teams ainda é uma funcionalidade em evolução no Claude Code. Para a maioria dos casos, squads já resolvem bem. Agent Teams vale explorar quando você já tiver squads rodando com consistência e precisar escalar volume.

---

## Exercício

Pense num projeto que teria pelo menos 3 partes independentes que poderiam rodar ao mesmo tempo.

Responda:
1. Quais são as 3 partes?
2. O que cada agente faria?
3. Como você consolidaria os resultados no final?
