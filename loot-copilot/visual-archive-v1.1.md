# Visual Evidence Archive, v1.1 prototype

Status: local Windows package built and tested; **not yet published to the automatic update channel**.

The v1.1 archive is distributed as a ZIP in the ChatGPT conversation. It extends M&M Loot Copilot with a **Visual evidence archive** button in the Adventure Journal and a standalone `Start_Visual_Archive.bat` launcher.

## What it does

- Watches a user-selected OBS Studio recording folder for finalized MKV/MP4/other supported recordings.
- Waits at least 75 seconds after file modification before trying to extract images.
- Uses locally installed `ffmpeg.exe` and `ffprobe.exe` to extract a configurable maximum number of JPEG candidates per recording (60 by default).
- Writes a private manifest for each recording with frame offsets, approximate UTC timestamps, and review states, under `data/evidence_sessions/<recording-id>/`.
- Skips historical recordings on first setup, unless the user explicitly chooses **Import past recordings**.
- Does not send screenshots to OpenAI, GitHub, or any other server, and does not automatically interpret game imagery.
- Does not replace `data/`, so saved character history, API-key ciphertext, research cache and preferences are preserved.

## Setup

Install OBS Studio and FFmpeg. In OBS select your game capture source, verify the preview, and record in MKV for resilience. Start and stop the recording yourself. Launch the visual archive tool, select the OBS recording folder, enter paths to `ffmpeg.exe` and `ffprobe.exe` if needed, and enable automatic private screenshot extraction. Review the resulting images before publishing any.

## GitHub updater caveat

The previous version's updater has a strict file allowlist that does not include `capture_archive.py` or `Start_Visual_Archive.bat`. Therefore it would reject a full v1.1 package. Do **not** advance `loot-copilot/latest.json` until a compatible migration release is available. A one-time manual installation of the v1.1 ZIP is required for this prototype.

## Boundaries

This is recording and local offline image extraction, not continuous screen interpretation. No automated NPC, PvP, chat, party, or quest claims are produced from the screenshots. The existing 20-minute idle/verified-exit journal publication remains ledger-only. Confirm game developer permission before adding unattended AI parsing of gameplay images.
