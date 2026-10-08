# Security Policy

DEVI Registry is used in digital evidence workflows, so security and correctness reports are taken seriously and handled first.

## Supported versions

| Version | Supported |
| --- | --- |
| 1.0.x | Yes |

## Reporting a vulnerability

Please report vulnerabilities privately. Do not open a public issue.

- **Email:** admin@deviops.app, with "DEVI Registry security" in the subject line.
- **GitHub:** use **Report a vulnerability** on the Security tab of this repository to open a private advisory.

Include the DEVI Registry version, the operating system, and the steps or input needed to reproduce the problem. **Do not include real evidence, case material, keys, passphrases, or personal data.** A synthetic file or a description of the input is enough.

We aim to reply within 3 business days and to keep you informed while a fix is prepared. Once a fix is released, we will credit you in the release notes unless you would rather not be named.

## In scope

Reports are especially welcome for anything that could:

- present a wrong record, status, or content hash;
- make offline lookup use the network without the examiner choosing a link;
- get around the signature or SHA-256 checks in the update process;
- ship third-party product logos or trademarked marks without a clear license to do so.

## Security design

- Record lookup in the Windows app does not use the network.
- No telemetry is collected or sent.
- The only network feature is the optional update check. It is off by default and runs only when you ask, or when you turn on "Check for updates when the app opens". It is one HTTPS GET of a signed version file from the DEVI download host, with no machine identifier and no query string. A download starts only after you confirm it, and only after its SHA-256 matches the signed version file. See [docs/UPDATES.md](docs/UPDATES.md).
- Public UI in this repository must not rely on third-party product logos or generic colored letter-tile avatars as stand-ins for apps. Prefer neutral text labels and DEVI brand assets.

## Code signing

The update feed signature is separate from Authenticode code signing. Release packages and the DEVI program files are Authenticode-signed through Microsoft Artifact Signing, with a timestamp. Signing happens only on a maintainer's computer; no signing material is in this repository or in GitHub Actions. Windows SmartScreen can still warn about a newly signed release. Check downloads against the published SHA-256 values.

## No certification claim

This policy does not claim a certification, an accreditation, or a particular laboratory method. Each lab or agency should validate the build it uses under its own procedures.
