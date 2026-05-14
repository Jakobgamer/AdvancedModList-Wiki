# Permissions

## Admin Permission

```text
aml.admin
```

Default:

```text
op
```

Gives access to all administrative commands and notifications.

Important:

`aml.admin` does not include `aml.bypass`. Operators are not automatically skipped by the scan.

## Command Permissions

```text
aml.command.help
```

Allows `/aml help`.

```text
aml.command.reload
```

Allows `/aml reload`.

```text
aml.command.probe
```

Allows `/aml probe <player>`.

```text
aml.command.list
```

Allows `/aml list <player>`.

```text
aml.command.modlist
```

Allows `/aml <player>` shortcut.

```text
aml.command.gui
```

Allows `/aml gui` and `/aml gui <player>`.

## Blocked Mod Management

```text
aml.command.blocked
```

Parent permission for blocked-mod subcommands.

```text
aml.command.blocked.list
```

Allows `/aml blocked list`.

```text
aml.command.blocked.add
```

Allows `/aml blocked add <mod>`.

```text
aml.command.blocked.remove
```

Allows `/aml blocked remove <mod>`.

## Multi-Server Permissions

```text
aml.command.multiserver
```

Parent permission for multi-server commands.

```text
aml.command.multiserver.info
```

Allows `/aml multiserver info`.

```text
aml.command.multiserver.clear
```

Allows `/aml multiserver clear confirm`.

## Notification Permissions

```text
aml.notify
```

Parent permission for probe notifications.

```text
aml.notify.blocked
```

Receive full notifications when blocked mods are detected.

```text
aml.notify.allowed
```

Receive notifications for clean or allowed probe results.

## Bypass Permission

```text
aml.bypass
```

Players with this permission are not probed.

Default:

```text
false
```

Operators do not get this permission automatically unless your permission plugin grants it.

