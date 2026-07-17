# VoteGA

**Nonpartisan civic information for Georgia voters.** → [votega.org](https://www.votega.org)

VoteGA publishes accessible, accurate information about Georgia elections, elected
officials, legislation, and executive action — and releases the underlying data as
free, machine-readable, openly licensed files that anyone can use.

No party affiliation. No endorsements. No visitor profiling or data sales.

---

## Open data repositories

These are updated automatically by scheduled workflows. Use them directly — no key,
no signup, no rate limit.

| Repository | Contents | Format | Updated |
|---|---|---|---|
| [ga-legislators](https://github.com/Votega/ga-legislators) | Current GA House & Senate members (158th General Assembly) — name, party, district, committees, contact, official page | `data/all.json` | Daily |
| [ga-federal-legislators](https://github.com/Votega/ga-federal-legislators) | Georgia's 2 U.S. Senators and 14 U.S. Representatives | JSON | Weekly |
| [ga-legislation](https://github.com/Votega/ga-legislation) | GA General Assembly bills, 2025–26 session (adapted from Open States) | JSON | Daily |
| [ga-executive-orders](https://github.com/Votega/ga-executive-orders) | Georgia Governor's executive orders, 2023–present — date, number, title, category, PDF link | One JSON file per year | On publication |
| [ga-races-elections](https://github.com/Votega/ga-races-elections) | 2026 Georgia races and candidates | JSON | As SOS publishes |

**Sources:** [Open States](https://openstates.org/) (Plural Policy) · [Congress.gov](https://api.congress.gov/) ·
[Federal Register](https://www.federalregister.gov/developers/api/v1) · [FEC](https://api.open.fec.gov/) ·
[Oyez](https://api.oyez.org/) · [gov.georgia.gov](https://gov.georgia.gov/) · Georgia Secretary of State

Full methodology and update schedules: [votega.org/about-the-data](https://www.votega.org/about-the-data)

---

## Quick start

```bash
# Every current Georgia state legislator
curl -s https://raw.githubusercontent.com/Votega/ga-legislators/main/data/all.json

# Georgia executive orders signed in 2026
curl -s https://raw.githubusercontent.com/Votega/ga-executive-orders/main/data/2026.json
```

```python
import urllib.request, json

URL = "https://raw.githubusercontent.com/Votega/ga-legislators/main/data/all.json"
members = json.load(urllib.request.urlopen(URL))["members"]

senate = [m for m in members if m["chamber"] == "Senate"]
print(f"{len(senate)} Georgia state senators")
```

---

## Who this is for

- **Civic app developers** — structured GA data without building or maintaining a pipeline
- **Journalists** — a current, citable roster and bill list you can join against your own data
- **Researchers** — daily snapshots with a stable schema and full commit history
- **Anyone** — attribution appreciated, not required beyond the license terms

## Contributing

Spot a wrong district, a stale phone number, a missing email? Open an issue or PR on the
relevant repo. Accepted corrections flow into our override files and appear on votega.org
on the next scheduled run.

We accept: data corrections, schema suggestions, bug reports, new source ideas.
We don't accept: partisan framing, endorsements, or advocacy content.

## Contact

[admin@votega.org](mailto:admin@votega.org)
