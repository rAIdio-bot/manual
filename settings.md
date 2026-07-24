## Simple

### Provenance and C2PA

Every file you create in rAIdio.bot can carry a signed record that proves you made it, when you made it, and what tools were used. This is your proof of authorship.

The Provenance page in Settings lets you turn this on or off. We recommend keeping it on. The signed records are small files saved alongside your audio. Keep them: they are the closest thing available right now to proof that your music is yours.

### Neural watermark

Alongside the signed record, every track you generate carries an inaudible watermark woven into the audio itself. You can't hear it, but a detector can read it back — even after the file is converted to MP3, shared, or re-uploaded somewhere that strips the signed record. It's a second, sturdier way to show a track came from rAIdio.bot.

Right-click any file and choose **Properties** to see both: the **Content Credentials** (the signed record) and the **Neural Watermark** (Detected or not). A track you generated shows both; a file you imported shows neither, because we never mark audio that isn't AI-generated.

### Creator Identity

Your name, email, website, and organization are embedded in every file you create. This is how the signed record knows who made the music. You can fill in as much or as little as you want.

Your display name defaults to your computer username. Change it to whatever you want to be credited as.

### Backend

The local AI engine that runs all your music, voice, and analysis work on your GPU. The status indicator in the bottom-left corner shows whether it's running.

If a long mixed-mode session ever stops working — usually after 30+ generations of mixed Music / Voice / Stem work — click **Force Restart Backend** in Settings → AI Models, or click **Restart Backend** when it appears next to the status dot. The restart takes about 30 seconds and doesn't lose any saved work.

### Licenses

The Licenses page lists every piece of open-source software that rAIdio.bot uses, along with each one's license type. This is here for transparency: you can see exactly what powers the app.

### DLC

The rAIdio.bot XL Model is included free with rAIdio.bot. If your GPU has 24 GB or more of VRAM, install it from **Settings → AI Models** to unlock the "XL High Quality" option in the Music tab. The SFT Studio Model is also included free — install it the same way to unlock the "SFT Studio" option: the original ACE-Step 3.5B model run through its adaptive-guidance pipeline for higher-fidelity, wider-stereo music, running on roughly 8 GB of VRAM or more. Any future add-ons will appear here.

### Global Keyboard Shortcuts

These work everywhere — any tab, while focus is not in a text field.

**Navigation**

| Shortcut | Action |
|----------|--------|
| Ctrl+1 | Music tab |
| Ctrl+2 | Voice tab |
| Ctrl+3 | Edit tab |
| Ctrl+4 | Mix tab |
| Ctrl+5 | Play tab |
| F1 | Help (current tab) |
| F2 | Rename selected asset |
| Enter | Open selected asset |

**Transport (works whenever audio is loaded for playback — Mix, Edit, Play tab, or any preview)**

| Shortcut | Action |
|----------|--------|
| Space | Play / Pause |
| ← / → | Seek back / forward 1 second |
| Shift + ← / → | Seek back / forward 5 seconds |
| Home | Jump to start |
| End | Jump to end |
| J | Skip back 5 seconds |
| K | Stop |
| L | Skip forward 5 seconds |

## Advanced

### Provenance and C2PA

C2PA (Coalition for Content Provenance and Authenticity) is an open standard for content credentials, backed by Adobe, Microsoft, and major digital camera manufacturers.

rAIdio.bot signs every output with C2PA content credentials using ES256 (ECDSA with P-256) certificates. The signature is a tamper-evident record that documents:

1. Creator identity (name, email, URL, organization)
2. Timestamp of creation
3. AI model names and versions used
4. That the models were trained on licensed/public domain data
5. The tool that produced the output (rAIdio.bot + version)

Signatures are embedded in WAV file headers where possible. For formats that do not support embedded metadata (MP3), the signature is stored in a binary `.c2pa` sidecar file alongside the audio. FLAC, OGG, and Opus exports use a JSON sidecar (`<file>.c2pa.json`) — same ES256 cert chain as the embedded path, but our custom JSON shape rather than the JUMBF binary format that Adobe's Content Credentials Verify expects. To verify these files, use the in-app Properties dialog or the open-source verifier in the [sbom repo](https://github.com/rAIdio-bot/sbom).

The C2PA toggle in Settings controls whether signing is active. The status indicator shows: Ready (certificates found), Error (signing failed), or Missing Certs (certificates not yet generated).

### Neural watermark

In addition to the C2PA signature, every AI-generated output carries an inaudible neural watermark embedded directly in the audio samples (SilentCipher, an open-source method from Sony, MIT-licensed). Where a C2PA credential is metadata that can be stripped on re-encode or re-upload, the watermark travels in the signal itself and survives format conversion, MP3/FLAC encoding, resampling, and mixing.

