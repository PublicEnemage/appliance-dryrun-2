---
cycle: 1
phase: setup
active_tracks: []
updated: 2026-10-01
---

# State

The cockpit card. Rewritten each session, archived each cycle to `docs/archive/`.
Capped at 200 lines by check E9.

## Now

Cycle 1: setup, smoke cycle and discovery. No product code this cycle.

## Next

- Bootstrap fills the constitution slots, roles and CODEOWNERS (`BOOTSTRAP.md`).
- A fresh session challenges the bootstrap output against the floor.
- The Engineering Lead approves.

## Open decisions

Each entry is a question the bootstrap session would have asked, with the assumption made.

1. **Crew review for `domain-core` (first open decision).** No seat can judge the Shelf
   domain core (lending rules, due dates, reminder logic). `qualified_domains` and the
   `domain-core` layer are empty on purpose. Checks D6 and C8 will fail at the design and
   case gates until a crew review names a seat or a reference. Assumption: none made.
2. **Tech stack, store and hosting.** Not stated. `appliance.yml` keeps the default
   `contracts/` and `migrations/` folders. Chosen by ADR at the design gate.
3. **Grade.** Proposed `standard`: real members and their contact details. The business
   case confirms it (C6).
4. **Merge autonomy.** Kept at `human` for main and lanes. Assumption: a first-cycle
   project with a single principal has no reason to loosen it.
5. **Reminder channel.** Email assumed. SMS and push are open. It affects data class and cost.
6. **Retention.** Assumed 12 months of loan history after return, then anonymise. Contact
   details are deleted when a member leaves. The Intent Owner confirms in C4.
7. **Coordinator model.** One or several coordinators, and whether members self-register or
   are approved. Assumption: several coordinators, approved registration. Not yet in any artifact.
8. **Seat narrowing.** The Architect's `deployment-runtime` qualification was removed: no
   stack or runtime reference exists to judge it. The Operator holds that layer.
9. **STD-003 Data quality** signed not-applicable (D11.1): no external datasets. The
   Engineering Lead's merge is the signature.
10. **Data Architect seat.** Not needed now (`docs/standards/data/README.md`).
11. **Test-run log.** `DRYRUN-QUESTIONS.md` is a dry-run artifact. Remove it before any real use.

## Left mid-task

Bootstrap step 4 is complete on branch `bootstrap`. Step 5 is done: findings are in
`docs/bootstrap.review.md` (15 open, none high). The bootstrap author answers each one, then step 6.
