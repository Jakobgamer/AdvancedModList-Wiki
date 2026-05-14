# AdvancedModList Wiki

AdvancedModList is a Paper plugin that helps server owners detect configured client-side Minecraft mods. It is designed for servers that want to see which client mods players are using, warn staff about forbidden mods, and optionally react with Discord webhooks, commands, GUI views, multi-server storage, and PlaceholderAPI placeholders.

As a heads up this wiki is partially created by ai because I didn't have the time yet and thought this one is better than no one. 
## What AdvancedModList Does

- Detects configured client mods.
- Separates detected mods into allowed and blocked mods.
- Supports automatic scans when players join.
- Supports manual scans with `/aml probe <player>`.
- Can notify staff ingame.
- Can send Discord webhook embeds.
- Can run console commands after a scan.
- Can estimate bypass risk from suspicious scan results.
- Can store and display scan data in a GUI.
- Can sync data between servers using MySQL.
- Provides PlaceholderAPI placeholders with the `%aml_*%` identifier.

## Important Limitations

AdvancedModList is a detection and warning tool, not a perfect anticheat.

- A client can try to hide or spoof information.
- Some mods share similar public indicators.
- Indicators may differ between Fabric, Forge, NeoForge, and mod versions.
- Detection depends on the configured entries in `mods.yml`.
- Newer Minecraft versions may require slower scan settings for stability.

## Recommended Setup

For most servers:

```yaml
check-mode: "RELEVANT"
probe-speed: 8
probe-transport-speed: "auto"
```

Use `BLOCKED` if you only care about forbidden mods and want the smallest scan surface. Use `ALL` if you want the broadest possible mod list.

## Wiki Pages

- [Installation](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Installation)
- [Configuration](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Configuration)
- [Commands](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Commands)
- [Permissions](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Permissions)
- [Mod Configuration](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Mod-Configuration)
- [Modules](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Modules)
- [PlaceholderAPI](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/PlaceholderAPI)
- [Detection Behavior](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Detection-Behavior)
- [Troubleshooting](https://github.com/Jakobgamer/AdvancedModList-Wiki/wiki/Troubleshooting)
