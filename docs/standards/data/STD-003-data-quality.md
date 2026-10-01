---
id: STD-003
type: standard
title: Data quality
status: draft
author_seat: Architect
challenger_seat: Verifier
approver: Engineering Lead
parents: []
approved_at: null
---

# Data quality

- **Kind:** craft standard
- **Owning seat:** Architect, or the Data Architect once that seat is adopted. The
  Verifier challenges, and may not be the seat that designed the rules it applies.
- **Applies to:** every dataset that enters the system from outside: imports, feeds,
  third-party APIs, user uploads

A draft default. Adapt the clauses at bootstrap, then challenge and approve this file.
A rejection must cite a clause number.

## Clauses

1. **Every external dataset has a quality profile.** The profile names its validity rules,
   completeness threshold and freshness limit, in a file next to its contract.
2. **Provenance is recorded with the data.** Source, retrieval date, version or vintage,
   and licence travel with each dataset and are visible where its numbers are shown.
3. **Checks run at ingest.** Data that fails a rule is quarantined with the reason. It is
   never silently dropped, defaulted or passed through.
4. **Failures are loud.** A failed check raises an alert or fails the job. A missing or
   empty dataset is an error, not a valid state. (WorldSIM NM-060: an empty table produced
   a bare error with no diagnostic.)
5. **Quality is reported.** Each run writes a quality record: rows in, rows accepted, rows
   quarantined, and rules failed. The record is kept for the retention period of the data.

## Shelf adaptation (bootstrap draft)

- Applicability is open. No external dataset is known today, so the standard may end up
  not applicable. Two inputs are undecided, because the stack and reminder channel are
  open: member-uploaded tool photos or files (user uploads), and delivery or bounce data
  from a third-party email service (an external feed).
- Decide at the design gate. If neither exists, the Engineering Lead signs the standard
  not-applicable in `docs/dor/checklist.yml` then, with the decided facts as the reason,
  and the owner of the reopen condition is the Architect seat, who checks it at each
  architecture change. Until then the clauses stand as written and the row stays open.
