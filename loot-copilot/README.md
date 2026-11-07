# M&M Loot Copilot: GitHub updates

The `Check for updates` button in the desktop application reads [latest.json](latest.json) and downloads [release.b64](release.b64) through HTTPS.

## Current release

The complete **v0.6** installer is provided in the ChatGPT conversation. It includes multi-character monitoring and the updater that can install verified incremental releases.

**v0.7** is published here as the first incremental update from **v0.6**. It updates the version and updater module, demonstrating the small verified-patch release mechanism.

To upgrade older installations (v0.5 and earlier), install v0.6 manually once by copying application files into the same folder while preserving `data/`. Then select **Check for updates** to install v0.7.

## Persistence and safety

The updater downloads only from this specific GitHub repository, checks the decoded ZIP's SHA-256 against the manifest, checks the target version, rejects unexpected files and backs up the files being replaced before installing. Only program files on its allowlist can be replaced. The `data/` folder is never included or replaced; this retains character history, research cache, preferences and Windows DPAPI-protected API key.

This uses checksum-based integrity checking, not a separate digital signature. Repository access and GitHub account security are critical. Downloaded updates run local code on the user's PC.

The package is an unofficial community tool and must be used in accordance with the game's rules. Never commit API credentials or user data.

## Future release workflow

Generate a ZIP containing changed allowlisted program files plus `VERSION.txt`, base64-encode it as `release.b64`, publish the base64 file, then update `latest.json` with `version`, `base_version`, `package_url` and the SHA-256 of the decoded ZIP. GitHub's release artifacts are accessible publicly; only publish trusted source code.
