# M&M Loot Copilot: GitHub updates

The desktop application's **Check for updates** button reads [latest.json](latest.json) and downloads the verified [release.b64](release.b64) through HTTPS.

## Current release: v0.8

v0.8 is live on GitHub. It displays existing saved AI research automatically when an item is selected or when new loot arrives and no other item is selected. Reading cached research does not make an OpenAI API request. Manual research and optional auto-research can still generate charges for uncached items.

The v0.8 GitHub update package contains updated `app.py`, `updater.py` and `VERSION.txt`. It was built against the v0.6 and v0.7 application layout, so either version can upgrade directly through the button. Older versions may require manual installation of a newer base version first.

## Persistence and security

The updater checks the downloaded archive's SHA-256 against the manifest, rejects unapproved file paths, and backs up local program files before replacing them. The `data/` folder is excluded from update packages and retains character history, research cache, preferences, and the Windows DPAPI-protected OpenAI API key.

SHA-256 provides integrity matching against the manifest; it is not an independent code-signing signature. GitHub repository access security is important. Only install trusted releases.

## Release procedure

Publish an approved ZIP of changed, allowlisted application files (plus `VERSION.txt`) as UTF-8 base64 text at `release.b64`; confirm the decoded ZIP's SHA-256; then update `latest.json` with the release version, exact URL, and hash. Publish the payload before advancing the manifest. Test installation and preserved `data/` on Windows where possible.

This is an unofficial community tool. Use it according to Monsters & Memories rules, and never commit personal data or API keys.
