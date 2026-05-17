# rms

Marketplace pessoal de plugins do **Ramon Mendes** para o [Claude Code](https://docs.claude.com/claude-code).

Contém o plugin `rms` com skills e utilitários de uso geral.

---

## Instalação

Dentro de qualquer sessão do Claude Code, rode:

```
/plugin marketplace add soulhave/rms
/plugin install rms@rms
```

Pronto. As skills ficam disponíveis com o prefixo `/rms:`.

### Instalar uma versão específica

Você pode fixar a marketplace numa **tag** ou **branch**:

```
/plugin marketplace add soulhave/rms#v0.1.0
/plugin install rms@rms
```

> Pinning é feito no nível da marketplace, não do plugin individual.

---

## Skills disponíveis

| Comando | Descrição |
|---|---|
| `/rms:ola [nome]` | Cumprimenta o usuário em português (skill de exemplo) |

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
│   └── ola/SKILL.md         # skill de exemplo
└── README.md
```

---

## Desenvolvimento local

Pra testar mudanças sem precisar dar push:

```bash
claude --plugin-dir /caminho/para/rms
```

Dentro do Claude Code, depois de editar arquivos:

```
/reload-plugins
```

---

## Licença

MIT
