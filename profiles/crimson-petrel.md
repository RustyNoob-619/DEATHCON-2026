# CRIMSON PETREL

*Meridian Threat Research · profile v6 · last updated 2026-03-02 · TLP:CLEAR · a fictional composite for training: no real group, person, organisation or country is described.*

- **Calling card.** Fouls the colony and eats what is left.
- **Faction.** Carrion Syndicate
- **Kind.** Criminal, loud
- **Wants.** Money, from whoever is weakest
- **Hours (UTC).** 05:00 to 14:00
- **Public record.** 2024 MTR report with a configuration (a mutex, a user agent, a campaign tag and an RC4 key) and a Rich hash

**Summary.** A criminal syndicate, loud and quick, that mails widely and extorts whoever pays. A long public indicator trail since 2023. Confidence: high on scale, medium on motive.

![CRIMSON PETREL: the diamond as MTR publishes it](../../figures/fig5b.png)

## Attribute details

| ID | Attribute | Detail | Confidence |
|---|---|---|---|
| A1 | Operator | The Carrion Syndicate. | Medium |
| A2 | Intent | Money. | High |
| C1 | Loader | GULLNEST (EXE). Reads its mutex, user agent, campaign tag and key from a configuration block and posts to a path that starts `/gn/`. | High |
| C2 | Cryptography | RC4 with a 12-character key protects the configuration and the traffic. The routine is public code. The key published in the 2024 report is `c4rR10n-P3tr`. | High |
| C3 | Build | Visual Studio 2015 (build 24215). A genuine Rich header (hash `c8a9333b855bd1ca28a2960e042cc33a`, published), linker 14.0, imports the Visual Studio 2015 C runtime and WS2_32. | High |
| C4 | Debug paths | None in the three builds seen. | Medium |
| I1 | Domains | Names of the form `gull-nest-N`; three are listed in the 2024 report (4, 9 and 12). | Medium |
| I2 | Servers | Bulk-hosted VPS at one low-cost provider. Free public certificates, 90 days. | Medium |
| I3 | Hosting | Bulk hosting at several providers. | Low |
| V1 | Sectors | Any weak target: co-ops, ferry lines, small utilities, clinics. | Medium |
| V2 | First targets | General mailboxes. | Medium |
| M1 | Timestamp | 05:00 to 14:00 UTC. | Medium |
| M2 | Phase | Quick. | Medium |
| M3 | Result | Extortion. | High |
| M4 | Direction | Outward. | Medium |
| M5 | Methodology | Invoice-themed mail with an archive attachment. | High |
| M6 | Resources | Cheap tooling, public code. | Medium |

**Network identifiers.** Mutex `Global\PetrelSync2_4`. User agent `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0)`. Campaign tags look like `gn-24b` (two letters, a hyphen, two digits and a letter).

**Public record.** *Gullnest and the carrion trade* (MTR, 20 June 2024) published the mutex, the user agent, the campaign tag, the RC4 key, the Rich-header hash of the three builds and three domains. Other vendors reuse these indicators in feeds.

**Procedure examples (ATT&CK).** T1566.001 (attachment in mail); T1573.001 (RC4 over HTTP and HTTPS); T1041 (exfiltration over the C2 channel); T1486 (data encrypted for impact).

**Gaps.** Our view of the Syndicate's tradecraft after delivery is thin.
