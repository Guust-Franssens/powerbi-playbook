# Power BI Playbook

Skills for **GitHub Copilot CLI** and **Claude Code**: portable Power BI AI-readiness policy and
two compact **Tableau-migration host contracts**, not generic PBIR/TMDL encyclopedias.

The AI skill can be used with an existing Power BI model regardless of source tool. The report and
semantic cores preserve Tableau source intent, shipped-artifact identity and evidence-bounded
handoffs; they are **not greenfield authoring guides**. General procedures belong to separately
installed upstream `powerbi-report-cli` and `semantic-model-authoring`, in the selected mode/topic.
The host repository supplies migration scripts/docs, refresh/persistence, live-source proof and
declarations; those operations are **not bundled**. Missing required owners block only their affected
operation, never permission to improvise. Optional pinned history is evidence, not a procedure.

## Install

```
/plugin marketplace add Guust-Franssens/powerbi-playbook
/plugin install powerbi-playbook@powerbi-playbook-collection
```

## What's included

| Skill | Use it for |
|---|---|
| `powerbi-ai-readiness` | Descriptions, enumerated categorical domains, model-level AI instructions (`CustomInstructions`), and the `qnaEnabled` switch that silently voids all of it |
| `powerbi-report-gotchas` | Tableau-migration report core: source grain/defaults, shipped-model binding, replay/declaration and layer handoff; requires host owners |
| `powerbi-semantic-model-gotchas` | Tableau-migration semantic core: source calculations, request roles, visual grain, current-model proof and handoff; requires host owners |

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
The AI bundle carries its own scripts/tests; CI copies code-bearing bundles into an isolated
directory and runs their tests with the source repo unimportable. The two migration cores are
knowledge-only `SKILL.md` files: copying them does **not** copy their host-repository dependencies.
Resolve the owners named by the selected core before its dependent operation. Static checks do not
prove fresh-role resolution, live data, render fidelity or durable cold reopen.

Do not edit these files here; edit them in the source repo and re-publish.
