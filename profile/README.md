# VoteGA

**Nonpartisan civic information for Georgia voters.** → [votega.org](https://www.votega.org)

VoteGA publishes accessible, accurate information about Georgia elections, elected
officials, legislation, and executive action — and releases the underlying data as
free, machine-readable, openly licensed files that anyone can use.

No party affiliation. No endorsements. No visitor profiling or data sales. VoteGA is nonpartisan. Contributions must be sourced to official
records and free of advocacy framing.

---

## Open data repositories

These are updated automatically by scheduled workflows. 

Every repository has JSON, a CSV for spreadsheets and a JSON Schema.

| Repository | Contents | Start with | Updated |
|---|---|---|---|
| [ga-legislators](https://github.com/Votega/ga-legislators) | Georgia General Assembly members: the current roster (name, party, district, committees, contact, official page), each session's passage votes, and a derived voting scorecard (party unity and participation). Earlier General Assemblies back to 2017 | `latest.json`, `data/all.json` | Roster daily · votes and scorecard weekly |
| [ga-federal-legislators](https://github.com/Votega/ga-federal-legislators) | Georgia's U.S. Senators and Representatives and every roll call of the current Congress, with a frozen record of each finished Congress | `data/members.json`, `data/votes.json` | Roster daily · votes weekly |
| [ga-legislation](https://github.com/Votega/ga-legislation) | Georgia General Assembly bills and resolutions by session, and every statewide ballot measure | `latest.json`, `ga-ballot-measures.json` | Bills weekly · ballot measures as they change |
| [ga-executive-orders](https://github.com/Votega/ga-executive-orders) | The Governor's executive orders since 2020: date, number, title, category, issuing Governor and PDF link | `data/executive-orders.csv`, `data/<year>.json` | Twice daily |
| [ga-races-elections](https://github.com/Votega/ga-races-elections) | Georgia races and candidates, one folder per election cycle, and early-voting turnout by county | `data/races/manifest.json` | Races daily · early voting during each voting period |
| [ga-local-government](https://github.com/Votega/ga-local-government) | What Georgia county and city governments discuss on their published agendas and minutes (license-plate readers, data centers, land use, local taxes), classified by keyword with the source document for every mention; current boards and term history of local officials; millage rates | `latest.json` | Twice weekly · millage monthly |
| [ga-district-information](https://github.com/Votega/ga-district-information) | ZIP code, county and census-tract crosswalks to state Senate, state House and U.S. House districts | `data/zips.json`, `data/county-districts.csv` | Monthly |

Each repository's README says which paths are permanent (`sessions/…` and the per-cycle folders) and which are rewritten in place when officeholders turn over (`data/`, `latest.json`). Changes a consumer may need to act on are listed in its `CHANGES.md`, where it has one.

**Sources:** [Congress.gov](https://api.congress.gov/), [Federal Register](https://www.federalregister.gov/developers/api/v1), [FEC](https://api.open.fec.gov/), [Oyez](https://api.oyez.org/), [Georgia Governor's Office](https://gov.georgia.gov/), [Georgia Secretary of State](https://sos.ga.gov/), [Georgia General Assembly](https://www.legis.ga.gov)

Full methodology and update schedules: [votega.org/about-the-data](https://www.votega.org/about-the-data)

---

## Quick start

```bash
# Every current Georgia state legislator
curl -s https://raw.githubusercontent.com/Votega/ga-legislators/main/data/all.json

# Every Georgia executive order since 2020, one row each (CSV)
curl -s https://raw.githubusercontent.com/Votega/ga-executive-orders/main/data/executive-orders.csv
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
