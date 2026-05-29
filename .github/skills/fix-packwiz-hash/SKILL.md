---
name: fix-packwiz-hash
description: "Fixes invalid mod file hash errors in packwiz by removing and re-adding the specified mods. Use when you encounter 'java.lang.Exception: Invalid mod file hash' during packwiz operations."
params:
  mods:
    type: string
    description: "A raw, comma-separated or newline-separated list of mod slugs (filenames without .pw.toml) that need their hashes regenerated. I will parse this string into individual mod slugs."
    required: true
---

## Fix Packwiz Hash

To resolve "Invalid mod file hash" errors for `packwiz`, the specified mods need to be removed and re-added to regenerate their hashes.

### Steps:
For each mod slug provided in the `mods` parameter (parsed from a comma or newline separated list):
1. Run `packwiz rm <mod_slug>`
2. Run `packwiz cf add <mod_slug>` (or `packwiz modrinth add <mod_slug>` if it's a Modrinth mod)

