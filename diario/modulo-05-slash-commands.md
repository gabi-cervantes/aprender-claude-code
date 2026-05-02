# Módulo 5 — Slash Commands Personalizados

## O que são
Atalhos que você cria para executar tarefas repetitivas com um único comando. Em vez de escrever o mesmo prompt várias vezes, você digita `/nome-do-comando`.

## Como criar
1. Crie um arquivo `.md` com as instruções
2. Salve na pasta correta
3. O nome do arquivo vira o nome do comando

## Onde salvar
| Local | Escopo |
|---|---|
| `~/.claude/commands/nome.md` | Global — funciona em qualquer projeto |
| `.claude/commands/nome.md` | Só dentro daquele projeto |

## Exemplo: comando /resumir
Arquivo: `~/.claude/commands/resumir.md`
```
Resuma em português o que foi feito nesta sessão:
- O que foi criado ou editado
- Decisões importantes tomadas
- Próximos passos sugeridos

Seja breve e direto.
```

Agora basta digitar `/resumir` para executar esse prompt.

## Ideias de comandos úteis
- `/resumir` — resume a sessão atual
- `/revisar` — revisa o código aberto
- `/seguranca` — verifica vulnerabilidades
- `/standup` — gera resumo estilo reunião diária
- `/todo` — lista pendências do projeto

## Como pedir ao Claude para criar um comando
Basta dizer: "cria um comando `/nome` que faz isso" — o Claude cria o arquivo na pasta certa automaticamente.

## Exercício
Crie um comando `/revisar` com as instruções: "Revise o código atual e liste possíveis melhorias em português, de forma simples e direta."
