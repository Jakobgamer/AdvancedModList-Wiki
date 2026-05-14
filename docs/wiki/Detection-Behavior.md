# Detection Behavior

AdvancedModList uses a client-side verification scan to compare a player's runtime behavior against the configured mod list.

When enough configured indicators match, the related mod is shown as detected.

## Result Types

AdvancedModList separates scan results into operational categories:

- Allowed or informational mods.
- Blocked mods.
- Warnings, such as incomplete or suspicious scan results.

## Transport Speed

Configured by:

```yaml
probe-transport-speed: "auto"
```

Values:

```text
auto
fastest
fast
```

`fastest` uses the highest-speed scan path and is best for older supported versions up to `1.21.4`.

`fast` uses a safer path and is recommended on `1.21.5+`.

`auto` chooses based on server version.

## Probe Speed

Configured by:

```yaml
probe-speed: 8
```

Higher values mean fewer request cycles.

Normally you should keep this at 8.

Lower values reduce scan pressure and improve stability on sensitive versions.

## Bedrock Players

Bedrock players use a different client stack and should not be scanned with the Java-only scan path.

If Bedrock detection is enabled, AdvancedModList skips them.

```yaml
bedrock:
  detect: true
```

## Bypass Detection

The bypass module is separate from normal mod detection.

It estimates whether a scan result looks incomplete or suspicious compared with the expected result shape.

Bypass risk is not the same as a blocked-mod detection.

## False Positives and False Negatives

Possible false positives:

- A configured indicator is too broad.
- Multiple mods expose similar indicators.
- A modpack includes files or behavior from another mod.

Possible false negatives:

- The mod changed its public indicators.
- The mod hides or changes client-side behavior.
- The client blocks or manipulates the scan.
- The selected `check-mode` does not include the mod.

## Best Practices

- Use specific mod identifiers.
- Avoid broad or generic indicators where possible.
- Use multi-entry definitions for mods that differ between Fabric, Forge, NeoForge, or mod versions.
- Keep `blocked-mods.yml` focused.
- Use `RELEVANT` or `BLOCKED` mode for faster operational scans.
