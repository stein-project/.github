# Contributing to Stein

Thanks for your interest! Stein Bridge, Stein Loader, the installer, the Stein SDK and the Stein mods are open
source, and bug reports, ideas and pull requests to them are welcome. This guide applies to every public Stein
Project repository; each one also has its own README (and some their own CONTRIBUTING) with what is specific to it
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
well-tested change can still be declined if it does not fit where the project is going. Forks of the mods are
welcome: read the [trademark policy](TRADEMARK.md) first — a modified mod needs its own name and must credit the
original.

Be kind and constructive: see the [Code of Conduct](CODE_OF_CONDUCT.md).

## Before you start

- **Small fixes** (typos, clear bugs with an obvious fix): just open a pull request.
- **Anything bigger** (a feature, a new option, a refactor): **open an issue first** and wait for a go-ahead. It
  saves you from writing something that will not be merged.
- **Security problems**: never in a public issue — see [SECURITY.md](SECURITY.md).
- Look for issues labelled `good first issue` if you want somewhere to start.

## Rules that are not negotiable

- **Nothing from Mojang/Minecraft in the repository.** No game code, no game assets, no decompiled sources, no
  mapping files. Mods are built with the Stein SDK, which reads the player's own copy of the game.
- **Nothing copied from other clients, mods or servers** (OptiFine, Lunar, Sodium and the like), including decompiled
  or "translated" code. Reading public documentation for ideas is fine; copying is not.

For the Minecraft 1.8.9 client repositories (Bridge, Loader, installer, SDK and mods), also:

- **Game logic and physics stay identical to vanilla.** A mod changes what the client shows and offers, never how
  the game plays. Mods must keep working on any vanilla server.
- **Be honest with servers.** A mod says it is there and lists what a server can turn off. The base mods, the ones
  the Stein Client brings, have no features that play for the player or give a combat advantage (automated clicks,
  extended reach, seeing through walls and the like). Mods for specific servers are official extras: the player adds
  them and chooses what to turn on, and a server can turn them off.
- **Mods use the Stein API**, not the game's OpenGL directly: the Stein renderer runs in an OpenGL core context.

## Setting up

For the Minecraft 1.8.9 client repositories, you need **JDK 25 or newer**, a graphics card with **OpenGL 4.1** or
newer, **Minecraft 1.8.9** installed, and the **[Stein Client](https://stein-project.github.io/downloads/)**
to play with your change. The [Stein SDK](https://github.com/Stein-Project/sdk) guide explains the
API and how a mod is built; each mod's README has its own commands.

## Code style

- **Java: [Google Java Style](https://google.github.io/styleguide/javaguide.html), AOSP variant** (4-space
  indentation, 100 columns), applied by `google-java-format --aosp`. CI rejects unformatted code.
- **English** for everything in the repository: identifiers, comments, Javadoc, log messages. Text the player sees
  goes in the translation files (`assets/*/lang/en_US.lang`, `pt_BR.lang`, `es_ES.lang`), never hard-coded.
- **Comments explain why**, not what. Every class starts with a Javadoc whose first sentence says what it is.
- **Small, single-purpose classes and methods.** As a guide: classes under ~800 lines, methods under ~100, unless
  there is a reason (a flat hot loop), stated in a comment.
- **Hot paths** (anything per frame or per entity): no allocations, boxing, streams, capturing lambdas or extra
  virtual dispatch.
- **New source files** start with the licence header of their repository (copy it from any file nearby).

## Testing your change

Every pull request must build cleanly. For the client repositories, then play with it in the game, with the latest
Stein Client:

| You changed | Also show |
|---|---|
| Anything visual (HUD, menus, options) | before/after screenshots in the pull request |
| Options or config | that an existing config from the previous version still loads |
| Performance | numbers: frame time before and after, same scene, same machine |

Describe in the pull request what you ran and what you saw.

## Commits and pull requests

- **One subject per pull request.** Refactors and behaviour changes go in separate pull requests.
- **Commit messages**: imperative English summary of at most 72 characters (`Fix the armor bar after a respawn`),
  a blank line, then why the change is needed. Reference the issue (`Fixes #123`).
- Keep the history readable: pull requests are squash-merged by default.
- Do not bump version numbers or write release notes: the maintainer does that at release time. Do describe any
  change the player will notice, in the pull request, so it can go in the notes.

## Compatibility

- **Player data**: config file names, JSON keys, translation keys and on-disk folders are part of what players
  already have. Do not rename them; add new ones instead.
- **The mod API** is versioned by the Stein Loader. A mod declares the minimum Loader it needs in `steinmod.json`
  (`"loader"`); raise it only when the change uses something newer.

## Contributor License Agreement

Before your first pull request is merged, you need to sign the [Contributor License Agreement](CLA.md). The CLA
bot asks you on the pull request, and you sign by replying with the sentence it gives you (once in each repository).

The CLA gives the project owner, Breno Xavier, a broad licence to your contribution, including the right to
relicense it. You keep your copyright, and the history keeps your name.

## Licence

The Stein Client, Stein Bridge, Stein Loader, the installer and the Stein mods are licensed under the Mozilla Public
License 2.0. The Stein SDK, its template and examples, and the Stein Loader mod API are licensed under MIT. Each
repository says its licence in its LICENSE file.
Contributions are accepted under the licence of the file you change.
