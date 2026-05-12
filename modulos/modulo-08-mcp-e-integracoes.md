# Módulo 8 — MCP e Integrações Avançadas

## O que é MCP?

MCP significa **Model Context Protocol** — é um protocolo que permite o Claude se conectar a ferramentas externas.

Sem MCP, o Claude só conversa e lê arquivos locais.
Com MCP, o Claude acessa o mundo externo.

```
Sem MCP:  Você → Claude → resposta
Com MCP:  Você → Claude → Google Drive / Notion / Web / APIs → resposta
```

---

## Como instalar MCPs

### Via Claude.ai (mais simples)
Acesse as configurações do Claude.ai e adicione integrações pela interface visual. É o jeito mais fácil — sem mexer em arquivo nenhum.

MCPs disponíveis no Claude.ai:
- Google Drive
- Google Calendar
- Notion
- Canva
- GitHub
- E outros

### Via arquivo `.mcp.json` (para MCPs customizados)
Para ferramentas que não estão disponíveis no site do Claude. Você cria um arquivo `.mcp.json` na raiz do projeto:

```json
{
  "mcpServers": {
    "nome-do-mcp": {
      "command": "npx",
      "args": ["@pacote/mcp@latest"]
    }
  }
}
```

| Via Claude.ai | Via .mcp.json |
|---|---|
| Interface visual, simples | Editar arquivo manualmente |
| MCPs oficiais e populares | Qualquer MCP, inclusive customizados |
| Funciona em qualquer projeto | Configurado por projeto |

---

## O que você pode conectar via .mcp.json

**Pesquisa e dados:**
- Perplexity, Brave Search, Exa

**Produtividade:**
- Airtable, Obsidian, Todoist

**Comunicação:**
- Slack, Gmail

**Analytics:**
- Google Sheets, bancos de dados

**Automação:**
- n8n, Zapier

**Outras IAs via API:**
- GPT (API da OpenAI), Gemini (API do Google)

> Conectar outras IAs via API é técnico — o agente chama a API, recebe a resposta e traz de volta. Não abre a interface visual delas.

---

## Como um agente usa um MCP

Você instrui o agente no CLAUDE.md dele quais ferramentas usar e quando.

Exemplo — agente que pesquisa tendências e salva no Notion:

```markdown
# Agente Radar de Tendências

## Ferramentas disponíveis
- Use WebSearch para buscar tendências de IA no YouTube
- Use o Notion para criar uma página com os resultados

## Fluxo
1. Pesquise os temas de IA mais comentados essa semana
2. Identifique 5 oportunidades de vídeo
3. Crie uma página no Notion com o resumo
```

Quando acionado, o agente executa tudo sozinho — sem você precisar abrir o Notion manualmente.

---

## Exemplo prático: agente salvando no Notion automaticamente

Para um sistema de produção de vídeos para YouTube, o agente poderia ser instruído assim:

```markdown
## Ao finalizar a análise do vídeo

Use o Notion para criar uma página com:
- Título do vídeo
- Público principal
- Keyword escolhida
- Títulos recomendados
- Conceito de thumbnail
- Diagnóstico final

Salve na base "Vídeos em produção" do workspace.
```

O agente cria a página e preenche tudo automaticamente ao final do fluxo.

**O que é necessário:**
- MCP do Notion conectado (via Claude.ai)
- Instrução no CLAUDE.md dizendo onde salvar e o quê
- Estrutura no Notion já existindo (a base precisa existir antes)

---

## Tudo funciona do VS Code

Sim — você opera tudo daqui. O agente pesquisa, salva arquivos, atualiza o Notion, chama APIs. Você vê o resultado no chat sem precisar abrir nenhuma outra ferramenta.

---

## O que você já tem conectado hoje

| MCP | O que permite |
|---|---|
| Google Drive | Ler e salvar arquivos |
| Google Calendar | Ver e criar eventos |
| Notion | Criar e atualizar páginas |
| Canva | Criar e editar designs |
| WebSearch | Pesquisar na web |

---

## Exercício

Pense em uma tarefa que você faz manualmente hoje — copiar algo para o Notion, salvar um arquivo no Drive, pesquisar algo na web.

Escreva como seria a instrução no CLAUDE.md de um agente para fazer isso automaticamente:
1. Qual MCP ele usaria?
2. O que ele faria exatamente?
3. Onde salvaria o resultado?
