## Stein Project

Open-source tools for Minecraft, by [Breno Xavier](https://github.com/brenoxavier).

Stein started as a platform for the Minecraft 1.8.9 client and is growing into more: Stein Bot, a Minecraft bot,
and tools for servers are next.

**[Download the Stein Client](https://github.com/Stein-Project/stein-client/releases/latest)** ·
**[Discord](https://discord.gg/MEHE9b5bjj)**

### Minecraft 1.8.9 client

Minecraft 1.8.9 on **Java 25 and LWJGL 3**, with its own renderer that makes the game faster **without changing how
it looks**, a mod platform with a small, stable API, a launcher and mods.

| | What it is | Licence |
|---|---|---|
| [Stein Client](https://github.com/Stein-Project/client) | The launcher: open source | MPL-2.0 |
| [Stein Bridge](https://github.com/Stein-Project/bridge), [Stein Loader](https://github.com/Stein-Project/loader), [installer](https://github.com/Stein-Project/installer) | The engine, the mod platform and its installer: open source | MPL-2.0 |
| **Stein mods** | [HUD](https://github.com/Stein-Project/hud), [Connect](https://github.com/Stein-Project/connect), [Keybind](https://github.com/Stein-Project/keybind), [Replay](https://github.com/Stein-Project/replay): open source | MPL-2.0 |
| **Third-party mods** | Mods by other authors: the player adds them in the Stein Client, which keeps them updated ([how to publish one](https://github.com/Stein-Project/stein-sdk#publishing-your-mod)) | Their author's |
| **[Stein SDK](https://github.com/Stein-Project/stein-sdk/releases/latest)** and the mod API | Everything to write your own mod: the API, a Gradle plugin, a template and an example ([source](https://github.com/Stein-Project/sdk)) | MIT |

### Principles

- **Nothing from Mojang is redistributed.** The game is patched on the player's machine, from the player's own copy.
- **Invisible by default.** Optimizations that change nothing the player sees are on by default, after being measured.
  Anything that changes what the player sees or does is opt-in.
- **Game logic stays vanilla in the client.** The Stein client works on any vanilla server.

### Using and contributing

**Using Stein in a product** (a launcher, another client, a modpack or a service): the Stein Client, the Bridge, the
Loader, the installer and the mods can be used under the MPL-2.0 (changes to their files stay open source); the Stein
name and logo follow the [trademark policy](https://github.com/Stein-Project/.github/blob/main/TRADEMARK.md). Playing, streaming, making videos and
using Stein on servers are free.

**Contributing to any open-source Stein repository:** read the [contributing guide](https://github.com/Stein-Project/.github/blob/main/CONTRIBUTING.md)
and the [trademark policy](https://github.com/Stein-Project/.github/blob/main/TRADEMARK.md).

<sub>Not an official Minecraft product. Not approved by or associated with Mojang or Microsoft.</sub>
