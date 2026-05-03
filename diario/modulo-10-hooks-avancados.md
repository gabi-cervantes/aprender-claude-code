# Módulo 10 — Hooks Avançados

## Revisão rápida

Hooks são comandos que rodam automaticamente em eventos específicos. Você já usou no Módulo 6 para notificações de som. Agora vamos além.

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

## O que os usuários avançados fazem com hooks

### 1. Log de comandos (PreToolUse + Bash)
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

### 2. Formatar código após edição (PostToolUse + Write/Edit)
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

### 3. Bloquear comandos destrutivos (PreToolUse)
Intercepta `rm -rf` antes de executar e bloqueia automaticamente.

### 4. Rodar testes após edição (PostToolUse)
Toda vez que Claude edita um arquivo `.js` ou `.py`, roda os testes automaticamente.

### 5. Notificação ao iniciar sessão (SessionStart)
Dispara uma mensagem ou carrega um contexto específico quando a sessão começa.

### 6. Resumo ao final da sessão (Stop)
**Limitação importante:** o hook `Stop` não tem acesso ao conteúdo da conversa — ele é um comando de shell "burro" que só sabe que Claude terminou de responder. Não consegue gerar um resumo inteligente do que foi feito.

Para resumos com contexto real, use o comando `/resumir` — ele pede ao Claude para gerar o resumo com tudo que aconteceu na conversa.

---

## Matcher: como direcionar o hook para a ferramenta certa

O `matcher` define para qual ferramenta o hook dispara:

```json
"matcher": "Bash"        // só para comandos no terminal
"matcher": "Write|Edit"  // para escrita e edição de arquivos
"matcher": "Read"        // para leitura de arquivos
```

Sem matcher, o hook dispara para qualquer ferramenta.

---

## Quando hooks avançados fazem sentido para você

Hooks de formatação, testes e logs fazem mais sentido em **projetos de código** — quando você está desenvolvendo software com Claude.

Para uso em conversas, estudo e configurações (seu momento atual), os hooks mais úteis são:
- **Notification** — som quando Claude pede permissão
- **Stop** — som quando Claude termina (se quiser saber quando acabou)

Conforme você evoluir para projetos mais técnicos, os hooks avançados vão fazer cada vez mais sentido.

---

## Exercício

Pense em um processo que você repete toda vez que trabalha em um projeto. Responda:

1. Qual evento do hook capturaria esse momento? (PreToolUse, PostToolUse, Stop...)
2. Qual ferramenta você usaria como matcher?
3. O que o comando faria?
