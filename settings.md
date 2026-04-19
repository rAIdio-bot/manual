## Simple

### Provenance and C2PA

Every file you create in rAIdio.bot can carry a signed record that proves you made it, when you made it, and what tools were used. This is your proof of authorship.

The Provenance page in Settings lets you turn this on or off. We recommend keeping it on. The signed records are small files saved alongside your audio. Keep them: they are the closest thing available right now to proof that your music is yours.

### Creator Identity

Your name, email, website, and organization are embedded in every file you create. This is how the signed record knows who made the music. You can fill in as much or as little as you want.

Your display name defaults to your computer username. Change it to whatever you want to be credited as.

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

C2PA (Coalition for Content Provenance and Authenticity) is an open standard for content credentials, adopted by Adobe, Microsoft, and major camera manufacturers.

rAIdio.bot signs every output with C2PA content credentials using ES256 (ECDSA with P-256) certificates. The signature is a tamper-evident record that documents:

1. Creator identity (name, email, URL, organization)
2. Timestamp of creation
3. AI model names and versions used
4. That the models were trained on licensed/public domain data
5. The tool that produced the output (rAIdio.bot + version)

Signatures are embedded in WAV file headers where possible. For formats that do not support embedded metadata (MP3), the signature is stored in the JSON sidecar file.

The C2PA toggle in Settings controls whether signing is active. The status indicator shows: Ready (certificates found), Error (signing failed), or Missing Certs (certificates not yet generated).

### Creator Identity

Fields embedded in every asset's JSON sidecar and C2PA signature:

- Display Name: Your credited name. Defaults to your OS username.
- Email: Optional. For C2PA credential attribution.
- Website/Portfolio URL: Optional. Links to your web presence.
- Publishing Channel: Optional. E.g., your YouTube or SoundCloud channel.
- Organization/Label: Optional. E.g., your record label or studio name.

All fields are stored in settings and persist across sessions.

### Licenses (SBOM)
The Licenses page is a Software Bill of Materials (SBOM) viewer. It lists every dependency: ComfyUI core, all custom nodes, Python packages, and their license types.

Use the search field to filter by name or license type. The summary shows the total dependency count and a breakdown by license category.

This data is loaded from sbom_licenses.json.

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
