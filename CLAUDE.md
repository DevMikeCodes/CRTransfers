# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev        # Start development server with HMR
npm run build      # Type-check (tsc -b) then bundle for production
npm run lint       # Run ESLint
npm run preview    # Preview production build locally
```

No test framework is configured.

## Architecture

**Stack**: React 19 + TypeScript 6 + Vite 8

- Entry point: `index.html` → `src/main.tsx` → `src/App.tsx`
- Styles: plain CSS (`index.css` for globals, `App.css` for component styles)
- No routing, no global state management library

**TypeScript**: Strict mode is on — `noUnusedLocals`, `noUnusedParameters`, and `noFallthroughCasesInSwitch` are all enabled. The `tsconfig.json` splits into `tsconfig.app.json` (for `src/`) and `tsconfig.node.json` (for `vite.config.ts`).

**React Compiler** is enabled via Babel in `vite.config.ts`, so manual `useMemo`/`useCallback` is generally unnecessary.

**ESLint** uses the flat config format (`eslint.config.js`) with TypeScript and React Hooks rules.

## Agent skills

### Issue tracker

Issues live in GitHub Issues (`github.com/DevMikeCodes/CRTransfers`). See `docs/agents/issue-tracker.md`.

### Triage labels

Default label vocabulary (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context layout — `CONTEXT.md` + `docs/adr/` at the repo root. See `docs/agents/domain.md`.
