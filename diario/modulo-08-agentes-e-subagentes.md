# Módulo 8 — Agentes e Subagentes

## O que é um agente?

No Claude Code, um agente é o Claude executando uma tarefa de forma autônoma — ele lê arquivos, roda comandos e toma decisões no meio do caminho, sem você precisar aprovar cada passo.

A diferença do chat normal é a **autonomia**: ele age, não só responde.

---

## Os 3 conceitos centrais

### Agente
Executa uma missão com autonomia. Você dá o objetivo, ele resolve.

### Subagente
Um "Claude filho" criado pelo agente principal para executar parte da tarefa. Roda separado, faz o trabalho e devolve o resultado. Útil para:
- tarefas que podem rodar em paralelo
- proteger o contexto principal de ficar cheio
- isolar uma pesquisa ou análise específica

### Squad
Uma equipe de agentes com papéis fixos. Cada um tem uma função definida — um pesquisa, um escreve, um revisa. Eles se comunicam e o resultado final é o trabalho conjunto.

---

## Tipos de agentes

| Tipo | O que faz | Exemplo (squad de carrossel para Instagram) |
|---|---|---|
| **Orquestrador** | Coordena, delega e consolida. É o "chefe" do fluxo | Recebe o tema do carrossel e aciona os outros agentes |
| **Executor** | Recebe uma tarefa específica e executa. Não decide nada | Escreve o texto de cada slide seguindo o briefing |
| **Crítico/Revisor** | Avalia o output de outro agente antes de chegar em você | Revisa se o carrossel está claro, atrativo e com bom CTA |
| **Monitor** | Fica de olho em algo ao longo do tempo e dispara alertas | Acompanha o engajamento do post e sugere ajustes |
| **Pesquisador** | Busca informação externa e traz de volta | Pesquisa referências e tendências do nicho antes de criar |

---

## Agente vs Skill vs Subagente

Nem tudo deve ser agente. A regra é:

```
Agente    = decide, coordena, interpreta, critica ou monitora continuamente
Skill     = executa um método repetível (é um arquivo de instrução, não um Claude novo)
Subagente = Claude separado acionado para uma tarefa pesada e independente
```

**Quando usar skill em vez de subagente:**
Se a tarefa é aplicar uma perspectiva ou seguir um protocolo simples, use skill — é só contexto, não gasta tokens extras.

**Quando usar subagente:**
Quando a tarefa é complexa, independente e pode rodar em paralelo com outras coisas.

---

## Como um agente chama uma skill

O agente não chama skills automaticamente — ele chama porque você instruiu no CLAUDE.md dele.

Exemplo de instrução no CLAUDE.md do agente:
```
Quando precisar avaliar uma ideia pelo ângulo de um público específico,
leia o arquivo skills/skill_publico_correspondente.md e aplique aquela perspectiva.
```

Você também pode pedir no chat:
```
Avalie esse título usando a skill do público iniciante.
```

---

## Como evitar que o agente esqueça de usar uma skill

### 1. Prompt mais rígido

Em vez de "quando precisar", use linguagem obrigatória:
```
OBRIGATÓRIO: antes de recomendar qualquer título,
você DEVE consultar pelo menos uma skill de público.
Nunca pule essa etapa.
```

### 2. Checkpoints no fluxo

Defina pontos onde o agente para e te mostra o que fez antes de continuar:
```
Após o diagnóstico inicial, pare e me mostre:
- qual público você consultou
- o que a skill disse
Aguarde minha aprovação para continuar.
```

---

## Como o comportamento do agente é definido

O comportamento do agente vive no **CLAUDE.md** dele — é lá que você escreve as regras, o fluxo, o que é obrigatório e o que é proibido.

Para criar um bom prompt de agente, o processo prático é:
1. Explicar por áudio ou texto o que você quer que o agente faça e não faça
2. Pedir para uma IA gerar o prompt estruturado
3. Colar no CLAUDE.md do agente

---

## Limitação importante

Nenhum sistema de agentes é 100% confiável sem revisão humana. Checkpoints existem exatamente para manter você no loop, validando antes de avançar.

---

## Exercício

Pense em um processo repetitivo que você faz — pode ser profissional ou pessoal. Responda:

1. Qual seria o agente orquestrador?
2. Que skills ele precisaria?
3. Em que momento você colocaria um checkpoint?
