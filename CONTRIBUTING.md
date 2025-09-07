# Contributing

## TL;DR
1. Fork → branch from `dev` (e.g. `feat/x`).
2. Run `pnpm i`, make changes, add tests if applicable.
3. Open PR into `dev`. CI must pass (format check, pack preview).
4. Maintainers merge, then we cut a release from `main`.

## Project flow
- Daily work → `dev`
- Release: `dev` → `main` (via short-lived `release/vX.Y.Z` PR), then tag `vX.Y.Z`.
- After release, we back-merge `main` → `dev` (auto PR).

## Commands
- Format check example (no changes): `pnpm -C example exec prettier --check .`
- Pack preview: `pnpm pack --silent` (lists tarball path)

## Commit style
Conventional-ish: `feat:`, `fix:`, `chore:`, `docs:`. Sign commits/tags if possible.
