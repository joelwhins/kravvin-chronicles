# M&M Loot Copilot releases

## Current update: v1.1 Visual Evidence Archive

The GitHub manifest `latest.json` points to v1.1. The update package `release.b64` is a Base64-encoded ZIP verified by SHA-256.

This is a compatibility release for older v0.9 installations. It only replaces filenames permitted by the v0.9 updater; the new screenshot archive module is included in the updated journal component and extracted locally when the user opens **Visual evidence archive**. Future updates can use the expanded v1.1 updater allowlist directly.

Install from v0.9 using **Check for updates**. The updater backs up the existing application files and never replaces `data/`, which retains per-character history, cached research, preferences, and Windows-encrypted API credentials.

Visual Evidence Archive watches completed OBS recordings, extracts a bounded number of local screenshots using FFmpeg and FFprobe, and stores them privately. It does **not** perform continuous automated AI analysis, publish videos/screenshots, or make API calls for visual interpretation.

For setup, use OBS recording directory and executable paths configured on the local Windows machine. Character-specific journal publishing requires a separately saved GitHub token and is independent of the private visual screenshot archive.

The package's updater installation, checksum validation, preserved data, and embedded capture module were checked in a local simulation. The updated application still requires verification on the user's Windows PC.

Use this unofficial tool only in compliance with the game rules. Never store secrets in this GitHub repository.
