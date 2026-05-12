# Módulo 7 — GitHub e Versionamento

## O que é o GitHub
Um serviço onde você guarda e sincroniza arquivos de código (e configurações). Funciona como um Google Drive, mas com histórico completo de todas as mudanças.

## Por que usar
- Não perder suas configurações se trocar de computador
- Ter histórico de tudo que você mudou
- Compartilhar projetos com outras pessoas

## Conceitos básicos
| Termo | O que significa |
|---|---|
| Repositório (repo) | A pasta do seu projeto no GitHub |
| Clone | Baixar o repositório para o seu computador |
| Commit | Salvar um ponto no histórico de mudanças |
| Push | Enviar suas mudanças para o GitHub |

## Configuração inicial (uma vez só)
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

## Fluxo básico para subir mudanças
```bash
git add .
git commit -m "descrição do que você fez"
git push
```

## Como pedir ao Claude para subir algo
Estando dentro do Claude Code, basta dizer:
> "Sobe o que fizemos hoje pro GitHub"

O Claude executa o `git add`, `git commit` e `git push` por você.

## Autenticação
O GitHub não aceita sua senha normal — exige um **token** (senha especial gerada nas configurações da sua conta). Gere em: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic).

## Exercício
Crie um arquivo `modulos/meu-primeiro-dia.md` com um resumo do que você aprendeu hoje e suba para o GitHub usando os 3 comandos acima.
