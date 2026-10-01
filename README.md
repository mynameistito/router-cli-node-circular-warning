# Router CLI Node circular warning repro

Minimal TanStack Router project showing a Node.js circular-dependency warning from `@tanstack/router-core` when running the Router CLI.

## Reproduce

```sh
bun install
```

In PowerShell:

```powershell
$env:NODE_OPTIONS = '--trace-warnings'
bun run repro
```

Route generation succeeds, but Node prints a warning similar to:

```text
Warning: Accessing non-existent property 'replaceRouteChunk' of module exports inside circular dependency
    at .../node_modules/@tanstack/router-core/dist/cjs/router.cjs:835:64
```

Tested with Bun 1.4.2, `@tanstack/router-cli` 1.167.40, and `@tanstack/react-router` 1.170.41 on Windows.
