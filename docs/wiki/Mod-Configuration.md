# Mod Configuration

Mod detection is configured in:

```text
plugins/AdvancedModList/mods.yml
```

Blocked mods are configured in:

```text
plugins/AdvancedModList/blocked-mods.yml
```

Relevant mods are configured in:

```text
plugins/AdvancedModList/relevant-mods.yml
```

## mods.yml

`mods.yml` maps display names to detection identifiers.

Single-entry format:

```yaml
mods:
  ExampleMod: "example.identifier"
```

Multi-entry format:

```yaml
mods:
  ExampleMod:
    - "example.identifier.primary"
    - "example.identifier.secondary"
```

Both formats can be mixed.

## Why Multiple Entries Exist

Some mods expose different indicators depending on:

- Fabric vs Forge vs NeoForge.
- Minecraft version.
- Mod version.
- Config library.

Using multiple entries lets one mod be represented once while still checking several possible identifiers.

## Duplicate Results

If multiple identifiers for the same mod match, the mod is only added once to the detected mod list.

Example:

```yaml
ExampleMod:
  - "example.identifier.primary"
  - "example.identifier.secondary"
```

If both identifiers match, the result is still only:

```text
ExampleMod
```

## blocked-mods.yml

`blocked-mods.yml` lists mods that should be treated as forbidden.

Example:

```yaml
blocked-mods:
  - meteor-client
  - xray
  - Freecam
```

Names are matched case-insensitively against configured mod names.

Detected blocked mods affect:

- Ingame notifications.
- Discord webhook category.
- Auto-command groups.
- PlaceholderAPI `%aml_clean%`.
- GUI threat display.

## relevant-mods.yml

`relevant-mods.yml` is used when:

```yaml
check-mode: "RELEVANT"
```

Blocked mods are automatically included in `RELEVANT` mode. You do not need to duplicate blocked mods in `relevant-mods.yml`.

## Choosing a Check Mode

`ALL`:

- Most complete output.
- Slowest scan.
- Best for audit/admin use.

`BLOCKED`:

- Fastest scan.
- Best if you only care about forbidden mods.

`RELEVANT`:

- Balanced mode.
- Checks blocked mods plus useful/common mods.

## Adding a New Mod

1. Add a stable identifier for the mod.
2. Add it to `mods.yml`.
3. If it is forbidden, add the mod name to `blocked-mods.yml`.
4. Run:

```text
/aml reload
```

5. Test with:

```text
/aml probe <player>
/aml list <player>
```

## Good Identifiers

Good identifiers are:

- Specific to one mod.
- Stable across releases.
- Not shared by unrelated mods.
- Tested on the loader and Minecraft versions you support.

Avoid generic identifiers that many mods share unless you intentionally want broad detection.

## YAML Notes

Do not define the same mod name twice in YAML. YAML parsers usually keep only the last value.

Use the multi-entry list format instead:

```yaml
SomeMod:
  - "first.identifier"
  - "second.identifier"
```
