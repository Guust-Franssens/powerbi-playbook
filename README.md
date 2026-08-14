# Power BI Playbook

Reusable skills for **GitHub Copilot CLI** and **Claude Code** that get a Power BI semantic model
production-ready: making it answer natural-language questions correctly, and avoiding the PBIR and
TMDL defects that pass every validator and then break at open, refresh or render.

Every skill is **source-tool agnostic** — the input is already a Power BI model — so they apply
equally to a Tableau, Qlik or Cognos migration, and to greenfield Power BI work.

## Install

```
/plugin marketplace add Guust-Franssens/powerbi-playbook
/plugin install powerbi-playbook@powerbi-playbook-collection
```

## What's included

| Skill | Use it for |
|---|---|
| `powerbi-ai-readiness` | Descriptions, enumerated categorical domains, model-level AI instructions (`CustomInstructions`), and the `qnaEnabled` switch that silently voids all of it |
| `powerbi-report-gotchas` | PBIR authoring and Desktop verification: defects that pass `validate` but render wrong, conditional-formatting encodings, azureMap/scatter/matrix recipes |
| `powerbi-semantic-model-gotchas` | TMDL and DAX pitfalls that crash Desktop on open, fail to bind, or throw only at query time - each one paid for by a real debugging cycle |

## Why a plugin and not a repo-local skill

A skill committed to a consuming repo's `.github/skills/` is **not** registered inside a Copilot
custom-agent subagent — the `skill` tool rejects the name:

```
Skill "<name>" not found. Available skills: ...
```

Plugin-provided skills *are* registered, so an agent persona can reference them **by name** instead
of reading a file path. That is the entire reason this marketplace exists.

## Client support

Both clients read the root `.claude-plugin/marketplace.json` as the catalogue. Claude Code
*additionally* requires this plugin's own `plugins/powerbi-playbook/.claude-plugin/plugin.json`, which is
what it uses to recognise, version and update the plugin.

That asymmetry is worth knowing if you fork this: omit the per-plugin manifest and `marketplace add`
still succeeds in both clients while `plugin install` succeeds only in Copilot CLI — a plugin half
its audience cannot install, with nothing in the build output to show for it.

## Source

Generated from [Guust-Franssens/tableau-to-powerbi-migration](https://github.com/Guust-Franssens/tableau-to-powerbi-migration) by `scripts/build_plugin.py`.
Each skill folder is self-contained — `SKILL.md` plus its own `scripts/` and `tests/` — and the
source repo's CI proves that by copying the folder to a temp directory and running its tests there
with the source repo unimportable.

Do not edit these files here; edit them in the source repo and re-publish.
