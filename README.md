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

