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

I'm sure you can understand. Trusting the tools that you rely on to work as expected is important. I think TypeScript is amazing and love how it has helped put Microsoft back on the Open Source map. But, when a tool works unpredictably, it ruins that trust. I trust that `tsc` will generate good code. I just don't trust that `tsc -b .` will do the right thing without deleting the `outDir` or `*.tsbuildinfo`.

This issue has been around for a long time, since the `incremental` build feature was introduced. So, I didn't use it. But recently I have needed to use the `composite` build feature due to trying to support both CommonJS and ESM Modules. So it has been biting me a lot.

I'm logging this issue with the hope that it gets fixed.

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
