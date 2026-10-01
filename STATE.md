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

- The Engineering Lead reads `docs/bootstrap.review.md` and merges the `bootstrap` branch
  (step 6), then installs the hooks (step 7).
- A fresh session runs the smoke cycle (step 8).
- The discovery track starts with the open decisions below (step 9).

## Open decisions

Each entry is a question the bootstrap session would have asked, with the assumption made.

1. **Crew review for `domain-core` (first open decision).** No seat can judge the Shelf
   domain core (lending rules, due dates, reminder logic). `qualified_domains` is empty on
   purpose and no seat lists `domain-core`. Today no check fails for this reason: SEATS
   passes, because no artifact names the layer or domain yet. The only failure is the DOR
   gate, which reports "C8 is open" and "D6 is open" like every open row, without naming
   `domain-core`. The signal that points at it will be SEATS refusing the first case or
   architecture artifact that names `domain-core` or a domain area no seat lists.
   Assumption: none made.
2. **Tech stack, store and hosting.** Not stated, and not assumed anywhere: not the
   platform (web or other), not the number or kind of stores. `appliance.yml` keeps the
   default `contracts/` and `migrations/` folders. Chosen by ADR at the design gate. The
   product description is not in the repository, so the mission carries no platform.
3. **Grade.** Proposed `standard`: real members and their contact details. The business
   case confirms it (C6). `appliance.yml` carries a dated comment.
4. **Merge autonomy.** Kept at `human` for main and lanes. Assumption: a first-cycle
   project with a single principal has no reason to loosen it.
5. **Reminder channel.** Email assumed. SMS and push are open. It affects data class and
   cost. Member contact details are name and email only. A phone number is added only if
   SMS is chosen, with its purpose stated.
6. **Retention.** Assumed 12 months of loan history after return, then anonymise. Contact
   details are deleted when a member leaves. The Intent Owner confirms in C4.
7. **Coordinator model.** One or several coordinators, and whether members self-register or
   are approved. Assumption: several coordinators, approved registration. Not yet in any
   artifact. It decides who owns reference data values (decision 12).
8. **Seat narrowing.** One rule for every seat, stated in `docs/roles.yml`: no stack is
   chosen, so no seat holds a stack reference, and a seat keeps a layer only when its
   charter covers that layer's work. The Architect's `deployment-runtime` was removed
   because the Operator's charter covers it. All other lists stay as the template has them
   on that rule. The Verifier keeps its two layers as challenger of the Operator's work.
   Stack references are named by ADR at the design gate, and lists are re-narrowed then.
9. **STD-003 Data quality** applicability. Open. Member uploads and email delivery data
   are undecided, so the standard is not signed not-applicable. Decided at the design
   gate, once the stack and channel are chosen. The Architect seat owns the reopen check.
10. **Data Architect seat.** Not needed on current assumptions. Revisit at the design gate
    (`docs/standards/data/README.md`).
11. **Test-run log.** `DRYRUN-QUESTIONS.md` and `DRYRUN-QUESTIONS-CHALLENGER.md` are
    dry-run artifacts. Remove them before any real use.
12. **Reference data.** Loan period defaults, reminder schedule (days before and after due)
    and tool categories are likely reference datasets. Values and owners are open and
    depend on decision 7. No assumption made.
13. **Data classes.** Confidential (contact details) and internal (tool and loan state)
    are provisional until the risk assessment (C5).
14. **Backup deletion window.** How long a leaving member's details may persist in backups.
    Open. Set in the business case.

## Left mid-task

Step 4 ran its checks on branch `bootstrap`: `run_all.py` passed 9 of 9, and the case and
design gates failed on open rows only (2026-10-01). Step 5 findings are in
`docs/bootstrap.review.md`. The bootstrap author answered all 15 (15 fixed, 0 declined),
and `open_findings` is 0. The checks were run again after the fixes, same result. The
branch is ready for step 6.
