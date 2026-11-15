# Snapshot metadata

`rules.json` and `metadata.json` are updated in one Git commit. Read both files
at the same commit SHA when you need a consistent snapshot across requests.

| Field | Contract |
| --- | --- |
| `schemaVersion` | Metadata schema version, currently `1`. |
| `version` | Monotonically increasing DynamicRule observation version. |
| `versionId` | Immutable version UUID in the DynamicRule archive. |
| `rulesSha256` | SHA-256 of compact canonical rules JSON: `static_param`, `format`, `checksum_indexes`, `checksum_constant`, in that order. Indexes are sorted numerically and duplicates retained. |
| `sourceSha256` | SHA-256 fingerprint of the captured source from the version's first observation. No source code is included. |
| `firstObservedAt` | UTC ISO timestamp when this version was first stored. |
| `publicationPreparedAt` | UTC ISO timestamp when these files were prepared for the successful GitHub update. The Git commit has its own publication history. |
| `checkAtPublication` | Matching successful collection evidence available when the files were prepared, or `null` if none is available. |
| `checkAtPublication.completedAt` | Completion time of that collection check. |
| `checkAtPublication.liveServiceValidated` | Whether that check recorded the expected signed response and an explicitly rejected incorrect-signature control. |
| `checkAtPublication.liveCheckedAt` | Time of the controlled live probe, or `null`. |
| `checkAtPublication.endpoint` | Recognized probe endpoint, or `null`. |
| `website` | The project's public website. |

The JSON is UTF-8 with a final newline. `rulesSha256` hashes the canonical compact
JSON representation, not the pretty-printed `rules.json` file bytes.

Checks happen every 15 minutes, but a successful unchanged check creates no new
version or Git commit. The badges in the README query the collector's live
status; they can be newer than `checkAtPublication`. A live validation result is
historical evidence scoped to one endpoint and time, not a general guarantee of
request acceptance.

Do not use `publicationPreparedAt` or a badge timestamp as the source's change
time. The archive only knows what it observed at successful checks.
