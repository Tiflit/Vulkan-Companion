DRAFT:

This is to serve as the main software, a unified UI to enable Vulkan sub-tools management and compatibility between games and hardware.

1. Vulkan-Companion - manage and optimize Vulkan games directly from this software UI with portability and privacy being mandatory (users can choose to participate in the online compatibility database if they so desire);
2. DXVK-Companion - serves as the main component to enable Vulkan features and compatibility on (almost) any game;
3. Neural-Companion - (WIP) component allowing to enable and manage AI features from any Vulkan-compatible game, used to extract/translate/estimate the necessary data for enhancing techniques such as DLSS/FSR/XeSS - complement to Optiscaler when Optiscaler's features are not available natively;
4. Optiscaler-Companion - (not yet implemented) would serve to manage Optiscaler integration for games using DLSS/FSR/XeSS natively;
5. BFI-Companion - (not yet implemented) would serve to enable and manage BFI Presenter's integration into Vulkan games for high refresh rate displays;
6. Others - Maybe

A compatibility database is planned to ease management with recognized games, versions and hardware capabilities.
It will keep track of a games' available native features and applicable enhancements. Workarounds will be documented too if necessary.

The objective of this project is to centralize and facilitate the use of image and performance enhancing techniques, with Vulkan seen as the universal framework.
Separate tools are implemented as independent plugins downloaded separately and never bundled together.
Management can be manually tuned per-game, or automatically applied for every compatible game based on hardware capabilities.
This is designed to be highly automated to also enable features for controller-first gaming systems.
The software should be able to automatically recognize the available features based on the game name, version and available hardware - an application restart might be prompted if no documented compatibility is available from the database.

Future ideas:
Optional frame limiting
Automatic enablement of LSFG if available - for compatibility reasons
Respect of other tools' settings, like Optiscaler-Client or DLSS-Enabler, if also present on the system (might be mutually exclusive, this will require more work)




Suggested by Claude:

"# Vulkan-Companion

A proposed umbrella project for managing Vulkan-based graphics and performance tools for games from one place, with portability, privacy and safety as requirements.

**Status: concept / planning draft. No code, installer, UI, or compatibility database exists yet.** This repository is intentionally waiting on its first component, [DXVK-Companion](https://github.com/Tiflit/DXVK-Companion), which is the project under active development. Everything below describes intent, not current functionality, and there are no release dates.

## Why this exists

Vulkan is a common foundation for modern graphics tooling: DXVK translates older Direct3D games to it, and several upscaling, frame-pacing and enhancement tools build on or alongside it. Using them today usually means manual file placement, per-game trial and error, and little shared knowledge of what works on which hardware.

Vulkan-Companion aims to eventually provide a single, mostly automated interface that:

- recognises a game and the hardware it runs on,
- applies the appropriate tools with sensible defaults,
- lets the user override anything per game,
- and can restore the original game state at any time.

## Components

Each tool is an independent project. Components are downloaded separately, are never bundled together, and must not require each other. Vulkan-Companion will only coordinate them.

| Component | Purpose | Status |
|---|---|---|
| [DXVK-Companion](https://github.com/Tiflit/DXVK-Companion) | Detects older Direct3D 9/10/11 games and manages DXVK deployment, updates, rollback and per-game configuration | In development. This is the primary project |
| [Neural-Companion](https://github.com/Tiflit/Neural-Companion) | Vulkan layer for neural visual enhancement, using providers' unmodified models and runtimes | Planning draft; only a pass-through layer experiment exists |
| Optiscaler-Companion | Would manage OptiScaler integration for games with native DLSS/FSR/XeSS | Idea only |
| BFI-Companion | Would manage black frame insertion for high-refresh-rate displays | Idea only |

Ideas marked "Idea only" may never be built. DXVK-Companion comes first, and nothing else should delay it.

## Planned: compatibility database

An opt-in, community-maintained record of which tools work with which game versions and hardware, including known workarounds. It would let the app recommend or apply settings automatically for recognised games.

Open design questions, to be settled before any server exists:

- Game identification: executable hash and store IDs are preferred over game names.
- Record format: a versioned, human-readable schema, starting as plain files in a repository.
- What each record contains: tool and version, GPU model, driver version, outcome, and notes.
- Moderation and validation of submitted data.

Hardware and driver versions are the only environment details a record needs. No account, user identifier, or personal data should ever be required.

## Principles

- **Privacy first.** Fully usable offline. Any online feature, including the database, is opt-in and documented. Nothing personal is collected or stored in this repository.
- **Portable.** Prefer self-contained, portable tools that do not write outside their own folder, unless a feature clearly requires otherwise.
- **Safe and reversible.** Every change to a game's files must be backed up and restorable. Changes are never injected into a running game.
- **Independent plugins.** Tools are separate downloads with their own licences, and the umbrella must never make one a hard requirement of another.
- **Honest compatibility.** Report what is verified, what is estimated, and what is unknown. Unsupported paths should fall back to the original, untouched game.
- **Respect for prior work.** Review a third party's licence before using it, preserve required notices, and credit influences. Credit is never a substitute for permission.

## Anti-cheat warning

Tools in this family may replace or add graphics-related files in a game's folder or hook into its rendering. This is not safe for online multiplayer games with anti-cheat systems and can result in bans. Any future automatic mode must detect known anti-cheat titles and avoid applying changes by default. Use these tools only with single-player or offline games unless you are certain they are permitted.

## Non-goals

- Bypassing DRM, licensing, or anti-cheat systems
- Bundling or redistributing proprietary models, runtimes or game files
- Training, reverse engineering, or modifying third-party models or runtimes
- Requiring an account, an installer, or an internet connection for core features
- Promising performance or compatibility results

## Roadmap

1. **Now:** finish DXVK-Companion to a stable, documented release.
2. **After that:** define the compatibility record schema and trial it using DXVK-Companion's own per-game results.
3. **Only then:** decide whether a shared shell is needed, and what plugin interface it requires, based on a second real component.

The order may change, and later steps are contingent on earlier ones.

## Credits and independence

This project builds on or works alongside the work of others, including [DXVK](https://github.com/doitsujin/dxvk) and [OptiScaler](https://github.com/optiscaler/OptiScaler). It is independent and not affiliated with or endorsed by their authors, NVIDIA, AMD, Intel, or Microsoft. All trademarks belong to their owners. Third-party software, models and runtimes keep their own licences.

## Contributing

Not open for code contributions yet. Feedback on the concept, the compatibility record format, and the safety model is welcome through issues.

## License

Apache-2.0. See [LICENSE](LICENSE)."