The watermark carries a fixed rAIdio.bot identifier, not your personal details — it marks the audio as AI-generated by rAIdio.bot, while the C2PA credential carries your authorship. Only AI-generated audio is watermarked (music and synthetic speech); imported audio is never marked, so the watermark is never a false claim. The Properties dialog reports both layers — **Content Credentials (C2PA)** and **Neural Watermark** (Detected / Not detected) — so you or a downstream platform can verify any file.

Like all in-signal watermarks it's a high-confidence indicator rather than cryptographic proof: deliberate adversarial processing or heavy neural recompression can degrade it. It complements the C2PA credential rather than replacing it.

### Creator Identity

Fields embedded in every asset's JSON sidecar and C2PA signature:

- Display Name: Your credited name. Defaults to your OS username.
- Email: Optional. For C2PA credential attribution.
- Website/Portfolio URL: Optional. Links to your web presence.
- Publishing Channel: Optional. E.g., your YouTube or SoundCloud channel.
- Organization/Label: Optional. E.g., your record label or studio name.

All fields are stored in settings and persist across sessions.

### Backend

rAIdio.bot's AI engine is a child ComfyUI process that runs on your GPU. After many model loads / unloads in one session, GPU virtual-address-space can fragment (most visible on RTX 30/40-series cards) and the next prompt fails with a `VBAR allocation failed` error.

rAIdio.bot proactively defragments the address space after every 15 successful generations, so most users never see this. When the proactive reset isn't enough, two recovery paths are available:

- **Settings → AI Models → Force Restart Backend** — on-demand full restart, 30 seconds, no saved work lost.
- **Restart Backend** button next to the status dot — appears automatically after 3 consecutive workflow failures (or immediately on a `VBAR allocation failed` error). Same restart action, one-click access.

Both go through the same `restart_backend` Tauri command (shutdown + start), which rebuilds the ComfyUI HTTP client and the WebSocket event bridge. Models reload on the first generation after restart.

### Uninstalling rAIdio.bot

Uninstalling rAIdio.bot (via Windows **Settings → Apps**, or the bundled uninstaller) removes the application and the AI backend it shipped, but **leaves a few runtime files behind** that the app created during normal use (custom-node modifications, partially-downloaded archives, the ComfyUI runtime's `output/` / `input/` / `temp/` / `user/` directories, voice training intermediate files). The uninstaller only removes what it installed; anything created at runtime stays.

After uninstalling, if you want to fully reclaim disk space, delete the install folder (by default):

```
C:\Program Files\rAIdio.bot\
```

(adjust the path if you installed rAIdio.bot elsewhere). This may free 1-25 GB depending on how much you used the app — most of it is the ComfyUI `Backend\` directory.

**Your generated content survives the uninstall.** Your library, projects, playlists, saved voices, trained models, signing certificate, and settings live in:

```
C:\Users\<You>\AppData\Local\rAIdio.bot\
```

This is intentional — reinstalling the app picks up where you left off. If you want a **completely clean wipe** (e.g., before transferring the machine to someone else), also delete that directory. Note that deleting the `c2pa\` subfolder of your AppData root invalidates the signing certificate that proves your prior outputs are yours — back it up first if you might want to verify your prior tracks later.

### Windows SmartScreen on first launch

rAIdio.bot is code-signed by Creative Mayhem UG, so Windows should launch it without warning. If a brand-new release ever shows a "Windows protected your PC" SmartScreen prompt while the signing certificate's reputation is still building, click "More info" then "Run anyway". You can confirm the app is genuine at any time: right-click `raidio-bot.exe` → **Properties → Digital Signatures** and check the signer is Creative Mayhem UG — the full recipe is in the [`github.com/rAIdio-bot/sbom`](https://github.com/rAIdio-bot/sbom) README under "Verify your install".

### Licenses (SBOM)
The Licenses page is a Software Bill of Materials (SBOM) viewer. It lists every dependency: ComfyUI core, all custom nodes, Python packages, and their license types.

Use the search field to filter by name or license type. The summary shows the total dependency count and a breakdown by license category.

The full machine-readable SBOM (CycloneDX) is also published per release at [github.com/rAIdio-bot/sbom](https://github.com/rAIdio-bot/sbom) for OSPO ingestion. Each component carries a `com.raidio.ships-in` property (`installer-exe`, `backend-bundle`, or `xl-model`) so OSPO tooling can scope analysis to where a component actually ships.

### Global Keyboard Shortcuts

These shortcuts work from any tab:

- Ctrl+1: Music tab
- Ctrl+2: Voice tab
- Ctrl+3: Edit tab
- Ctrl+4: Mix tab
- Ctrl+5: Play tab
- F1: Help (opens the help panel for the current tab)
- F2: Rename selected asset in the Assets panel
- Enter: Open selected asset in the Assets panel
