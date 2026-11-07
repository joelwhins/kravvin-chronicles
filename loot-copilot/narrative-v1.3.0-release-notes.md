# M&M Loot Copilot v1.3.0: Narrative Profile

Build prepared on November 6, 2026. This release updates the *active* story-generation function in `capture_archive.py`.

Default storytelling settings:
- Epic classic tabletop/D&D fantasy.
- Rich atmosphere, imagery, pacing, and character voice.
- Third-person perspective.
- Fictional internal thoughts and optional clearly fictional dialogue. No invented direct quotes attributed to actual players or NPCs.
- Explicit evidence notes separating confirmed gameplay, uncertainty, and narrative embellishment.
- Never fabricate named participants, locations, combat/PvP outcomes, deaths, quests, spells, loot, or actual messages.

The patch contains `capture_archive.py`, `updater.py`, and `VERSION.txt`. It includes the JSON response-format instruction in the active Visual Review request, and keeps analysis and story-writing separate. All user data, encrypted API credentials, research cache, saved reports, and screenshot evidence live outside those three files and must not be overwritten.

The release ZIP has been built and Python syntax checked locally, but **is not yet activated in the GitHub `latest.json` update channel**. Do not tell users that clicking `Check for updates` will install v1.3.0 until its actual checksum-verified package has been uploaded to `loot-copilot/release.b64` and the manifest has been updated. The installed release remains v1.2.1.

Local package SHA-256: `84332eda7a30eb36f713866889067a5bbb45737dd5604664a5524e49167fc694`

After installing, restart all Copilot and Visual Review processes. Previously saved stories remain unchanged; clicking `Create private story (paid)` generates a new draft with the updated narrative profile from a saved evidence report, without reuploading screenshots.
