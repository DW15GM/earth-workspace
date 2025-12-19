# Repository Guidelines

## Project Structure & Module Organization
- This repo is a virtual monorepo that coordinates multiple Earth repos without merging them.
- `.meta` maps repo names to GitHub URLs for `meta` cloning.
- `tools/cli/src` holds the TypeScript source for the `earth` CLI; `tools/cli/dist` is the compiled output (keep both in sync).
- `earth-*` and `dropshipearth/` directories are cloned sub-repos and are gitignored here.
- `earth-shared/` is the SSOT repo containing ADRs, playbooks, and work orders.

## Build, Test, and Development Commands
```bash
npm install                    # install workspace tooling
npm run setup                  # clone/update sub-repos using .meta
npm run sync                   # pull latest main for each sub-repo
npm run status -- --pr=123     # unified PR/CI/deploy status
npm run test -- --repo earth-core  # run tests inside a sub-repo
```
If you change `tools/cli/src`, rebuild with:
```bash
npx tsc -p tools/cli/tsconfig.json
```

## Coding Style & Naming Conventions
- TypeScript CLI code uses 2-space indentation, single quotes, and semicolons; follow existing patterns in `tools/cli/src`.
- Keep CLI commands small and focused; prefer explicit options and helpful console output.
- Directory names use lowercase with hyphens (e.g., `earth-ecommerce/`).

## Testing Guidelines
- This repo does not define its own unit tests; `npm run test` delegates to a target repo.
- Pass `--repo <name>` to test a cloned repo (e.g., `earth-ads`, `earth-core`).
- Keep test outputs clean; do not commit generated coverage or `.next/` artifacts.

## Commit & Pull Request Guidelines
- Commit messages follow `type: summary` (seen examples: `feat: ...`, `docs: ...`).
- Always open a PR to `main`; no direct commits to base branches.
- PRs should include a concise summary, test command(s) run, and linked work order/issue when applicable.
- Auto-merge is preferred when checks are green.

## Agent-Specific Instructions
- Follow the global agent constitution at `/Users/drakewu/.codex/AGENTS.md`.
- Treat `earth-shared/` as the SSOT for ADRs, playbooks, and work orders.

## Security & Configuration
- Do not commit secrets. Env values are SSOT-owned in `earth-shared/` (see ADRs and playbooks there).
- This repository is local tooling only and should not be deployed.
