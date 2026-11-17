# Anti-slop tooling

This is a local, tooling-only rollout of [anti-slop](https://github.com/K-Mistele/anti-slop) at `b7c1619b4d51b4815e89ba3700a975a6ec54b8c3`, with the vendored Jev fork at `fd3e4b1ad3b8fa7c0d08cdc92633e33c7e662f9e`. `tools/oxlint/anti-slop/UPSTREAM.md` records repository-specific pending activation and evidence. All existing product source, runtime dependencies, checks, CI, and integration settings are preserved.

## Offline checks

Anti-slop commands require Node 22.18 or later. This requirement is for tooling, not a product/runtime or TypeScript migration. Existing checks retain their runtime contract. `oxlint` and `@oxlint/plugins` are both pinned to the upstream-tested `1.86.0`; move them together. The installed Core rules use the syntax tree, not the TypeScript checker.

- `npm run lint:anti-slop`: compatible Core rules as errors and seven Fowler AST smells as warnings, on maintained source only. Use `pnpm` in repositories already using it.
- `npm run lint:strict`: the complete proposed Core policy as errors, including rules with existing source findings. This command intentionally fails pending a scoped migration/policy decision; it is not a normal check or an approved exemption list.

`.oxlintrc.json` is the offline editor configuration. It does not register Jev or import an AI provider. Native Oxlint default categories are not added as an unrelated policy change; the explicitly requested native accumulating-spread companion is enabled. No direct Effect dependency exists, so Effect AST/Jev/tsgo activation is not applicable. Effect assets travel with the upstream bundle but are disabled. No compiler patch or TypeScript migration is installed.

Staged activation is approved; full strict acceptance and source migration are not. Existing normal lint gates and severities are retained. Where there was no lint command, `lint` invokes the offline configuration. Motion's Node 22 lint chain appends the compatible offline checks after its existing gates. Linear TaskNotes retains Node 20/22 ESLint unchanged, with `lint:anti-slop` supplementary on Node 22.18+ rather than forcing a runtime/CI migration. Agent assets, generated output, and vendored tooling are excluded rather than refactored. Both JSON overlays repeat the exclusions explicitly: Oxlint does not inherit the base ignore list through `extends`.

## Explicit semantic review (may cost money and disclose source)

These commands are not part of normal lint, editor checks, hooks, tests, build, or CI. Do not run them against a live provider without separate authorization. No credentials are needed for ordinary checks, and this rollout adds no secrets or credential setup.

- `npm run lint:jev`: review staged, unstaged, and untracked nonignored changed JS/TS files using the twelve Fowler questions. A tooling-only diff with no selected source succeeds without requests.
- `npm run lint:jev:full`: review all configured maintained source, regardless of changed lines.
- `npm run lint:diff -- --working --backend command --command '<review-command>'`: review the current worktree through an explicitly selected command backend. The command receives the prompt on stdin and must return the upstream JSON verdict format. The runner also supports branch/base and committed/staged modes. No judge is configured by default; it warns and skips without one. The command backend needs no additional provider packages. Direct/gateway model backends need their documented optional SDK dependencies installed separately; none are added to product dependencies here.

**Disclosure is not limited to changed lines.** Changed-file Jev file questions send the whole changed file, including untouched functions, up to the 24,000-character snippet limit. Function questions select functions overlapping changed lines and send each selected function, not only its changed lines. The preset caps matches at 60 per file; truncated/capped review is not exhaustive. Unchanged files are omitted in changed mode. Untracked files count as entirely changed. `JEV_CHANGED_ONLY` and `JEV_CHANGED_BASE` can override changed-mode behavior; `--all` selects full review unless explicitly overridden by the environment. If the plugin cannot resolve its Git diff/base, it warns and treats every line in selected files as changed, broadening function review. Test files do not receive the source-smell questions, following the upstream overlay contract; this does not exclude them from offline Core checks.

Diff review sends added/deleted lines, unchanged hunk context, file summaries, and available branch/base commit subjects/history. It can include non-source maintained configuration/documentation. The local config excludes vendored tooling, installed agent assets, generated output, lockfiles, and image evidence. Review the selected base, mode, file list, and provider before any live run. Missing credentials can skip Jev outside CI; its opt-in overlay fails when explicitly run in CI without credentials. No such CI gate is installed.

## Validation and recovery

The rollout used an in-process mock AI provider and a local command stub, never a paid/live model. Network-isolated checks with fake keys verified ordinary lint and the actual tooling-only changed-file review make zero network attempts. Mock fixtures verified whole-file disclosure, changed-function overlap filtering, and diff context. Upstream rule suites were exercised separately because vendored files are intentionally not application lint targets.

Strict activation remains a proposal, not a completed source migration. Review the pending counts in `tools/oxlint/anti-slop/UPSTREAM.md`. Recover by reverting only these tooling/config/package/lockfile additions from the recorded base; no product source was changed. Keep existing unrelated work intact.
