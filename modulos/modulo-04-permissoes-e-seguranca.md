# Módulo 4 — Permissões e Segurança

## Como funciona o sistema de permissões
O Claude Code pede autorização antes de executar ações. Você pode configurar o que é automático, o que ele pergunta, e o que é bloqueado.

## Os 3 níveis
| Nível | O que significa |
|---|---|
| `allow` | Claude executa sem perguntar |
| Padrão (sem configuração) | Claude pergunta antes de executar |
| `deny` | Claude nunca executa, mesmo que você peça |

## Onde ficam as permissões
No arquivo `.claude/settings.json` dentro do projeto (ou `~/.claude/settings.json` para configuração global).

## Exemplo de settings.json
```json
{
  "permissions": {
    "allow": [
      "Read",
      "Bash(git status)",
      "Bash(git log)"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(curl * | bash *)"
    ]
  }
}
```

## O que NUNCA autorizar automaticamente
- `rm -rf` — apaga arquivos sem confirmação
- `curl | bash` — baixa e executa código desconhecido da internet
- Comandos que sobem código para produção sem revisão

## Exercício
Abra seu `settings.json` e identifique o que está no `allow` e no `deny`. Faz sentido para você?
