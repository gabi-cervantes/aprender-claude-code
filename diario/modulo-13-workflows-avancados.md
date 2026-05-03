# Módulo 13 — Workflows Avançados

## O que é um workflow?

**Workflow** = fluxo de trabalho. Uma sequência de etapas que sempre seguem a mesma ordem para produzir um resultado.

A diferença de um workflow avançado é que ele **combina várias peças que você já aprendeu**: agentes, skills, MCPs, hooks, checkpoints — tudo junto num processo coeso.

---

## O que muda num workflow avançado

Um workflow simples:
```
Você pede → Claude executa → entrega resultado
```

Um workflow avançado:
```
Gatilho → Agente orquestrador aciona skills e subagentes
       → Checkpoints pedem sua aprovação nos pontos certos
       → MCPs salvam no Notion / Drive / Sheets
       → Hook notifica quando termina
```

---

## Como criar um workflow

Um workflow vive no **CLAUDE.md do agente orquestrador**. Você escreve o fluxo lá:

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

**2. Papéis definidos**
Quem faz o quê? Orquestrador, executores, revisores — cada um com seu CLAUDE.md.

**3. Checkpoints estratégicos**
Onde você precisa validar antes de continuar? São os pontos onde o agente para, mostra o que fez e aguarda sua aprovação antes de avançar.

**4. Saída estruturada**
Onde o resultado vai? Notion, arquivo local, Google Sheets, email?

---

## Exemplo concreto

Workflow de análise e publicação de conteúdo:

```
1. Você envia o tema
2. Agente pesquisador busca referências (WebSearch)
3. CHECKPOINT — você aprova as referências
4. Agente executor cria o conteúdo seguindo as skills de público e tom
5. Agente revisor avalia qualidade
6. CHECKPOINT — você aprova o conteúdo final
7. MCP do Notion salva na base "Conteúdos prontos"
8. Hook Glass toca avisando que terminou
```

Você interagiu em apenas 2 momentos. O resto foi automático.

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
