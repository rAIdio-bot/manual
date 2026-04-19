# rAIdio.bot — Software Bill of Materials (SBOM)

This folder carries the public, machine-readable SBOMs for rAIdio.bot
releases. Formats follow CISA's minimum-element guidance.

## Current

| File | Format | Release tag | App version |
|------|--------|-------------|-------------|
| [rAIdio.bot-RC1-UAT1.1.cdx.json](rAIdio.bot-RC1-UAT1.1.cdx.json) | CycloneDX 1.5 JSON | RC1-UAT1.1 | 0.1.0 |

## Releases

Every SBOM is also attached as an asset to a GitHub release on this
repository, for OSPO tooling that prefers release-asset URLs:

<https://github.com/rAIdio-bot/manual/releases>

Tagging convention: `sbom-<app release tag>`, e.g. `sbom-RC1-UAT1.1`.

## What's inside

The CycloneDX document describes every third-party software component
shipped inside the rAIdio.bot binary and its bundled backend:

- All Rust crates linked into the Tauri binary
- All NPM packages in the Svelte frontend bundle
- All Python packages in the bundled ComfyUI backend that we vendor
- All ComfyUI custom nodes (both upstream-unmodified and our patches)
- All AI models distributed via the Steam content depot
- System tools packaged alongside (ffmpeg, etc.)

Each component carries an SPDX license identifier, a package URL
(purl), and a homepage where available. AI model components use the
`data` component type per CycloneDX 1.5 to distinguish them from
executable code.

## Generation

SBOM generation is a two-step pipeline in the source repository:

1. `tools/generate_sbom.py` builds the internal `sbom_licenses.json`
   from `cargo metadata`, `package.json`, and a hand-maintained list
   of non-package-manager components (AI models, ComfyUI nodes,
   system tools).
2. `tools/generate_cyclonedx.py` reads that file and emits
   CycloneDX 1.5 JSON.

Both are stdlib-only Python and run without any paid tooling.

## Root-of-trust signing

The SBOM itself is not yet signed. The rAIdio.bot app's C2PA
provenance key could be repurposed for SBOM attestation in a later
release (separate from the gated-features TSA work); flagged as
future work.

## Verification

Ingest into a compatible OSPO tool:

| Tool | Command |
|------|---------|
| OWASP Dependency-Track | upload via the web UI or API |
| `cyclonedx-cli` | `cyclonedx validate --input-file rAIdio.bot-RC1-UAT1.1.cdx.json` |
| `syft`/`grype` | `grype sbom:rAIdio.bot-RC1-UAT1.1.cdx.json` |

## Feedback

Issues, questions, or requests for additional SBOM formats: open an
issue on this repository or email `info@rAIdio.bot`.
