# pi-packages

Dmitri's owned fork of [TungLamC/pi-packages](https://github.com/TungLamC/pi-packages), containing independently published [Pi](https://pi.dev) packages.

## Owned inline-skills installation

Install this fork at a reviewed commit:

```bash
pi install git:github.com/dimajarkov/pi-packages@<commit>
```

The repository's root Pi manifest exposes only inline-skills, not the unrelated lark-cli package or its skills.
Dmitri's dotfiles pin the reviewed commit used on his machine.
Remove the original `npm:@tunglam/pi-inline-skills` declaration when switching to avoid loading the extension twice.
The original npm package and its publishing workflows remain upstream-owned; this fork is consumed directly through Git, without publishing under the original author's npm scope.

## Packages

| Package | Description | Install |
| --- | --- | --- |
| [`@tunglam/pi-inline-skills`](packages/pi-inline-skills) | Codex-style inline `$skill` references for Pi | `pi install npm:@tunglam/pi-inline-skills` |
| [`@tunglam/pi-lark-cli`](packages/pi-lark-cli) | Official lark-cli binary plus all official `lark-*` skills, synced with upstream releases | `pi install npm:@tunglam/pi-lark-cli` |

Each directory under `packages/` is an independent npm package with its own version and Pi manifest.
The repository root stays private for npm publishing, while its Pi manifest provides the owned inline-skills Git installation.

## Development

Requires Node.js 22 or newer.

```bash
npm install
npm run check
npm run pack:dry-run
```

Run a command for one workspace:

```bash
npm test --workspace=@tunglam/pi-inline-skills
npm run typecheck --workspace=@tunglam/pi-inline-skills
```

Test a package directly with Pi:

```bash
pi -e ./packages/pi-inline-skills
```

## Publishing

Packages are versioned and published independently through package-specific GitHub OIDC workflows.
After the package version is committed and CI passes, push an annotated tag matching the full npm
package name and version, such as `@tunglam/pi-inline-skills@0.1.3`.

`@tunglam/pi-lark-cli` normally needs no manual releases: an hourly workflow tracks upstream
lark-cli releases and commits, tags, and publishes automatically.

## License

MIT. See each package for package-specific attribution.
