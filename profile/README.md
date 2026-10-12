## Stein

A Minecraft 1.8.9 client by [Breno Xavier](https://github.com/brenoxavier).

Stein runs Minecraft 1.8.9 on **Java 25 and LWJGL 3**, with its own renderer that makes the game faster **without
changing how it looks**, and a mod platform with a small, stable API.

**[Download the Stein Client](https://github.com/x4vieer/stein-client/releases/latest)** ·
**[Discord](https://discord.gg/MEHE9b5bjj)**

| | What it is | Licence |
|---|---|---|
| **Stein Client** | The launcher | Proprietary |
| [Stein Bridge](https://github.com/Stein-Project/bridge), [Stein Loader](https://github.com/Stein-Project/loader) | The engine and the mod platform: open source | MPL-2.0 |
| **Stein mods** | [HUD](https://github.com/Stein-Project/hud), [Connect](https://github.com/Stein-Project/connect), [Keybind](https://github.com/Stein-Project/keybind), [Replay](https://github.com/Stein-Project/replay): open source | MPL-2.0 |
| **[Stein SDK](https://github.com/Stein-Project/stein-sdk/releases/latest)** and the mod API | Everything to write your own mod: the API, a Gradle plugin, a template and an example ([source](https://github.com/Stein-Project/sdk)) | MIT |

**Principles**

- **Nothing from Mojang is redistributed.** The game is patched on the player's machine, from the player's own copy.
- **Invisible by default.** Optimizations that change nothing the player sees are on by default, after being measured.
  Anything that changes what the player sees or does is opt-in.
- **Game logic stays vanilla.** Stein works on any vanilla server.

**Using Stein in a product** (a launcher, another client, a modpack or a service): the Bridge, the Loader and the
mods can be used under the MPL-2.0 (changes to their files stay open source); the Stein name and logo follow the
[trademark policy](https://github.com/Stein-Project/.github/blob/main/TRADEMARK.md), and the Stein Client needs a
licence from the author: write to [x4vieer@proton.me](mailto:x4vieer@proton.me). Playing, streaming, making videos and
using Stein on servers are free.

**Contributing to the Bridge, the Loader and the mods:** read the [contributing guide](https://github.com/Stein-Project/.github/blob/main/CONTRIBUTING.md)
and the [trademark policy](https://github.com/Stein-Project/.github/blob/main/TRADEMARK.md).

<sub>Not an official Minecraft product. Not approved by or associated with Mojang or Microsoft.</sub>
