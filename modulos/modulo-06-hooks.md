# Módulo 6 — Hooks (Completo)

## O que são
Comandos que rodam automaticamente em momentos específicos — sem você precisar pedir. Diferente de instruções no CLAUDE.md (que o Claude pode ou não seguir), hooks são executados pelo sistema.

## Diferença entre hook e instrução no CLAUDE.md
- **CLAUDE.md:** o Claude lê e tenta seguir — mas é uma instrução de comportamento
- **Hook:** o sistema executa automaticamente — não depende do Claude

## Onde ficam
No `~/.claude/settings.json`, dentro da chave `hooks`.

---

## Eventos disponíveis

| Evento | Quando dispara | Pode bloquear? |
|---|---|---|
| `PreToolUse` | Antes de Claude usar uma ferramenta | Sim |
| `PostToolUse` | Depois de Claude usar uma ferramenta | Não |
| `Stop` | Quando Claude termina de responder | Não |
| `Notification` | Quando o sistema pede permissão | Não |
| `UserPromptSubmit` | Quando você envia uma mensagem | Sim |
| `SessionStart` | Quando uma sessão começa | Não |

---

## Hooks básicos: notificações de som

### Stop + Blow
Toca quando Claude termina de responder — útil para tarefas longas onde você vai fazer outra coisa enquanto espera.

### Notification + Glass
Toca quando o sistema pede permissão — para você não perder o momento e deixar Claude travado esperando.

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"Claude terminou!\" with title \"Claude Code\" sound name \"Blow\"'"
          }
        ]
      }
    ],
    "Notification": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "osascript -e 'display notification \"Claude precisa da sua atenção!\" with title \"Claude Code\" sound name \"Glass\"'"
          }
        ]
      }
    ]
  }
}
```

### Sons disponíveis no Mac
`Basso`, `Blow`, `Bottle`, `Frog`, `Funk`, `Glass`, `Hero`, `Morse`, `Pop`, `Purr`, `Sosumi`, `Submarine`, `Tink`

Para testar um som antes de escolher:
```bash
afplay /System/Library/Sounds/Glass.aiff
```

---

## Hooks avançados

### Matcher: como direcionar o hook para a ferramenta certa

O `matcher` define para qual ferramenta o hook dispara:

```json
"matcher": "Bash"        // só para comandos no terminal
"matcher": "Write|Edit"  // para escrita e edição de arquivos
"matcher": "Read"        // para leitura de arquivos
```

Sem matcher, o hook dispara para qualquer ferramenta.

---

### O que os usuários avançados fazem com hooks

**1. Log de comandos (PreToolUse + Bash)**
Salva automaticamente tudo que Claude executa no terminal em um arquivo.
```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Bash",
      "hooks": [{
        "type": "command",
        "command": "jq -r '.tool_input.command' >> ~/.claude/bash-log.txt"
      }]
    }]
  }
}
```

**2. Formatar código após edição (PostToolUse + Write/Edit)**
Roda o Prettier automaticamente depois que Claude edita um arquivo.
```json
{
  "hooks": {
    "PostToolUse": [{
      "matcher": "Write|Edit",
      "hooks": [{
        "type": "command",
        "command": "jq -r '.tool_input.file_path' | { read -r f; prettier --write \"$f\"; } 2>/dev/null || true"
      }]
    }]
  }
}
```

**3. Bloquear comandos destrutivos (PreToolUse)**
Intercepta `rm -rf` antes de executar e bloqueia automaticamente.

**4. Rodar testes após edição (PostToolUse)**
Toda vez que Claude edita um arquivo `.js` ou `.py`, roda os testes automaticamente.

**5. Notificação ao iniciar sessão (SessionStart)**
Dispara uma mensagem ou carrega um contexto específico quando a sessão começa.

---

### Limitação importante: resumo automático de sessão

O hook `Stop` não tem acesso ao conteúdo da conversa — é um comando de shell que só sabe que Claude terminou de responder. Não consegue gerar um resumo inteligente do que foi feito.

Para resumos com contexto real, use o comando `/resumir`.

---

### Quando hooks avançados fazem sentido

Hooks de formatação, testes e logs fazem mais sentido em **projetos de código**. Para uso em conversas e configurações, os mais úteis são Notification e Stop.

---

## Como desativar os hooks
Apague o bloco `"hooks"` do `settings.json`, ou use:
```json
"disableAllHooks": true
```

---

## Exercício
Configure o hook de Notification com som Glass no seu `~/.claude/settings.json` e teste: peça algo ao Claude que precise de permissão e veja se o som toca.
