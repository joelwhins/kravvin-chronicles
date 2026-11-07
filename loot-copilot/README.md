# M&M Loot Copilot, GitHub update channel

## Latest release: v1.6.0 (AI Illustrated Adventure Journals)

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

## v1.4.0, character continuity and private illustrated chapters

- Select the correct character (for example `kravvin/Dewdandy`) before generating a private story. If an old saved evidence report has a different or unverified character, the application asks permission to associate the recording with the selected character; attribution is user-provided, not visual proof.
- The third-person, epic classic D&D narrative generator uses the selected character name, keeps each character's session history separate, and may incorporate observations from up to five earlier evidence-backed sessions for that same character, without treating prose as historical proof.
- Fights and enemy presence must not be treated as confirmed kills unless the evidence explicitly confirms the outcome. The AI may still make mistakes, so review privately.
- Each newly generated story includes an offline `adventure_illustrated_private.html` with actual OBS screenshots, offsets, and evidence notes; click **Open illustrated chapter** in Visual Review. Screenshots are not uploaded for gallery creation.
- The gallery is private; no automatic GitHub posting and no generative art. Review screenshots for private chat and player details before publishing anything.
- v1.4.0 GitHub updater patch replaces only `capture_archive.py`, `updater.py`, and `VERSION.txt`; `data/` remains untouched. Simulated upgrade from v1.3.0 passed, including history, encrypted-key and evidence preservation. Live Windows validation remains outstanding.

## Current: v1.6.0 (AI Illustrated Adventure Journals)

The **Check for updates** button in v1.5.0 now installs v1.6.0 from the verified release manifest. This is a v1.5.0-to-v1.6.0 update. Earlier installations should install the intermediate release before applying this version.

In **AI visual review**, select a saved narrative and use **Generate AI artwork (paid)**. The image API creates one cover and two scene illustrations using **gpt-image-1-mini** at medium quality. This requires explicit consent and is charged by the OpenAI API. It transmits story excerpts, the attributed protagonist name, and summarized visual observations. **It does not upload the original OBS screenshots to the image-generation endpoint.**

Generated images are cached locally in the recording's `private_art` folder. Reopening the illustrated chapter, or repeating the request when all matching artwork is present, does not regenerate or recharge. Failed or interrupted runs can resume missing images; every successfully returned image is saved before the next call.

**Story vs evidence:** AI fantasy illustrations are clearly labeled as creative interpretations, not evidence. The private chapter presents generated art inline, while raw screenshots remain in a collapsed private evidence appendix. The user's original `data/` folder, encrypted API key, screenshots, and saved stories remain untouched by the update.

Before any external sharing: open and review the private illustrated chapter, select **Approve reviewed artwork**, then **Export public-ready chapter ZIP**. The exported static ZIP contains the story and approved AI artwork only; it excludes the raw screenshots, analysis JSON, private evidence manifest, and API credentials. The ZIP stays local. This update **does not automatically publish to GitHub or any public website**.

**Test saved API key (free)** queries the OpenAI models endpoint without requesting paid model generation. The image-generation path has local mocked-response tests and the updater migration test passes; a live paid image generation has not yet been performed on the user's Windows installation.
