# Vulkan-Companion

A planned, unified interface for managing Vulkan-based graphics and performance tools for games, built around portability, privacy and safety.

**Status: concept / planning. No code, installer, UI or compatibility database exists yet.** Vulkan-Companion is intended to become the main application users download, but it will be built on top of working modules, not ahead of them. The first module, [DXVK-Companion](https://github.com/Tiflit/DXVK-Companion), is under active development. Everything below describes intent, not current functionality, and there are no release dates.

## What it aims to do

Vulkan is a common foundation for modern graphics tooling. DXVK translates older Direct3D games to it, and several upscaling, frame-pacing and presentation tools build on or alongside it. Using them today usually means manual file placement, per-game trial and error, conflicting layers and little shared knowledge of what works on which hardware.

Vulkan-Companion aims to provide one mostly automated interface that:

- recognises a game and the hardware and display it runs on,
- applies the appropriate tools with sensible defaults,
- lets the user tune or override anything per game, or apply settings automatically to every compatible game,
- preserves existing settings and detects conflicts between tools and layers already installed,
- tracks which files each tool installed, so every change can be restored,
- and works well on controller-first gaming systems.

## Intended usage modes

| Mode | Behaviour |
|---|---|
| Manage manually | Open the hub, configure a game, close the hub, launch the game normally |
| Launch through the hub | The hub checks compatibility, prepares integrations, then launches the game |
| Optional automatic management | A module watches for game launches when the user enables that feature |

The hub itself should not require continuous background operation. Individual modules may offer optional monitoring when automatic integration needs it. (DXVK-Companion, for example, is currently a tray application that can watch for game launches.) Installed rendering layers run inside the game regardless of whether the management interface is open.

## Modules

Each tool is an independent project. Modules are downloaded separately and are not bundled together. Each should remain usable on its own wherever practical. The hub coordinates supported combinations, and an integration may declare prerequisites (for example, a module that builds on DXVK).

| Module | Purpose | Status |
|---|---|---|
| [DXVK-Companion](https://github.com/Tiflit/DXVK-Companion) | Enables DXVK features locally: detects older Direct3D games and manages DXVK deployment, updates, rollback and per-game configuration | In development; the first and primary module |
| [Neural-Companion](https://github.com/Tiflit/Neural-Companion) | Enables AI features locally, as far as is realistically possible, using providers' unmodified models and runtimes; complements OptiScaler where its features are not available natively | Planning; only an early experiment exists |
| Optiscaler-Companion | Would download and manage OptiScaler for games with native DLSS/FSR/XeSS | Idea; may prove too complex |
| BFI-Companion | Would coordinate software black frame insertion and presentation timing through [BFI Presenter](https://github.com/artzox/BFI-Presenter). The first step would be evaluating detection and coexistence with its own manager and settings, and building extra management only where the hub needs it | Idea; may never be built |

Modules marked "Idea" may never be finished. Finishing DXVK-Companion comes first, and nothing else should delay it.

## Planned: compatibility database

An opt-in, community-maintained record of which tools work with which games, versions and hardware, including known native features, applicable enhancements and documented workarounds. It would let the app recognise a game and recommend or apply settings automatically. Where no documented compatibility exists, the app should leave the game untouched or ask the user.

Design questions to settle before any server exists:

- **Game identification:** executable hash and store IDs are preferred over game names.
- **Record format:** a versioned, human-readable schema, starting as plain files in a repository.
- **Record contents:** likely to include the operating system and build, graphics API (native or translated), executable architecture, game build, tool and layer versions (including other installed layers), GPU and driver version, display mode, refresh rate and VRR state, plus the outcome and notes.
- **Moderation and validation** of submitted data.

None of this requires an account, a user identifier or other personal data. Database content is expected to be licensed separately from the code.

## Principles

- **Privacy first.** Fully usable offline. Participation in the online database, and any other online feature, is opt-in and documented. Nothing personal is collected or stored in this repository.
- **Portable.** Prefer self-contained, portable tools that do not write outside their own folder unless a feature clearly requires it.
- **Safe and reversible.** Every change to a game's files is backed up and restorable, and each tool's installed files have a clear owner. Changes are never injected into a running game.
- **Independent modules.** Modules are separate downloads with their own licences. Each stays independently usable where practical, and any dependency between modules is explicit and documented.
- **Honest compatibility.** Report what is verified, what is estimated and what is unknown. Unsupported paths fall back to the original, untouched game.
- **Respect for prior work.** Review a third party's licence before using it, preserve required notices and credit influences. Credit is never a substitute for permission.

## Anti-cheat warning

Tools in this family may replace or add graphics-related files in a game's folder or hook into its rendering. This is not safe for online multiplayer games with anti-cheat systems and can result in bans. Any future automatic mode must detect known anti-cheat titles and avoid applying changes to them by default. Use these tools only with single-player or offline games unless you are certain they are permitted.

## Non-goals

- Bypassing DRM, licensing or anti-cheat systems
- Bundling or redistributing proprietary models, runtimes, paid tools or game files
- Training, reverse engineering or modifying third-party models or runtimes
- Requiring an account or an internet connection for core features
- Promising performance or compatibility results

## Ideas for later

- Optional frame limiting
- Automatic enablement of third-party frame generation, such as Lossless Scaling's LSFG, if the user already has it. It is a paid third-party tool, so it would be enabled, never bundled or redistributed
- Respecting the settings of other tools, such as OptiScaler or DLSS-Enabler, when they are already present on the system. They may be mutually exclusive, so this needs more work

## Roadmap

1. **Now:** finish DXVK-Companion to a stable, documented release.
2. **Next:** define the compatibility record schema and trial it with DXVK-Companion's own per-game results.
3. **Then:** define the smallest useful module interface from DXVK-Companion's real needs: detection, compatibility decisions, installation ownership, configuration, rollback and status reporting.
4. **Finally:** build the shared interface on top of it.

The order may change, and later steps depend on earlier ones.

## Official downloads

Official releases of Vulkan-Companion and its modules are available free of charge from their GitHub repositories, which are the recommended source: https://github.com/Tiflit/Vulkan-Companion

Redistribution is governed by each project's licence. Anyone sharing or reviewing these tools is asked to credit the project and link the original repository so users can find the official, unmodified releases.

## Credits and independence

This project builds on or works alongside the work of others, including [DXVK](https://github.com/doitsujin/dxvk), [OptiScaler](https://github.com/optiscaler/OptiScaler) and [BFI Presenter](https://github.com/artzox/BFI-Presenter). It is independent and not affiliated with or endorsed by their authors, NVIDIA, AMD, Intel or Microsoft. All trademarks belong to their owners.

Third-party software, models and runtimes keep their own licences. OptiScaler and BFI Presenter are released under GPL-3.0. The intended design is to manage them as separate, unmodified upstream downloads without copying their code, but each integration will be assessed individually for compatibility and obligations before it is built. Check each project's repository for its current terms.

## Contributing

Not open for code contributions yet. Feedback on the concept, the compatibility record format and the safety model is welcome through issues.

## License

Apache-2.0. See [LICENSE](LICENSE). Individual modules are licensed in their own repositories.
