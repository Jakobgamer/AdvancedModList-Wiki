# Commands

Main command:

```text
/aml
```

Aliases:

```text
/advancedmodlist
/ml
/modlist
```

## /aml help

Shows available commands.

Permission:

```text
aml.command.help
```

## /aml reload

Reloads config files, mod files, language files, and module configs.

Permission:

```text
aml.command.reload
```

## /aml probe <player>

Starts a manual probe for a player.

Permission:

```text
aml.command.probe
```

Example:

```text
/aml probe Waldran
```

## /aml list <player>

Shows the latest detected mods for a player.

Permission:

```text
aml.command.list
```

Example:

```text
/aml list Waldran
```

## /aml <player>

Shortcut for viewing a player's mod list.

Permission:

```text
aml.command.modlist
```

Example:

```text
/aml Waldran
```

## /aml gui

Opens the GUI.

Permission:

```text
aml.command.gui
```

## /aml gui <player>

Opens the GUI detail view for a player.

Permission:

```text
aml.command.gui
```

## /aml blocked list

Lists blocked mods.

Permission:

```text
aml.command.blocked.list
```

## /aml blocked add <mod>

Adds a configured mod to `blocked-mods.yml`.

Permission:

```text
aml.command.blocked.add
```

The mod name must match a configured mod from `mods.yml`.

## /aml blocked remove <mod>

Removes a mod from `blocked-mods.yml`.

Permission:

```text
aml.command.blocked.remove
```

## /aml multiserver info

Shows multi-server module information.

Permission:

```text
aml.command.multiserver.info
```

The parent permission also works:

```text
aml.command.multiserver
```

## /aml multiserver clear confirm

Deletes all global player data from the multi-server database.

Permission:

```text
aml.command.multiserver.clear
```

The parent permission also works:

```text
aml.command.multiserver
```

This command is destructive. Use it carefully.

