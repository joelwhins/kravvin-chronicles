# M&M Loot Copilot, GitHub update channel

## Latest release: v1.2 (Visual Evidence Review)

The **Check for updates** button on v1.1 downloads the verified, v1.1-updater-compatible package described in [latest.json](latest.json) from [release.b64](release.b64). Version 1.2 adds opt-in private AI screenshot review for evidence previously extracted locally from OBS recordings.

After updating, open **Adventure Journal > Visual evidence archive > AI visual review (paid)**. Choose an archived recording and the associated character (if known). Select 4, 6, 8 or 12 frames, then explicitly consent to a paid OpenAI request containing those screenshots. The analysis UI is bundled within capture_archive.py so the v1.1 updater can install it without a manual bootstrap. The response is saved as `data/evidence_sessions/<id>/visual_analysis.json` and `adventure_evidence_draft.md`. The optional **Create private story (paid)** button uses saved observations for a short draft. Opening cached analysis requires no further API calls.

**Privacy and accuracy:** Screenshots can include private messages, usernames and sensitive text. Inspect before transmitting. The analysis is based on sparse frames and approximate file timestamps; it cannot reconstruct all unseen gameplay. PvP outcomes, quest completions, player identities and dialogue require clear visual evidence and confirmation. Neither screenshot analysis nor the generated private draft is automatically sent to GitHub or included in public session posts.

The existing automatic publisher, when separately configured, continues to publish **ledger-only** narratives after its session-completion safeguards. The user must not mistake it for validated visual storytelling.

## Updating

- From v1.1, click **Check for updates** to install v1.2. The updater verifies the downloaded ZIP against the SHA-256 in the manifest and backs up program files.
- The `data/` folder is excluded from the patch. It preserves the Windows-encrypted API key, GitHub token, history, saved answers, evidence and preferences.
- The v1.2 package is an incremental update based on the v1.1 app. Older installs may require upgrading to v1.1 first.
- A complete v1.2 offline ZIP is also available in the associated ChatGPT conversation.

## Release procedure

Publish a base64-encoded ZIP at `release.b64` before updating `latest.json`. Include `VERSION.txt` and changed allowlisted application files. Verify the SHA-256 of the decoded ZIP. Test upgrade against the previous release and preservation of `data/` on Windows.

This is an unofficial community application. The user should confirm game developer approval before using automated AI analysis of gameplay recordings. No game memory reading, input automation or in-game modifications are implemented.

## v1.2.1 hotfix

Fixes OpenAI HTTP 400 for JSON-mode visual evidence analysis. The Responses API JSON object mode requires the word `json` in the request content; the updated `visual_analysis.py` includes it in lowercase in the request instructions and user message. The release contains only `visual_analysis.py` and `VERSION.txt`; no `data/` files are included. Use **Check for updates** from v1.2, restart, and retry **Analyze selected screenshots**. Local tests mock the OpenAI API; live Windows/API validation remains outstanding.

## v1.2.1 updater compatibility correction

The initial v1.2.1 release was rejected by the v1.2 updater because `visual_analysis.py` was missing from the old updater's allowed-file list. The corrected update package replaces only the allowlisted `updater.py` and `VERSION.txt`, adds `visual_analysis.py` to the updater allowlist for future releases, and performs a narrowly scoped, one-time JSON-mode prompt repair on the existing `visual_analysis.py` at the next app launch. The repair checks the exact old prompt before changing it, makes a backup of that source file in `data/updater_backups/pre_1_2_1/`, and does not change user data. If no matching file is installed, the repair makes no change. The corrected ZIP's SHA-256 is `cd5546dae18905f983efabd8b9f6b56fb095e681cfc4ccac57d571fa3475db2b`.
