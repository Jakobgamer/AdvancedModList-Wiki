# Installation

## Requirements

- Paper or a Paper-compatible server.
- Minecraft server API version `1.20+`.
- Java 17 or newer.
- Optional: PlaceholderAPI for `%aml_*%` placeholders.
- Optional: MySQL if the multi-server module is enabled.

## Basic Installation

1. Put the AdvancedModList jar into the server `plugins` folder.
2. Start the server once.
3. Stop the server.
4. Edit the generated files in `plugins/AdvancedModList/`.
5. Start the server again.

## Generated Files

Main files:

```text
plugins/AdvancedModList/config.yml
plugins/AdvancedModList/mods.yml
plugins/AdvancedModList/blocked-mods.yml
plugins/AdvancedModList/relevant-mods.yml
```

Module files:

```text
plugins/AdvancedModList/modules/start-scan.yml
plugins/AdvancedModList/modules/discord.yml
plugins/AdvancedModList/modules/auto-command.yml
plugins/AdvancedModList/modules/bypass-detection.yml
plugins/AdvancedModList/modules/gui.yml
plugins/AdvancedModList/modules/multi-server.yml
```

Language files:

```text
plugins/AdvancedModList/lang/en.yml
plugins/AdvancedModList/lang/de.yml
plugins/AdvancedModList/lang/es.yml
plugins/AdvancedModList/lang/fr.yml
```

## Updating

1. Stop the server.
2. Replace the jar.
3. Start the server.
4. Check the console for warnings.
5. Run `/aml reload` after manual config changes.

Do not delete existing config files unless you want the plugin to regenerate defaults.

## PlaceholderAPI

PlaceholderAPI is optional. If installed, AdvancedModList registers an internal expansion automatically.

You do not need to run:

```text
/papi ecloud download ...
```

The expansion is bundled inside AdvancedModList.

## Quick Test

After installing, join the server and run:

```text
/aml probe <player>
/aml list <player>
```

If PlaceholderAPI is installed:

```text
/papi parse <player> %aml_clean%
```

