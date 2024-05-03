# TypeScript Incremental Compile Issue

TypesScript does NOT build files when a SymLink dependency changes.

This is an issue for `composite` and `incremental` builds.

## Steps

1. Clone repository
1. `pnpm i`
1. `pnpm build` or `pnpm tsc -b .`
1. Update `@types/vscode`: `pnpm add -D @types/vscode@1.89.0`
1. `pnpm build` -- this seems to work, but it should not because the types have changed.
1. Delete `dist` and rebuild - Now it finds 🙁 the error.


## Why is this an issue? Trust



## Environment

<details>
<summary>VSCode About Details</summary>
```
Version: 1.89.0 (Universal)
Commit: b58957e67ee1e712cebf466b995adf4c5307b2bd
Date: 2024-05-01T02:10:10.196Z
Electron: 28.2.8
ElectronBuildId: 27744544
Chromium: 120.0.6099.291
Node.js: 18.18.2
V8: 12.0.267.19-electron.0
OS: Darwin x64 23.4.0
```
</details>