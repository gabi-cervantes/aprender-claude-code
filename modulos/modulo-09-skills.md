# Módulo 10 — Skills

## O que é uma skill?

Uma skill é um arquivo de instrução que ensina o Claude a executar um método repetível. Diferente de um agente, ela não decide nem coordena — ela segue um protocolo.

Pense assim:
- **Agente** = funcionário que pensa e decide
- **Skill** = manual de procedimento que o agente segue

---

## Skill vs Agente vs Subagente

| | Skill | Agente | Subagente |
|---|---|---|---|
| O que é | Arquivo de instrução | Claude com papel definido | Claude filho rodando separado |
| Decide? | Não | Sim | Sim |
| Gasta tokens extras? | Não (é só contexto) | Depende | Sim |
| Quando usar | Métodos repetíveis | Coordenação e decisão | Tarefas pesadas e independentes |

---

## Tipos de skills

**Skills de persona/público**
Simulam como um público específico reagiria a um conteúdo. Funcionam como lentes de avaliação.

Exemplo: `skill_publico_empreendedor.md` — contém dores, desejos, objeções e critérios de clique desse público.

**Skills operacionais**
Seguem um protocolo para executar uma tarefa específica.

Exemplos:
- skill de criação de títulos
- skill de revisão de copy
- skill de estrutura de roteiro
- skill de pesquisa de keywords

**Skills de comportamento**
Definem como o Claude deve se comunicar ou agir em um contexto.

Exemplo: tom de voz, formato de resposta, regras editoriais.

---

## Como criar uma skill

Uma skill é simplesmente um arquivo `.md` com instruções claras.

Estrutura básica:

```markdown
# Skill: Nome da Skill

## Objetivo
O que essa skill faz.

## Quando usar
Em quais situações o agente deve acionar essa skill.

## Protocolo
Passo a passo do que executar.

## Formato de saída
Como o resultado deve ser entregue.

## Restrições
O que essa skill NÃO deve fazer.
```

---

## Como um agente usa uma skill

O agente não usa a skill automaticamente — você instrui no CLAUDE.md dele:

```markdown
Quando precisar avaliar um título, leia skills/skill_titulos.md e siga o protocolo.
```

Você também pode pedir diretamente no chat:

```
Use a skill de revisão de copy nesse texto.
```

---

## Onde ficam as skills

Convenção recomendada:

```
meu-projeto/
  skills/
    skill_publico_empreendedor.md
    skill_criacao_titulos.md
    skill_revisao_copy.md
  CLAUDE.md
```

O CLAUDE.md do projeto referencia quais skills estão disponíveis e quando usá-las.

---

## Exemplos de skills que você já usa

- `/resumir` — skill de resumo de sessão (criada no Módulo 5 como slash command)
- Skills de público no Opensquad — simulam a reação de audiências específicas

---

## Exercício

Pense em uma tarefa que você repete frequentemente — pode ser revisar um texto, criar um título, responder um email com determinado tom.

Escreva no papel (não precisa criar o arquivo agora) o protocolo dessa skill:
1. Qual o objetivo?
2. Quais são os passos?
3. Qual o formato de saída?
4. O que ela não deve fazer?
