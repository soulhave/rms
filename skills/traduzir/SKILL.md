---
description: Traduz conteúdo (texto, código com comentários, markdown) para o idioma alvo, preservando formatação
---

Traduza o conteúdo fornecido pelo usuário para o idioma especificado em $ARGUMENTS.

## Como interpretar $ARGUMENTS

- Se `$ARGUMENTS` contém um idioma (ex.: "inglês", "espanhol", "en", "es", "pt-BR"), use-o como **idioma alvo**.
- Se `$ARGUMENTS` está vazio, pergunte ao usuário qual o idioma alvo antes de prosseguir.
- Se `$ARGUMENTS` contém texto adicional além do idioma, considere-o como instrução extra (ex.: "inglês formal", "espanhol coloquial").

## O que traduzir

Traduza o que o usuário fornecer:
- Mensagem de texto direta
- Trecho colado na conversa
- Arquivo referenciado (use a tool Read)
- Múltiplos arquivos (traduza cada um e mostre os caminhos resultantes)

Se não estiver claro o que traduzir, pergunte.

## Regras de tradução

1. **Preserve formatação**: markdown, indentação, quebras de linha, listas, tabelas, código.
2. **Não traduza código**: apenas comentários e strings voltadas ao usuário final. Identificadores (nomes de variáveis, funções, classes) ficam intactos.
3. **Preserve termos técnicos** consagrados (ex.: "deploy", "commit", "endpoint") a menos que o idioma alvo tenha equivalente natural.
4. **Detecte o idioma de origem** automaticamente — não pergunte.
5. **Mantenha o tom** do original (formal, casual, técnico).
6. **Sinalize ambiguidades**: se uma frase tem múltiplas traduções razoáveis e a escolha afeta o sentido, mostre as alternativas em vez de adivinhar.

## Saída

- Para texto curto: mostre a tradução diretamente na resposta.
- Para arquivos: pergunte se deve **substituir o original**, **criar arquivo novo** (ex.: `README.en.md`) ou **só mostrar na conversa**.
- Para conteúdo longo (mais de ~200 linhas): sempre proponha criar arquivo novo.
