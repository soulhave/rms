# rms

Marketplace pessoal de plugins do **Ramon Mendes** para o [Claude Code](https://docs.claude.com/claude-code).

Contém o plugin `rms` com skills e utilitários de uso geral.

---

## Instalação

Dentro de qualquer sessão do Claude Code, rode em sequência:

```
/plugin marketplace add soulhave/rms
/plugin install rms@rms
/reload-plugins
```

O `/reload-plugins` é necessário pra carregar as skills na sessão atual. Em sessões novas o reload é automático.

Verifique com:

```
/plugin
```

Pronto. As skills ficam disponíveis com o prefixo `/rms:` (ex.: `/rms:ola`).

### Instalar uma versão específica

Você pode fixar a marketplace numa **tag** ou **branch**:

```
/plugin marketplace add soulhave/rms#v0.1.0
/plugin install rms@rms
/reload-plugins
```

> Pinning é feito no nível da marketplace, não do plugin individual.

---

## Skills disponíveis

| Comando | Descrição |
|---|---|
| `/rms:ola [nome]` | Cumprimenta o usuário em português (skill de exemplo) |
| `/rms:traduzir <idioma>` | Traduz conteúdo para o idioma alvo, preservando formatação |

---

## Atualizações

O Claude Code verifica atualizações no **startup**. Para forçar:

```
/plugin marketplace update rms
```

Para reinstalar a versão mais recente:

```
/plugin install rms@rms
```

### Como o versionamento funciona

- Esta marketplace usa o campo `version` em `.claude-plugin/plugin.json` (semver).
- Releases são marcados como **tags git** (`v0.1.0`, `v0.2.0`, …).
- O Claude Code só oferece atualização quando o `version` no manifesto muda.
- Se você pinou numa tag, **fica preso nela** até rodar `/plugin marketplace add` com outra tag.

---

## Desinstalar

```
/plugin uninstall rms@rms
/plugin marketplace remove rms
```

---

## Estrutura do repo

```
rms/
├── .claude-plugin/
│   ├── marketplace.json     # lista os plugins desta marketplace
│   └── plugin.json          # manifesto do plugin "rms"
├── skills/
│   ├── ola/SKILL.md         # skill de exemplo
│   └── traduzir/SKILL.md    # tradução de conteúdo
├── .gitignore
├── LICENSE
└── README.md
```

---

## Desenvolvimento local

Como este repo é uma **marketplace**, pra testar mudanças sem dar push você registra o diretório local como marketplace via `file://`.

Adicione em `~/.claude/settings.json`:

```json
{
  "pluginMarketplaces": [
    "file:///caminho/absoluto/para/rms"
  ]
}
```

Depois, na sessão do Claude Code:

```
/plugin install rms@rms
/reload-plugins
```

A cada mudança em arquivos do plugin, rode `/reload-plugins` pra recarregar.

### Onde o plugin é cacheado

Plugins instalados ficam em:

```
~/.claude/plugins/cache/<marketplace>/<plugin>/<version>/
```

Útil pra inspecionar o que o Claude Code de fato carregou.

---

## Licença

MIT
