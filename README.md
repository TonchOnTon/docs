# tonch Mintlify docs

User-facing documentation for [tonch.app](https://tonch.app), formatted as a Mintlify site.

## Local preview

```bash
# from this directory
npx mintlify dev
```

Mintlify's CLI serves the docs at `http://localhost:3000` with live reload. The first run installs the CLI globally if it isn't already.

## Deploy

Two options:

1. **Mintlify Cloud** (recommended). Connect this repo at [mintlify.com](https://mintlify.com); `docs.json` lives at the repo root so no subdirectory configuration is needed. Docs auto-deploy on every push to `main`. Mintlify hosts at a `*.mintlify.app` subdomain by default; you can CNAME it to `docs.tonch.app` once the DNS is ready.
2. **Self-host.** `npx mintlify build` produces a static export. Serve it from any static host.

## Editing

Each page is an MDX file with frontmatter:

```mdx
---
title: Page title
description: One-line description used in <head> + nav.
---

Body content. Markdown plus Mintlify's React components (<Note>, <Warning>, <Steps>, <Card>, <CodeGroup>, etc.).
```

Internal links use root-relative paths: `/trading/overview`, `/launching/launch-form`, etc. Don't include the `.mdx` extension.

The navigation tree lives in `docs.json` → `navigation.groups`. Add a new page by creating the MDX file **and** adding it to the appropriate group's `pages` array.

## Source-of-truth notes

The application source for tonch lives in a separate repository at [github.com/TonchOnTon/tonch](https://github.com/TonchOnTon/tonch).

- **Calibration constants** (1B supply, 800M for-sale, 1000 TON target, etc.) are duplicated between these docs and `tonlaunch/contracts/params.fc` + `tonlaunch/scripts/deploy/deploy-mainnet.ts` in the app repo. If calibration changes there, mirror the new values here.
- **Contract addresses** are duplicated between `reference/contracts.mdx` here and `DEPLOYMENTS.md` in the app repo. Keep them in sync.
- **FAQ copy** intentionally diverges from the on-chain landing FAQ at `tonlaunch/components/landing/LandingSections.tsx` in the app repo — the landing page is simplified for first-time visitors; these docs are precise for readers who want the actual numbers.
