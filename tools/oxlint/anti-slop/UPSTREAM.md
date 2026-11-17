# Vendored anti-slop provenance

- Source: https://github.com/K-Mistele/anti-slop at `b7c1619b4d51b4815e89ba3700a975a6ec54b8c3`; README/install/update reviewed.
- Fresh installation into the owned `edmundmiller/linear-agent-bridge` fork at base `cb09637071dadf7a8bf5314310e1457ec4dd44d4`. Existing attribution, MIT license, upstream repository metadata, application conventions, dependencies, and build remain unchanged. No existing anti-slop fork/config was found.
- Plugin bytes match the incoming skill assets, plus this record and upstream MIT `LICENSE`; retain nested Stylistic license/provenance. Jev build bytes match the pinned asset with fork commit `fd3e4b1ad3b8fa7c0d08cdc92633e33c7e662f9e`, including its license and build record.
- Exact `oxlint` / `@oxlint/plugins` `1.86.0` pair, upstream-tested rather than registry latest 1.94.0, and local development-only Jev file dependency. npm and existing lockfile retained; TypeScript 5 and runtime unchanged. No direct Effect dependency; no Effect/tsgo activation.
- 15 compatible Core/native errors plus seven Fowler warnings in normal/editor lint. All 22 Core/native rules remain errors in the explicit strict proposal. Jev/diff commands are opt-in only; ignore patterns are repeated in overlays because Oxlint does not inherit them.

## Strict proposal, pending decision

`lint:strict` reports **588 errors** on unchanged source: `no-known-value-widening` 7; `no-runtime-typeof` 20; `no-unknown-parameters` 10; `no-unknown-returns` 6; `no-unsafe-dictionary-type` 43; `require-readable-spacing` 439; `require-safety-comment-for-type-assertion` 63. These seven rules are not activated in normal/editor lint pending a scoped boundary/type/spacing policy decision. No product refactor, unsafe cast, permanent disable, or source exemption was made. Fowler reports 13 advisory warnings.

## Verification / delivery

Fresh remote check: no PRs, master only; no discoverable Amp owner. Baseline has no lint command; baseline/final `tsc --noEmit` pass. New ordinary/offline lint passes with 13 warnings, 0 errors. No test suite exists. Network-denied fake-key lint and actual changed-file review make no network attempts; in-process mocked Fowler questions distinguish whole-file from changed-function disclosure, and command-stub diff review verifies hunks/context. Root `ANTI_SLOP.md` records limits and optional backend requirements.

Edmund authorized shipping this tooling-only adoption. Validation used no Linear/OpenClaw/API calls, services, credentials, CI changes, paid/live models, or deployment. Strict source migration and full strict acceptance remain separate decisions. Recover by reverting only the focused tooling commit against the recorded base. Accountable owner: https://ampcode.com/threads/T-01a1e6aa-5f11-73a3-b161-b97848780e6b .
