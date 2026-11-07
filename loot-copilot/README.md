# M&M Loot Copilot releases

## Current version: v0.9

The [latest.json](latest.json) manifest now points to the verified [release.b64](release.b64) ZIP payload for v0.9. In v0.8, click **Check for updates** to install it. The update archive contains `app.py`, `storage.py`, `updater.py` and `VERSION.txt`. These are all on v0.8's allowed-file list.

New in v0.9:
- **Adventure & economy** window with per-character and per-day event summaries
- Loot and gathering event counts, item-name frequencies, and saved AI recommendations
- Copyable text reports; no new API requests to view the report
- No unsupported vendor prices, sales, gold/hour, item quantity or drop-location claims

The app observes only previously verified character ledger acquisition events (`act_13`, `act_27`). Event counts are not necessarily item quantities. Historical events not imported into `data/item_history.json` are not included.

The updater checks the downloaded ZIP's SHA-256 against the pinned manifest, restricts overwritten paths, backs up code files, and does not overwrite `data/`. Keep your Windows account and GitHub credentials protected. Hash verification detects mismatches but is not independent code signing. Don't put API credentials into GitHub files.

The app is an unofficial community tool. Confirm that this type of monitoring complies with Monsters & Memories rules.

## Publishing subsequent versions

1. Build, test and package an incremental ZIP using allowlisted app files, including `VERSION.txt`.
2. Base64-encode the ZIP and publish it at `release.b64`.
3. Verify GitHub readback against the local ZIP and SHA-256.
4. Update `latest.json` with the new version, release URL, and checksum **last**.
5. Validate updater installation on Windows where possible.
