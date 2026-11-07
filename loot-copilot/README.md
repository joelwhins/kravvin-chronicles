# Jordain Loot Copilot updates

The desktop application checks `latest.json` when the user clicks **Check for updates**.

New releases require uploading a UTF-8 base64 encoding of a zip archive as `release.b64`, containing exactly these files: `app.py`, `ledger_core.py`, `ai_research.py`, `storage.py`, `auto_policy.py`, `updater.py`, `Start_Loot_Copilot.bat`, `README.txt`, and `VERSION.txt`.

For each release, compute the SHA-256 of the **decoded zip file**, update the manifest's `sha256`, `version`, and `package_url`, and commit package before manifest.

Application files are overwritten only after SHA-256 verification. The local `data/` directory is never included in the package, and is preserved with the user's history, cache, settings, and Windows-encrypted API key.

Version 0.4 introduces the update button. The v0.4 installer ZIP is distributed in the ChatGPT conversation. The remote release payload is not published yet; the manifest records the currently installed version only, so no remote installation is currently offered.

The copilot is an unofficial community tool. Do not publish user data or API credentials.
