---
artifact: "bootstrap"
challenger_seat: "Verifier"
session: "fresh Verifier session, 2026-10-01"
open_findings: 15
---

# Review of the bootstrap branch

Scope: everything changed on `bootstrap` since template commit 8660f2d (`git diff
8660f2d..bootstrap`), reviewed against `CLAUDE.md`, `docs/roles.yml`, `appliance.yml`,
`docs/standards/data/` and `BOOTSTRAP.md`. The draft standards' clauses are not judged in
detail. Their adaptation sections are read only for consistency with the constitution and
`STATE.md`. Reviewer ran `run_all.py` plus the case and design gates: the plain run passes
9 of 9 and both gates fail on open rows only.

Result: no high findings. Eight medium findings, seven low. Most medium findings share one
cause: assumptions were written into approved-on-merge artifacts (constitution, standards)
without a matching entry under "Open decisions".

Severity:
- **high:** blocks approval until fixed.
- **medium:** blocks approval until the author answers it, with a fix or a reasoned decline.
- **low:** may be deferred to the backlog with a note in the Answer column.

| # | Finding | Severity | Answer | Closed? |
| --- | --- | --- | --- | --- |
| 1 | `CLAUDE.md` Mission says Shelf "is a web app". `STATE.md` open decision 2 says the tech stack is not stated. A platform choice sits in the constitution that the Intent Owner approves by merging, and it is logged nowhere. Either the product description says "web app" (then say so and drop it from decision 2) or it does not (then remove it from the mission). The reviewer was not given the description and cannot tell which. | medium | | |
| 2 | STD-001 adaptation assumes "one relational store" and a "few hundred members". The Data Architect section in `docs/standards/data/README.md` then uses "one persistent store is assumed" to say trigger 1 is not met. Decision 2 says the store is not chosen and lists no assumption. The member count has no source in any artifact. Log the store assumption under decision 2 or remove it, and remove or source the scale figure. | medium | | |
| 3 | STD-005 adaptation lists "optional phone" among the member contact details. Decision 5 assumes email only, and principle 2 says collecting less beats a richer profile. A phone number serves no stated purpose, and it implies the open SMS channel. No open decision covers it. Remove it, or log it as an open decision with its purpose. | medium | | |
| 4 | Seat narrowing is applied once, to the Architect's `deployment-runtime`, on the ground that "no stack or runtime reference exists". That ground holds for every layer: no stack is chosen, so no seat has a reference for `data`, `services-apis`, `frontend` or `integration` either. The Verifier keeps `deployment-runtime` and `operations`, the Builder and Operator keep theirs, and the Architect keeps four layers. The step says to narrow each seat's list to what its holder can judge. Either narrow all lists on one stated rule, or state why a charter alone qualifies the other layers. Decision 8 gives only the one removal. | medium | | |
| 5 | STD-003 is signed not-applicable in D11.1 on the ground "no imports, feeds, third-party data APIs or bulk uploads". The standard's own scope is "imports, feeds, third-party APIs, user uploads". Tool photos or descriptions uploaded by members are user uploads, and delivery or bounce data from a third-party email service (decision 5, still open) is external data. Both are undecided, because the stack and channel are open. The reopen condition ("if an import is added") has no check and no owner. STD-003 itself carries no pointer to its not-applicable row. Narrow the reason to what is actually decided, or leave STD-003 as an adapted draft until the stack and channel are chosen. | medium | | |
| 6 | `STATE.md` decision 1 says "Checks D6 and C8 will fail ... until a crew review". Today the SEATS check passes with `qualified_domains` empty. The only failure is the DOR gate, which fails on every open row, so it does not point at `domain-core`. The step says to let the check fail, and no check currently fails for this reason. State the real current behaviour in decision 1, and name where the signal will appear. | medium | | |
| 7 | STD-004 adaptation sets product facts inside a standard: loan period defaults, a reminder schedule of days before and after due, and "the coordinator owns the values". None is in the open decisions. Coordinator ownership of reference data also depends on decision 7 (one or several coordinators), which the same list marks as unresolved. Log them, or reduce the adaptation to the format and ownership rule the standard needs. | medium | | |
| 8 | The author's own log (`DRYRUN-QUESTIONS.md`, M3) records reading `tools/checks/check_dor.py`, `check_seats.py`, `README.md`, `docs/enforcement.yml` and listing `docs/method/` file names, all outside the step 4 manifest. Session protocol 1 forbids that. The shape of the child row D11.1 (`rule`, `reason`, `approver` fields) came from that reading, not from the procedure. Record the shape as a method gap, and answer whether D11.1 is the intended way to sign one standard not-applicable. | medium | | |
| 9 | Step 4 requires the session to run the checks. No artifact records that it did or what the result was. `STATE.md` says only that step 4 is complete. Record the run and its result in `STATE.md`. | low | | |
| 10 | `appliance.yml` is unchanged from the template. The grade "proposal" and the merge autonomy "setting" are identical to the template defaults, so the file does not show that anyone proposed or set them. Only `STATE.md` decisions 3 and 4 do. Add a comment or a dated line in `appliance.yml`, or accept as is with a note. | low | | |
| 11 | `CLAUDE.md` marks only the mission and principles as drafts. Step 6 says the merge also approves roles, the grade proposal and the not-applicable row, and the Seats table is not marked. The comment above `holders` in `docs/roles.yml` ("Rename Human 1 ...") and the `.github/CODEOWNERS` comment ("Bootstrap replaces the handle below") both read as undone work, though both are done or moot. Reword the stale comments or note the handle was already correct. | low | | |
| 12 | `STATE.md` "Next" still lists "Bootstrap fills the constitution slots, roles and CODEOWNERS". That is done. Update it to the remaining steps. | low | | |
| 13 | `DRYRUN-QUESTIONS.md` M1 says the injected `CLAUDE.md` "carried an extra rule" that is "not in the repo's file". The rule ("Never declare a qualification, a seat or an approval to make a check pass") is in the repo's `CLAUDE.md` and in template commit 8660f2d. The log misstates the repo. Correct the entry. | low | | |
| 14 | STD-005 adaptation fixes data classes (confidential, internal) before the risk assessment (floor row C5), which clause 1 names as their source. It also says deletion reaches backups "within a stated window", and no window is stated anywhere. Mark the classes as provisional pending C5 and either state the window or log it as open. | low | | |
| 15 | The Data Architect decision is written into the shared standards README under a dated, project-specific heading, and it reads "Not needed now" while trigger 5 is "not assessable". The step says to record it there, so placement is as directed. The conclusion is firmer than its evidence. Reword to "not needed on current assumptions, revisit at the design gate". | low | | |
