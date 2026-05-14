# Modules

AdvancedModList modules are configured in:

```text
plugins/AdvancedModList/modules/
```

## Start Scan Module

File:

```text
modules/start-scan.yml
```

Controls automatic scans when a player joins.

```yaml
enabled: true
probe-delay-ticks: 20
```

`probe-delay-ticks` waits after join before starting the scan.

Recommended:

- `20` for stable join scans.
- `5` to `10` if you want faster scans after join.
- `0` only if you have tested it carefully.

Cooldown:

```yaml
cooldown:
  enabled: false
  duration-seconds: 300
```

When enabled, players are not rescanned on every join until the cooldown expires.

## Discord Module

File:

```text
modules/discord.yml
```

Supports multiple webhook targets.

Example:

```yaml
webhooks:
  primary:
    enabled: true
    webhook-url: "https://discord.com/api/webhooks/..."
    send-events: [allowed, illegal, warn]
```

Event groups:

```text
allowed
illegal
warn
```

`allowed` means clean or allowed results.

`illegal` means blocked mods were detected.

`warn` means scan warnings or bypass warnings.

Useful settings:

```yaml
include-allowed-mods: true
include-server-name: false
include-player-uuid: false
use-player-head-thumbnail: true
```

## Auto Command Module

File:

```text
modules/auto-command.yml
```

Runs console commands after a scan finishes.

Modes include:

```text
any-blocked
mods
except-mods
bypass-risk
```

Example:

```yaml
groups:
  hack-kick:
    enabled: true
    mode: mods
    mods: [Meteor, Wurst, LiquidBounce]
    commands:
      - "kick {player} Blocked mods detected: {matchedMods}"
```

Common placeholders:

```text
{player}
{uuid}
{brand}
{blockedMods}
{allowedMods}
{allMods}
{matchedMods}
{primaryBlockedMod}
{verification}
{verificationStatus}
{bypassRiskPercent}
{bypassWarningActive}
{bypassReason}
```

Velocity proxy commands can be forwarded with an external forwarding plugin, as described in the example comments inside the config.

## Bypass Detection Module

File:

```text
modules/bypass-detection.yml
```

Estimates whether a player may be hiding or manipulating scan information.

The module compares scan signals and reports suspicious result patterns.

Important values:

```yaml
enabled: true
min-mods-for-evaluation: 3
warn-threshold-percent: 50.0
warn-cooldown-hours: 48
```

If the risk reaches the threshold, the result can be reported as a warning.

## GUI Module

File:

```text
modules/gui.yml
```

Controls `/aml gui`.

Useful settings:

```yaml
enabled: true
default-sort-mode: THREAT_LEVEL
default-filter-mode: ALL
mods-page-size: 45
```

Sort modes:

```text
THREAT_LEVEL
UPDATED
NAME
BLOCKED_COUNT
BYPASS_RISK
```

Filter modes:

```text
ALL
FORBIDDEN_ONLY
WARNING_ONLY
FORBIDDEN_OR_WARNING
```

## Multi-Server Module

File:

```text
modules/multi-server.yml
```

Synchronizes player scan data across multiple servers using MySQL.

Main settings:

```yaml
enabled: false
server-name: "server1"
mysql:
  host: "localhost"
  port: 3306
  database: "advancedmodlist"
  username: "root"
  password: ""
```

Each server in the network must have a unique `server-name`.

Multi-server data is shown in GUI and can be inspected with:

```text
/aml multiserver info
```

Global data can be cleared with:

```text
/aml multiserver clear confirm
```
