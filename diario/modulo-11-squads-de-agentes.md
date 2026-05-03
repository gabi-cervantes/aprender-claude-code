# Módulo 9 — Squads de Agentes

## O que é um squad?

Squad é uma equipe de agentes com papéis fixos, onde cada um tem uma responsabilidade clara e trabalha em sequência ou em paralelo com os outros.

A diferença de um agente único com várias skills:

| Agente único com skills | Squad |
|---|---|
| Faz tudo sozinho | Cada agente faz uma parte |
| Mais simples de configurar | Mais poderoso para tarefas complexas |
| Um contexto só | Cada agente tem seu próprio contexto |
| Pode ficar sobrecarregado | Divide responsabilidade |

---

## Quando usar squad em vez de agente único?

A pergunta que resolve na maioria dos casos:

> *"Isso ficaria confuso demais para uma pessoa só fazer de uma vez?"*

**Use agente único com skills quando:**
- as tarefas são sequenciais e simples
- o contexto precisa ser compartilhado o tempo todo
- você quer economizar tokens

**Use squad quando:**
- a tarefa é grande demais para um agente só
- partes podem rodar em paralelo
- você quer especialização real — cada agente sendo muito bom em uma coisa só
- o erro de um não deve contaminar o trabalho do outro

**Exemplo prático:**
- Pedir para escrever um post com tom informal → agente único + skill de tom
- Criar uma campanha completa com pesquisa, 10 variações de copy, análise crítica e plano de distribuição → squad

---

## Como um squad funciona na prática

Cada agente do squad tem seu próprio arquivo CLAUDE.md com:
- quem ele é
- o que ele faz
- o que ele recebe como input
- o que ele entrega como output
- o que ele NÃO deve fazer

O output de um agente vira o input do próximo. O Agente 2 não começa até o Agente 1 terminar.

---

## Exemplo: squad para criar um carrossel no Instagram

### Agente 1 — Pesquisador
**Recebe:** tema do carrossel
**Faz:** pesquisa referências, tendências e dados relevantes sobre o tema
**Entrega:** documento com referências e insights organizados

### Agente 2 — Redator
**Recebe:** documento do Pesquisador
**Faz:** escreve o texto de cada slide seguindo o briefing de tom e público
**Entrega:** texto completo de todos os slides

### Agente 3 — Crítico
**Recebe:** texto do Redator
**Faz:** revisa se está claro, atrativo, com bom CTA e coerente com o público
**Entrega:** texto revisado com aprovação ou ajustes obrigatórios

---

## Como criar um squad do zero no Claude Code

### Passo 1 — Crie a estrutura de pastas

```
meu-squad/
  CLAUDE.md              ← instruções gerais do squad
  agente-pesquisador.md  ← instruções do agente 1
  agente-redator.md      ← instruções do agente 2
  agente-critico.md      ← instruções do agente 3
  output/                ← onde os outputs são salvos
```

### Passo 2 — Escreva o CLAUDE.md do squad

O CLAUDE.md geral define o fluxo:

```markdown
# Squad Carrossel Instagram

## Fluxo
1. O Pesquisador recebe o tema e entrega referências em output/pesquisa.md
2. O Redator lê output/pesquisa.md e entrega os slides em output/slides.md
3. O Crítico lê output/slides.md e entrega a versão final em output/final.md

## Regras gerais
- Nenhum agente pula sua etapa
- Cada agente salva seu output antes de passar para o próximo
- Checkpoints obrigatórios após cada etapa
```

### Passo 3 — Escreva o CLAUDE.md de cada agente

Exemplo para o Redator:

```markdown
# Agente Redator

## Quem sou
Especialista em copy para Instagram. Tom direto, linguagem simples.

## O que recebo
Documento em output/pesquisa.md com referências e insights.

## O que entrego
Texto completo de cada slide em output/slides.md.
Máximo 80 palavras por slide. Primeiro slide é o gancho.

## O que NÃO faço
- Não faço pesquisa (isso é papel do Pesquisador)
- Não reviso meu próprio texto (isso é papel do Crítico)
- Não publico nada
```

### Passo 4 — Acione o squad no chat

```
Leia o CLAUDE.md do squad e execute o fluxo completo.
Tema: "3 erros que iniciantes cometem ao usar IA no trabalho"
```

---

## Checkpoints entre agentes

Sempre coloque um checkpoint entre cada etapa para validar antes de continuar:

```
Após entregar a pesquisa, pare e me mostre o resultado.
Aguarde minha aprovação antes de acionar o Redator.
```

Isso evita que um erro do Agente 1 se propague para os outros.

---

## Ferramenta avançada: Opensquad

Se quiser um framework pronto para criar e gerenciar squads de forma mais estruturada, pesquise por **Opensquad** — é um sistema de orquestração de squads para Claude Code.

Ele automatiza a criação de agentes, pipelines e memória entre sessões. Mas entender como criar squads do zero (como mostrado acima) é o fundamento necessário antes de usar qualquer framework.

---

## Exercício

Monte no papel (não precisa criar os arquivos agora) um squad para uma tarefa do seu dia a dia. Defina:

1. Quantos agentes você precisaria?
2. Qual o papel de cada um?
3. O que cada um recebe e entrega?
4. Onde você colocaria checkpoints?
