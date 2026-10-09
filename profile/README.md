## Stein Project

Open-source tools for Minecraft, created by [Breno Xavier](https://github.com/brenoxavier).

Stein runs Minecraft 1.8.9 on **Java 25 and LWJGL 3**, with its own renderer that makes the game faster **without
changing how it looks**, and a mod platform with a small, stable API.

| Repository | What it is | Licence |
|---|---|---|
| [**bridge**](https://github.com/Stein-Project/bridge) | The engine: Java 25, LWJGL 3, Stein GFX renderer, game hooks and patcher | MPL-2.0 |
| [**loader**](https://github.com/Stein-Project/loader) | The mod platform: loads `.steinmod` files and gives them the Stein API | MPL-2.0 (API: MIT) |
| [**sdk**](https://github.com/Stein-Project/sdk) | Everything to write a mod: the API, a Gradle plugin, a template and examples | MIT |

**Principles**

- **Nothing from Mojang is redistributed.** The game is patched on the player's machine, from the player's own copy.
- **Invisible by default.** Optimizations that change nothing the player sees are on by default, after being measured.
  Anything that changes what the player sees or does is opt-in.
- **Game logic stays vanilla.** Stein works on any vanilla server.

**Contributing:** read the [contributing guide](https://github.com/Stein-Project/.github/blob/main/CONTRIBUTING.md)
and the [trademark policy](https://github.com/Stein-Project/.github/blob/main/TRADEMARK.md).

<sub>Not an official Minecraft product. Not approved by or associated with Mojang or Microsoft.</sub>
