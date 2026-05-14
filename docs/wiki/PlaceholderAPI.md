# PlaceholderAPI

AdvancedModList provides an internal PlaceholderAPI expansion.

Identifier:

```text
aml
```

You do not need to download an eCloud expansion.

The expansion is registered automatically when PlaceholderAPI is installed.

Expected startup log:

```text
[AdvancedModList] PlaceholderAPI expansion registered: %aml_*%
```

## Placeholders

```text
%aml_clean% / %aml_is_clean% - Scan result
%aml_mod_count% / %aml_mods_count% - Detected mod count
%aml_blocked_count% - Blocked mod count
%aml_allowed_count% - Allowed mod count
%aml_mods% - Detected mod list
%aml_blocked_mods% - Blocked mod list
%aml_allowed_mods% - Allowed mod list
%aml_brand% - Client brand
%aml_probe_status% / %aml_status% - Last probe status
%aml_bypass_risk% / %aml_risk% - Bypass risk percent
```

## clean Values

`%aml_clean%` can return:

```text
yes
no
checking
unknown
```

`yes` means the scan finished successfully, no blocked mods were detected, and no bypass warning is active.

`no` means blocked mods or an active bypass warning were detected.

`checking` means the probe is currently running.

`unknown` means there is no clear successful result yet.

## Probe Status Values

`%aml_probe_status%` can return values such as:

```text
SUCCESS
IN_PROGRESS
TIMEOUT
CANARY_FAILED
PACKET_SEND_FAILED
INTERNAL_ERROR
BEDROCK_CLIENT
PLAYER_LEFT_BEFORE_START
UNKNOWN
```

## Testing Placeholders

Use:

```text
/papi parse <player> %aml_clean%
/papi parse <player> %aml_mod_count%
/papi parse <player> %aml_blocked_mods%
```

If the placeholder is returned unchanged, PlaceholderAPI did not register the expansion.

Check:

- PlaceholderAPI is installed.
- AdvancedModList started after PlaceholderAPI.
- `softdepend: [PlaceholderAPI]` is present in `plugin.yml`.
- The server log contains the AML registration message.

## Behavior

Placeholders do not start scans.

They only read the latest known scan result or currently running probe state.

