# Módulo 13 — Workflows Avançados

## O que é um workflow?

**Workflow** = fluxo de trabalho. Uma sequência de etapas que sempre seguem a mesma ordem para produzir um resultado.

Workflow não exige múltiplos agentes. Pode ser um único Claude seguindo uma sequência de passos — com tools, MCPs, checkpoints e hooks integrados.

---

## Workflow simples vs Workflow com squad

**Workflow simples:**
Um único Claude executa todas as etapas em sequência.

```
Você envia o tema
→ Claude busca referências (WebSearch)
→ CHECKPOINT — você aprova
→ Claude escreve o texto (skill de conteúdo)
→ Claude salva no Notion (MCP)
→ Hook notifica que terminou
```

Um agente só. Sequência clara. Sem coordenação entre múltiplos papéis.

**Workflow com squad:**
Quando a tarefa é complexa demais para um agente só — você divide em agentes especializados. Cada um tem um papel fixo e o output de um vira o input do próximo.

```
Agente pesquisador → Agente redator → Agente revisor
```

A diferença não é complexidade técnica — é sobre quando a especialização justifica dividir. Na maioria dos casos, o workflow simples resolve.

---

## O que muda num workflow avançado

Um workflow simples:
```
Você pede → Claude executa → entrega resultado
```

Um workflow avançado:
```
Gatilho → Claude aciona skills e ferramentas
       → Checkpoints pedem sua aprovação nos pontos certos
       → MCPs salvam no Notion / Drive / Sheets
       → Hook notifica quando termina
```

---

## Como criar um workflow

Um workflow vive no **CLAUDE.md do agente**. Você escreve o fluxo lá:

```markdown
## Fluxo

1. Receba o tema do usuário
2. Use WebSearch para buscar 3 referências
3. CHECKPOINT: mostre as referências e aguarde aprovação
4. Use skill_criacao_conteudo.md para escrever o texto
5. Use o Notion para salvar na base "Conteúdos prontos"
```

Não tem ferramenta especial. É uma instrução bem escrita no CLAUDE.md.

Na prática, você não precisa escrever isso do zero:
1. Descreva em linguagem normal o que quer que aconteça
2. Peça ao Claude para transformar isso num CLAUDE.md estruturado
3. Cole no agente

---

## Os 4 elementos de um workflow avançado

**1. Entrada clara**
O que dispara o workflow? Uma mensagem sua, um arquivo novo, um horário?

**2. Passos definidos**
O que acontece em cada etapa? Quais ferramentas, skills ou MCPs são usados?

**3. Checkpoints estratégicos**
Onde você precisa validar antes de continuar? São os pontos onde o agente para, mostra o que fez e aguarda sua aprovação antes de avançar.

**4. Saída estruturada**
Onde o resultado vai? Notion, arquivo local, Google Sheets, email?

---

## Exemplo concreto (workflow simples)

Workflow de criação de conteúdo — um agente só:

```
1. Você envia o tema
2. Claude busca 3 referências (WebSearch)
3. CHECKPOINT — você aprova as referências
4. Claude escreve o conteúdo seguindo a skill de tom e público
5. CHECKPOINT — você aprova o conteúdo final
6. MCP do Notion salva na base "Conteúdos prontos"
7. Hook Glass toca avisando que terminou
```

Você interagiu em apenas 2 momentos. O resto foi automático.

Quando esse processo já estiver funcionando bem e você precisar de especialização maior — um agente só para pesquisa, outro só para escrita, outro para revisão — aí faz sentido evoluir para um squad (Módulo 11).

---

## A chave dos workflows avançados

Não é sobre complexidade — é sobre **saber onde colocar o humano no loop**.

Automatize o que é repetível. Reserve seus checkpoints para decisões que realmente precisam de você.

---

## Exercício

Pense em um processo que você faz com frequência e que tem pelo menos 4 etapas.

Mapeie:
1. Qual é a entrada?
2. Quais etapas poderiam ser automatizadas?
3. Onde você colocaria checkpoints?
4. Onde vai o resultado final?
