# Módulo 3 — Contexto e Memória

## O que é o CLAUDE.md
É um arquivo de texto que o Claude lê automaticamente no início de cada sessão. É onde você coloca regras, preferências e contexto do projeto.

## Onde ficam os CLAUDE.md
| Local | Escopo |
|---|---|
| `~/.claude/CLAUDE.md` | Global — vale para todos os projetos |
| `.claude/CLAUDE.md` dentro de um projeto | Só para aquele projeto |

## O que colocar no CLAUDE.md
- Seu perfil (quem você é, seu nível técnico)
- Preferências de resposta (idioma, estilo, tamanho)
- Regras de comportamento ("sempre pergunte antes de apagar")
- Contexto do projeto ("este projeto é um sistema de agentes de IA")

## O que NÃO colocar
- Informações que mudam todo dia (use memória automática para isso)
- Código ou instruções técnicas longas
- Mais de 175 linhas — impacta performance

## Memória pessoal vs memória de projeto
- **Pessoal** (`~/.claude/CLAUDE.md`): suas preferências como usuária
- **Projeto** (`.claude/CLAUDE.md` dentro do projeto): contexto específico daquele projeto

## Exercício
Abra seu `~/.claude/CLAUDE.md` e adicione uma linha dizendo qual é o seu objetivo principal ao usar o Claude Code.
