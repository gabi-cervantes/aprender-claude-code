# Módulo 6 — Hooks

## O que são
Comandos que rodam automaticamente em momentos específicos — sem você precisar pedir. Diferente de instruções no CLAUDE.md (que o Claude pode ou não seguir), hooks são executados pelo sistema.

## Quando disparam
| Evento | Quando acontece |
|---|---|
| `PreToolUse` | Antes do Claude usar uma ferramenta |
| `PostToolUse` | Depois do Claude usar uma ferramenta |
| `Stop` | Quando o Claude termina de responder |
| `Notification` | Quando o Claude manda uma notificação |

## Onde ficam
No `settings.json`, dentro da chave `hooks`.

## Exemplo: notificação quando o Claude termina
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
    ]
  }
}
```

Este hook mostra uma notificação no Mac com som quando o Claude para de responder — útil para tarefas longas onde você vai fazer outra coisa enquanto espera.

## Diferença entre hook e instrução no CLAUDE.md
- **CLAUDE.md:** o Claude lê e tenta seguir — mas é uma instrução de comportamento
- **Hook:** o sistema executa automaticamente — não depende do Claude

## Exercício
Adicione o hook de notificação acima no seu `~/.claude/settings.json` e teste: peça algo ao Claude, vá para outra aba, e espere a notificação aparecer.
