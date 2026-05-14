# Configuration

Main configuration file:

```text
plugins/AdvancedModList/config.yml
```

## language

```yaml
language: "en"
```

Selects the language file from:

```text
plugins/AdvancedModList/lang/<language>.yml
```

Bundled languages:

```text
en
de
es
fr
```

## check-mode

```yaml
check-mode: "ALL"
```

Controls which configured mods are checked.

Available modes:

```text
ALL
BLOCKED
RELEVANT
```

`ALL` checks every mod in `mods.yml`.

`BLOCKED` checks only mods listed in `blocked-mods.yml`.

`RELEVANT` checks all blocked mods plus mods listed in `relevant-mods.yml`.

Recommended values:

- Use `BLOCKED` for the fastest forbidden-mod checks.
- Use `RELEVANT` for a good balance.
- Use `ALL` for the most complete mod list.

## probe-speed

```yaml
probe-speed: 8
```

Controls how fast the scan is executed.

You should rarely change this.

Higher values are faster, but they also increase scan load. If players get kicked during scans on newer versions, lower this value.

## probe-transport-speed

```yaml
probe-transport-speed: "auto"
```

Controls the scan transport strategy without exposing internal implementation names.

Available values:

```text
auto
fastest
fast
```

`auto` uses the fastest path on versions up to `1.21.4` and a safer path on `1.21.5+`.

`fastest` forces the maximum-speed transport. This is best for versions up to `1.21.4`.

`fast` uses the slightly slower safer transport. This is recommended for `1.21.5+`.

Why this exists:

Newer Minecraft versions changed some client/server timing behavior. Very fast scanning can cause decode errors or unstable responses on newer versions. `auto` chooses a safer default.

## check-delay-ticks

```yaml
check-delay-ticks: 0
```

Delay between request cycles.

`0` means send the next check as soon as possible.

Usually this should stay at `0`. Increase it only if you see instability.

## timeout-ticks

```yaml
timeout-ticks: 200
```

How long a probe may run before it is considered timed out.

`200` ticks equals about 10 seconds.

## bedrock

```yaml
bedrock:
  detect: true
  warn-on-detect: false
```

`detect` skips Java-only scans for Bedrock players when Floodgate/Geyser detection is available.

`warn-on-detect` controls whether skipped Bedrock probes are reported as warnings.

