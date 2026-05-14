# Troubleshooting

## PlaceholderAPI says `0 placeholder hook(s) registered`

This message can be from PlaceholderAPI itself and does not necessarily mean AdvancedModList failed.

Check for this AdvancedModList log line:

```text
PlaceholderAPI expansion registered: %aml_*%
```

Test:

```text
/papi parse <player> %aml_clean%
```

If `%aml_clean%` is returned unchanged, the expansion is not registered.

## Player gets kicked during scanning

Symptoms may include:

```text
DecoderException
Packet decode error
Unexpected client response
```

Try:

```yaml
probe-transport-speed: "fast"
```

Or lower:

```yaml
probe-speed: 4
```

Then run:

```text
/aml reload
```

## Scan is slow on newer versions

Newer Minecraft versions may require safer scan settings.

Options:

- Use `check-mode: "BLOCKED"` to check fewer mods.
- Use `check-mode: "RELEVANT"` for a balanced list.
- Keep `check-delay-ticks: 0`.
- Increase `probe-speed` only if players are not kicked.

## Player shows no mods

Possible reasons:

- The player is vanilla.
- The configured identifiers do not match the installed mods.
- The mod exposes different indicators for Fabric/Forge/NeoForge.
- The player is Bedrock and scanning was skipped.
- The scan timed out.
- `check-mode` excludes the mod.

Check:

```text
/aml list <player>
```

Also inspect logs if debug mode is enabled.

## Unknown mod when using `/aml blocked add`

The mod must exist in `mods.yml`.

Add the mod to `mods.yml`, reload, then try again.

```text
/aml reload
```

## Multi-server data is empty

Check:

- `modules/multi-server.yml` has `enabled: true`.
- MySQL credentials are correct.
- Each server has a unique `server-name`.
- The database user can create and update tables.
- The server was restarted after enabling the module.

Use:

```text
/aml multiserver info
```

## Discord webhook does not send

Check:

- The webhook group is enabled.
- `webhook-url` is set.
- `send-events` includes the event type.
- Discord did not delete or rotate the webhook.
- `timeout-millis` is not too low.

## OP players are still scanned

This is intentional.

Operators do not bypass scans automatically.

Only players with:

```text
aml.bypass
```

are skipped.

## `/aml reload` does not apply everything

Most config changes reload with `/aml reload`.

Some module changes, especially database or multi-server startup behavior, may require a full server restart.
