# Contributing to Stein

Thanks for your interest! Bug reports, ideas and pull requests are welcome. This guide applies to every
repository of the Stein Project. Each repository also has its own `CONTRIBUTING.md` with what is specific to it
(how to build, what to test).

- [How the project is run](#how-the-project-is-run)
- [Before you start](#before-you-start)
- [Rules that are not negotiable](#rules-that-are-not-negotiable)
- [Setting up](#setting-up)
- [Code style](#code-style)
- [Testing your change](#testing-your-change)
- [Commits and pull requests](#commits-and-pull-requests)
- [Compatibility](#compatibility)
- [Contributor License Agreement](#contributor-license-agreement)
- [Licence](#licence)

## How the project is run

Stein is created and maintained by [Breno Xavier](https://github.com/brenoxavier), who has the final say on what
goes in (see [GOVERNANCE.md](GOVERNANCE.md)). Every pull request is reviewed before it is merged, and a working,
well-tested change can still be declined if it does not fit where the project is going. Forks are welcome: read
the [trademark policy](TRADEMARK.md) first — a modified version needs its own name and must credit Stein.

Be kind and constructive: see the [Code of Conduct](CODE_OF_CONDUCT.md).

## Before you start

- **Small fixes** (typos, clear bugs with an obvious fix): just open a pull request.
- **Anything bigger** (a feature, a new API event, a refactor, a new optimization): **open an issue first** and
  wait for a go-ahead. It saves you from writing something that will not be merged.
- **Security problems**: never in a public issue — see [SECURITY.md](SECURITY.md).
- Look for issues labelled `good first issue` if you want somewhere to start.

## Rules that are not negotiable

- **Nothing from Mojang/Minecraft in the repository.** No game code, no game assets, no decompiled sources, no MCP
  mapping files. The game is patched at runtime, on the player's machine, from the player's own copy; the build
  downloads what it needs to compile into `build/`, which is never committed.
- **Nothing copied from other clients or mods** (OptiFine, Lunar, Sodium and the like), including decompiled or
  "translated" code. Reading public documentation for ideas is fine; copying is not.
- **Game logic and physics stay identical to vanilla.** Stein changes how the game is drawn and what the client
  offers, never how the game plays. Stein must keep working on any vanilla server.
- **Invisible by default.** An optimization that changes nothing the player sees may be on by default only if it:
  1. has a verification mode that compares it with the game's own computation and reports divergences
     (`-Dsteinbridge.opt.check*` / `-Dsteinbridge.gfx.*Check`);
  2. has a kill switch that turns it off (`-Dsteinbridge.opt.vanilla*` or a `steinbridge.gfx.*` option);
  3. shows a measured gain.

  Anything that changes what the player sees or does is opt-in, off by default.
- **Be honest with servers.** No features that play for the player or give a combat advantage (automated clicks,
  extended reach, seeing through walls and the like).

## Setting up

You need **Windows with Git Bash** (the build scripts are bash; Linux and macOS support for the build is welcome),
**JDK 25**, a graphics card with **OpenGL 4.1** or newer, and **Minecraft 1.8.9** installed (or `tools/fetch-mc.sh` in the bridge, which downloads it from
Mojang into `build/mc`).

Clone the repositories you need side by side; most changes need all three:

```
stein/
├── bridge/   https://github.com/Stein-Project/bridge
├── loader/   https://github.com/Stein-Project/loader
└── sdk/      https://github.com/Stein-Project/sdk
```

Then follow the README of each repository, in that order. If your JDK is not at the default path, export
`JDK=/path/to/jdk-25`.

## Code style

- **Java: [Google Java Style](https://google.github.io/styleguide/javaguide.html), AOSP variant** (4-space
  indentation, 100 columns), applied by `google-java-format --aosp`. Run `tools/format.sh` before committing; CI
  rejects unformatted code.
- **English** for everything in the repository: identifiers, comments, Javadoc, log messages. Text the player sees
  goes in the translation files (`assets/*/lang/en_US.lang`, `pt_BR.lang`, `es_ES.lang`), never hard-coded.
- **Comments explain why**, not what. Every class starts with a Javadoc whose first sentence says what it is.
- **Small, single-purpose classes and methods.** As a guide: classes under ~800 lines, methods under ~100, unless
  there is a reason (a flat hot loop), stated in a comment.
- **Hot paths** (anything per frame, per entity, per chunk, per vertex): no allocations, boxing, streams,
  capturing lambdas or extra virtual dispatch. Prefer `static` methods and primitive arrays.
- **New source files** start with the licence header of their repository (copy it from any file nearby). In the
  Loader, the `api` package uses the MIT header; everything else uses the MPL-2.0 header.
- **Log messages** start with a short lowercase tag in brackets: `[gfx]`, `[loader]`, `[terrain]`.

## Testing your change

Every pull request must build cleanly with the full build of the repositories it touches (each README lists the
commands; they run the coverage, preflight, API and access checks). Then, depending on what you changed:

| You changed | Also run |
|---|---|
| Rendering, the engine or a patcher rule | `loader/tools/verify.sh <world>`: plays a world with every verification mode on and fails on any divergence or exception |
| The mod API | the SDK's `tools/sdk-test.sh` and the example mod |
| Menus, HUD or anything visual | look at it in the game, and put before/after screenshots in the pull request |
| Performance | numbers: frame time before and after, same scene, same machine |

Describe in the pull request what you ran and what you saw.

## Commits and pull requests

- **One subject per pull request.** Refactors and behaviour changes go in separate pull requests.
- **Commit messages**: imperative English summary of at most 72 characters (`Fix sky flicker after a dimension
  change`), a blank line, then why the change is needed. Reference the issue (`Fixes #123`).
- Keep the history readable: pull requests are squash-merged by default.
- Do not bump version numbers or write release notes: the maintainer does that at release time. Do describe any
  change the player will notice, in the pull request, so it can go in the notes.
- Update the documentation (README, Javadoc, the SDK guide) in the same pull request when behaviour changes.

## Compatibility

- **The mod API** (`dev.xavier.stein.loader.api`) is checked against `loader/api/stein-api.txt` on every build.
  Removing or changing a public signature breaks mods and needs an issue and a decision first. Additions are fine
  when discussed; new members are marked `@Experimental(since = "x.y.z")` until they settle.
- **Player data**: config file names, JSON keys, translation keys, `-Dsteinbridge.*` property names and on-disk
  folders are part of what players already have. Do not rename them; add new ones instead.
- **Patcher entry points**: methods named in `bridge/patcher/redirects-*.tsv` are called from the patched game.
  Changing their name or descriptor needs the rule changed in the same commit; the coverage check catches mistakes.

## Contributor License Agreement

Before your first pull request is merged, you need to sign the [Contributor License Agreement](CLA.md). The CLA
bot asks you on the pull request, and you sign once by replying with a comment.

The CLA gives the project owner, Breno Xavier, a broad licence to your contribution, including the right to
relicense it. You keep your copyright, and the history keeps your name.

## Licence

Stein is licensed under the Mozilla Public License 2.0. The Stein SDK, its template and examples, and the Stein
Loader mod API are licensed under MIT. Contributions are accepted under the licence of the file you change.
