<p align="center">
  <img src="assets/crown.svg" width="80" height="80" alt="Blue DynamicRule crown" />
</p>
<h1 align="center">OnlyFans Dynamic Rules</h1>
<p align="center"><strong>Current rules. Clear provenance. A history you can follow.</strong></p>
<p align="center">
  <a href="https://www.dynamicrule.com">Open DynamicRule ↗</a> ·
  <a href="https://raw.githubusercontent.com/Fanclan/OnlyFans-Dynamic-Rules/main/rules.json">Latest rules JSON</a> ·
  <a href="https://github.com/Fanclan/OnlyFans-Dynamic-Rules/commits/main/">Version history</a>
</p>
<p align="center">
  <a href="https://www.dynamicrule.com"><img alt="Collection status" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fwww.dynamicrule.com%2Fapi%2Fpublic%2Fbadge%3Fmetric%3Dstatus&amp;style=flat-square" /></a>
  <a href="https://www.dynamicrule.com"><img alt="Last collection check" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fwww.dynamicrule.com%2Fapi%2Fpublic%2Fbadge%3Fmetric%3Dlast-check&amp;style=flat-square" /></a>
  <a href="rules.json"><img alt="Current stored version" src="https://img.shields.io/endpoint?url=https%3A%2F%2Fwww.dynamicrule.com%2Fapi%2Fpublic%2Fbadge%3Fmetric%3Dversion&amp;style=flat-square" /></a>
</p>

---

This repository publishes the latest canonical signing-rule snapshot collected by
[DynamicRule](https://www.dynamicrule.com), made by the team at
[**Fanclan.io**](https://fanclan.io). Collection checks run every **15 minutes**.
A new commit is created when the rule values change, so unchanged checks do not
fill the history with duplicate snapshots.

### Get the JSON — no API key

```sh
curl -fsSL https://raw.githubusercontent.com/Fanclan/OnlyFans-Dynamic-Rules/main/rules.json
```

| File | What it contains |
| --- | --- |
| [`rules.json`](rules.json) | The four canonical signing fields, ready to parse. |
| [`metadata.json`](metadata.json) | Version, fingerprints, first observation, and the check recorded when this snapshot was prepared. |
| [Commit history](https://github.com/Fanclan/OnlyFans-Dynamic-Rules/commits/main/) | Published changes, including a return to previously observed values. |

For a reproducible result, replace `main` in the raw URL with a commit SHA.
GitHub may cache raw responses; the JSON describes the most recently published
snapshot and may briefly lag a completed collection.

### What each field means

| Field | Meaning |
| --- | --- |
| `static_param` | Fixed string included with the timestamp, exact request path/query, and user ID in the SHA-1 input. |
| `format` | Signature template: prefix, SHA-1 digest, checksum in hexadecimal, and suffix. |
| `checksum_indexes` | Digest character positions used in the checksum. Repeated indexes count more than once. |
| `checksum_constant` | Fixed value added to the character-code sum before taking its absolute value. |

Keep the request path and query exactly as sent, including parameter order,
repeated parameters, and percent escapes. These rules do not supply account
credentials, sessions, or permission to access private content.

### Public files and the hosted API

**These GitHub files are public and require no DynamicRule API key.**
The hosted [DynamicRule service](https://www.dynamicrule.com) provides latest and
historical lookups, timestamp queries, and request signing through its API.
Hosted `/api/rules*` and `/api/sign` requests require a key issued through your
[DynamicRule account](https://www.dynamicrule.com/account). GitHub raw downloads,
the public dashboard, and `/api/public/status` and `/api/public/badge` collection
metadata do not.

Visit [DynamicRule](https://www.dynamicrule.com) for the dashboard,
[API documentation](https://www.dynamicrule.com/docs), and [account access](https://www.dynamicrule.com/account). Keep issued keys private and send them only to the hosted
service, never to GitHub or OnlyFans.

### Freshness and validation

- **First observed** records when DynamicRule first stored these rule values.
  It is not an upstream publication timestamp.
- **Check at publication** is a snapshot of matching collection evidence when
  this repository update was prepared. It does not advance on unchanged checks.
- **The cached badges above** report collection status separately. The public
  endpoint caches for 60 seconds with a 30-second stale window; Shields requests
  a 300-second cache. A newer badge timestamp does not imply a new commit, and
  the display may lag a completed check.
- Live validation requires an expected API response and rejection of a request
  signed with deliberately incorrect rules. It applies only to the endpoint and
  time recorded; it does not establish that every possible request will succeed.
- Failed capture or validation keeps the last successful stored rules. A durable
  publication queue retries GitHub failures without replacing newer snapshots
  with older ones.

See the [metadata contract](docs/metadata.md) for the precise file fields.
No browser bundles, session cookies, account IDs, request signatures, or raw
upstream responses are published here.

### Project and license

Project-authored documentation and assets are available under the [MIT license](LICENSE).
The JSON files contain observed rule data; the license does not grant rights to
OnlyFans content or third-party software. DynamicRule is an independent project
and is not affiliated with OnlyFans.

<p align="center">Built with care by <a href="https://fanclan.io"><strong>Fanclan.io</strong></a> · <a href="https://www.dynamicrule.com">DynamicRule.com</a></p>
