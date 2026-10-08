<p align="center">
  <img src="assets/brand/devi-readme-banner.svg" alt="DEVI" width="600">
</p>

<h1 align="center">DEVI Registry</h1>

<p align="center">
  A sourced JSON and YAML database of application and artifact metadata for examiners.
</p>

<p align="center">
  <a href="https://deviops.app/tools/devi-registry/">Download</a> ·
  <a href="CHANGELOG.md">Changelog</a> ·
  <a href="SECURITY.md">Security</a> ·
  <a href="https://deviops.app">deviops.app</a>
</p>

---

DEVI Registry is a database of application and artifact metadata for examiners. Every record cites the public sources it was taken from and carries a status that says how far the claim was checked. The Windows app answers the question an examiner has on scene or at the bench: found this app, now what.

It is a reference, not a finding about a case. A record says what a cited source says, not what is on a given device or what a provider will produce.

DEVI Registry is part of **DEVI**, a set of tools built by experienced digital forensic examiners for examiners. It does not carry a court, standards-body, or laboratory certification. Each lab or agency should validate it under its own procedures before relying on it in casework. Nothing in it is legal advice.

This repository is the home for the DEVI Registry source release. Windows builds and the data zip are published at [deviops.app/tools/devi-registry/](https://deviops.app/tools/devi-registry/). `src/DeviRegistry.Core` holds the published C# project skeleton (shared identity constants); fuller application source and data snapshots land under `src/` and `data/` as they are released. Community health files and brand assets follow the same layout as [DEVI Validate](https://github.com/Deviops-app/DEVI-Validate). Before any public UI lands here, third-party logos and colored letter-tile avatar patterns stay out of the tree.

## What it does

- Ships sourced records that list sources by title, publisher, address, and the date each was read.
- Marks every claim verified, reported, or disputed, with a statement of what was and was not checked.
- Provides an offline Windows app to look up an app by name, Android package, or Apple bundle ID.
- Documents artifact file names and paths as open-source parsers report them, with known limits.
- Links published law-enforcement guides, request portals, preservation, and emergency disclosure pages.
- Publishes the snapshot as JSON and YAML (one file for the whole set, and one file per record group).

## Offline and local-first

- **Offline app.** Search and record display do not use the network. A preservation, legal-process, or source link opens in your browser only when you choose it.
- **No telemetry.** Searches and lookups are not sent anywhere. The website never receives your searches.
- **Content hash.** The app checks the bundled data's content hash before it shows a record.

### The one network feature: an optional update check

- It is **off by default**. It runs only when you choose **Check for updates**, or turn on "Check for updates when the app opens".
- It is one HTTPS request for a **signed** version file. It sends the product name and version and nothing else: no machine identifier, and never any case details, keys, file names, or hashes.
- A download starts only after you confirm it, and only after its SHA-256 matches the signed version file. Nothing is installed silently.

See [docs/UPDATES.md](docs/UPDATES.md) for details.

## Download

The current release is **DEVI Registry 1.0.4** for Windows x64 (bundled data **1.0.0**). Download it from <https://deviops.app/tools/devi-registry/>. The installer, the portable zip, and the data zip are published only there. GitHub releases carry the release notes and the SHA-256 values below, not the files.

| Package | SHA-256 |
| --- | --- |
| `DEVI-Registry-Setup-1.0.4-win-x64.exe` (installer) | `8080264fc52d5bbc0bf1e43db35b659c69310bb5bbe911e92c95f11e68cbd9b2` |
| `DEVI-Registry-1.0.4-win-x64.zip` (portable) | `c0ea79e9fd6a608f63367de72ffcc22923f110f632bca5db0333bc0a62e990f6` |
| `DEVI-Registry-1.0.0.zip` (data) | `05bfa3dc4bc761c3fe974055c6ef7acd102e16b01836ed8efa36db823e79e0d3` |

The Windows app packages include the .NET runtime, so nothing else needs to be installed. In the portable zip, `app\DEVI-Registry.exe` is the desktop app. The data zip is JSON and YAML only (no program).

### Check your download

Before you run a download, confirm its SHA-256 matches the table above. In PowerShell:

```powershell
Get-FileHash .\DEVI-Registry-Setup-1.0.4-win-x64.exe -Algorithm SHA256
```

In Command Prompt:

```bat
certutil -hashfile DEVI-Registry-Setup-1.0.4-win-x64.exe SHA256
```

On Linux or macOS:

```bash
sha256sum DEVI-Registry-Setup-1.0.4-win-x64.exe
```

The value must match this README, the GitHub release notes, and the DEVI website. If it does not match, do not run the file.

The installer, its uninstaller, and the desktop app are Authenticode-signed through Microsoft Artifact Signing, with a timestamp. A valid signature does not replace the SHA-256 check. Windows SmartScreen can still warn about a newly signed release.

## Repository layout

| Path | Contents |
| --- | --- |
| `src/` | C# solution projects (see `DeviRegistry.sln` and `src/README.md`) |
| `data/` | Reserved for JSON/YAML registry snapshots when published |
| `docs` | Update check notes and repository status |
| `assets/brand` | DEVI brand assets used by the app |
| `.github` | Issue and pull request templates, Dependabot, CI |

## Build from source

Build with the [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) (see `global.json`):

```bash
git clone https://github.com/Deviops-app/DEVI-Registry.git
cd DEVI-Registry

dotnet restore DeviRegistry.sln
dotnet build DeviRegistry.sln --configuration Release
```

See [BUILDING.md](BUILDING.md) and [docs/STATUS.md](docs/STATUS.md). Community files, documentation, and brand assets mirror [DEVI Validate](https://github.com/Deviops-app/DEVI-Validate).

## Testing

See [TESTING.md](TESTING.md). Do not commit real case data, provider returns, keys, or personal information.

## Contributing

Bug reports, documentation fixes, and carefully sourced contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) and the [Code of Conduct](CODE_OF_CONDUCT.md) first. Report security issues privately as described in [SECURITY.md](SECURITY.md). Never attach real evidence, case material, keys, or personal data to an issue or pull request.

## License

Copyright 2026 The DEVI Registry authors.

Licensed under the [Apache License, Version 2.0](LICENSE). See [NOTICE](NOTICE) and [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for third-party components.

As Section 6 of the license states, it does not grant permission to use the DEVI name or logo, except as needed to describe where the software came from.
