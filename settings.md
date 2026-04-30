## Simple

### Provenance and C2PA

Every file you create in rAIdio.bot can carry a signed record that proves you made it, when you made it, and what tools were used. This is your proof of authorship.

The Provenance page in Settings lets you turn this on or off. We recommend keeping it on. The signed records are small files saved alongside your audio. Keep them: they are the closest thing available right now to proof that your music is yours.

### Creator Identity

Your name, email, website, and organization are embedded in every file you create. This is how the signed record knows who made the music. You can fill in as much or as little as you want.

Your display name defaults to your computer username. Change it to whatever you want to be credited as.

### Backend

The local AI engine that runs all your music, voice, and analysis work on your GPU. The status indicator in the bottom-left corner shows whether it's running.

If a long mixed-mode session ever stops working — usually after 30+ generations of mixed Music / Voice / Stem work — click **Force Restart Backend** in Settings → AI Models, or click **Restart Backend** when it appears next to the status dot. The restart takes about 30 seconds and doesn't lose any saved work.

### Licenses

The Licenses page lists every piece of open-source software that rAIdio.bot uses, along with each one's license type. This is here for transparency: you can see exactly what powers the app.

### Global Keyboard Shortcuts

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

### Licenses (SBOM)
The Licenses page is a Software Bill of Materials (SBOM) viewer. It lists every dependency: ComfyUI core, all custom nodes, Python packages, and their license types.

Use the search field to filter by name or license type. The summary shows the total dependency count and a breakdown by license category.

The full machine-readable SBOM (CycloneDX) is also published per release at [github.com/rAIdio-bot/sbom](https://github.com/rAIdio-bot/sbom) for OSPO ingestion.

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
