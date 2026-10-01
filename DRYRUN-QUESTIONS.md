# Dry-run questions (test of the bootstrap procedure; remove before real use)

Session: bootstrap, Architect seat, branch `bootstrap`, 2026-10-01.
Label: PRODUCT = only the human can decide. METHOD = the procedure should have answered it.

## Context at session start

Other projects' files were in my context before I read anything. The session's injected
project instructions held `CLAUDE.md` text from three clones: `/home/claude/agentic-dev-appliance`,
`/home/claude/appliance-dryrun` and `/home/claude/appliance-dryrun-2`. The user's memory
snapshot (profile and notes naming WorldSIM and the "development appliance" idea) was also
in context. I did not open any directory outside this repository. See M1.

## PRODUCT questions (7)

**P1. Tech stack, datastore, hosting.**
Source: BOOTSTRAP step 4 ("contracts and migrations folders if the stack is known").
Assumption: unknown. Defaults kept (`contracts/`, `migrations/`). One relational store assumed
only in the STD-001 adaptation. Listed in STATE.md open decision 2.

**P2. Reminder channel.**
Source: product description ("return on time with reminders"); STD-002 and STD-005 depend on it.
Assumption: email. SMS and push open. STATE.md decision 5.

**P3. Retention period for loan history and contact details.**
Source: STD-005 clause 2; floor row C4.
Assumption: loan history 12 months after return, then anonymise; contacts deleted on leaving.
STATE.md decision 6.

**P4. Coordinator and registration model.**
Source: product description ("a volunteer coordinator"). One or several coordinators? Do
members self-register or get approved?
Assumption: several coordinators, approved registration. Not written into any artifact.
STATE.md decision 7.

**P5. Is STD-003 (data quality) not-applicable?**
Source: BOOTSTRAP step 4 (adapt each standard or mark not-applicable). Depends on whether
Shelf will ever import members or tools in bulk.
Assumption: no imports, so signed not-applicable as row D11.1. STATE.md decision 9.

**P6. Merge autonomy.**
Source: BOOTSTRAP step 4 ("sets merge autonomy"). No criterion is given, and the choice is a
risk appetite only the human holds.
Assumption: kept at `human` for main and lanes. STATE.md decision 4.

**P7. Who holds Shelf domain knowledge (lending rules, due dates, reminder logic)?**
Source: roles.yml comment on `domain-core`; BOOTSTRAP step 4 (leave empty, record crew review).
Assumption: none made, per the rule. Left `qualified_domains` empty. STATE.md decision 1.

## METHOD questions (7)

**M1. Injected context disagreed with the files on disk.**
The `CLAUDE.md` text injected for this repo already had mission, principles and seats filled
and differed in wording from what I then wrote. The file on disk was the unfilled template,
and the working tree was clean. The rule "Never declare a qualification, a seat or an approval
to make a check pass" is in the file on disk and in template commit 8660f2d.
The injected text for the other two clones overlaps with it. The procedure has no rule for
which source wins or for isolating a session from sibling clones.
Assumption: the file on disk is the constitution. I wrote my own mission and principles
from the product description and did not copy the injected text. The rule above was
already in the repo's file, so there was nothing to add.

**M2. What "narrow `qualified_layers` to what its holder can judge" means for an agent seat.**
Source: BOOTSTRAP step 4; roles.yml header ("a generic agent session is qualified only when
its charter, instructions or a named reference give it the knowledge"). No stack is chosen,
so no reference exists for any layer. Taken literally, most lists would be emptied.
Assumption: one narrowing only. Removed `deployment-runtime` from the Architect, since the
Operator holds that layer and no runtime reference exists. Other lists kept, because their
charters name the layer. This is a judgment call the procedure should define.

**M3. Reading outside the manifest, and how a single standard is signed not-applicable.**
Source: CLAUDE.md session protocol 1 ("read nothing else unless the manifest names it"),
BOOTSTRAP step 4 (mark not-applicable in `docs/dor/checklist.yml`).
The checklist has one row, D11, for all five standards. The procedure does not say to use a
child row such as D11.1. I read `tools/checks/check_dor.py` to learn the shape, plus
`README.md`, `docs/enforcement.yml` and `tools/checks/check_seats.py` for context. I also ran
`git log` and `ls docs`, and a grep that listed file names mentioning "PublicEnemage"
(`docs/method/*` among them) without opening them. I did not open `docs/method/`.
Assumption: child row `D11.1` with `status`, `reason` and `approver` fields.

**M4. How deep to adapt a data standard, and where to write the adaptation.**
Source: BOOTSTRAP step 4 ("adapts each draft data standard"). No instruction on editing
clauses versus appending, or on what counts as adapted.
Assumption: appended a "Shelf adaptation (bootstrap draft)" section to STD-001, 002, 004 and
005. Clauses untouched. Front matter already had `author_seat: Architect` and
`challenger_seat: Verifier`, so the "sets" instruction was already met. Status stays `draft`.
STD-003 left unedited because it is signed not-applicable.

**M5. The template already carried the human's handle.**
`.github/CODEOWNERS` already read `@PublicEnemage` although its comment says bootstrap
replaces the handle. `README.md` and `docs/method/` also name this handle. It is unclear
whether the template was prefilled for this test or the step is a no-op. Assumption: no change
needed to CODEOWNERS. The handle matches the human seat holder I was given.

**M6. Formats the procedure leaves unspecified.**
(a) How to mark mission and principles as drafts: I used an italic line under each heading.
(b) How to word "Open decisions" in STATE.md: I used a numbered list, question plus assumption.
(c) Whether to update STATE.md `cycle`, `phase` and `updated` front matter: left as is, `updated` was already today.
(d) How to record the Data Architect decision: a dated section in the data README.
(e) Where to log the Step 4 outcome: "Left mid-task" in STATE.md, pointing at step 5.

**M7. Branch and push mechanics.**
The clone was already on a local `bootstrap` branch with the template commit `8660f2d` as its
only commit, and `origin/bootstrap` already existed. Step 4 says "commits on a `bootstrap`
branch" but says nothing about pushing; the session protocol says only that agents never push
to `main`. Assumption: push `bootstrap` to origin, as the task instructed. Step 5 needs the
"template commit" for its diff; it is `8660f2d`, and the procedure does not name it.

## Not done (outside this session's role)

Steps 1 to 3, 5, 6, 7, 8 and 9. I did not check that rulesets exist on the repository.

## Answering session

Session: Architect seat (bootstrap author), fresh session, branch `bootstrap`, 2026-10-01.
Points where the procedure did not tell me what to do. Label: PRODUCT or METHOD.

**A1. METHOD. Which session answers, and under which step.**
BOOTSTRAP step 5 says "the bootstrap author then answers each finding". Steps 4, 5 and 8 are
fresh sessions, and the answering has no step number or session type of its own. Assumption: a
fresh session holding the Architect seat, the same seat as step 4, does it. No input manifest
exists for it. I read: `CLAUDE.md`, `STATE.md`, `BOOTSTRAP.md`, the review file and template,
`appliance.yml`, `docs/roles.yml`, CODEOWNERS, the data standards, `docs/dor/checklist.yml`,
this log, the diff against the template commit, and a grep in `docs/dor/floor.yml` for D6 and C8.
The last three go beyond the step 4 manifest.

**A2. METHOD. Meaning of the "Closed?" column.**
The procedure defines Answer ("fixed, or declined with a reason") but not Closed?. Assumption:
the author writes "Yes" once answered. The challenger would confirm, but no step re-checks
fixes. Assumption: no second challenge round, since step 5 says the branch is ready once every
finding is answered and `open_findings` is 0.

**A3. METHOD. Who updates `open_findings`.**
The review template says it counts findings with no answer plus unfixed highs. The file is the
challenger's. Assumption: the author sets it to 0 after answering.

**A4. METHOD. Fix or defer the low findings.**
The template lets lows be "deferred to the backlog with a note". No backlog artifact exists in
the repository. Assumption: fix all 15, so no backlog is needed.

**A5. METHOD. Whether a finding may be answered by removing the thing it flags.**
Findings 2, 3 and 5 are answered by removing text or a checklist row (D11.1) rather than by
logging an open decision. Assumption: removal is a valid fix when the text had no source.

**A6. METHOD. Whether charter alone qualifies a layer (finding 4).**
roles.yml says a generic session is qualified when its charter, instructions or a named
reference give it the knowledge. It does not say if a charter that names the work is enough.
Assumption: yes. I stated one rule in `docs/roles.yml` and kept all lists except the original
removal. The Verifier's two layers are kept as challenger of the Operator's artifacts, though
its charter does not name them. That is a judgment the procedure leaves open.

**A7. PRODUCT. Platform of the product (finding 1).**
The product description is not in the repository, and I was not given it. I cannot tell whether
Shelf is a web app. Assumption: no platform. The Intent Owner confirms the description.

**A8. PRODUCT. STD-003 applicability (finding 5).**
Whether members upload files, and whether an email service returns delivery data, are product
and stack decisions. Assumption: neither is decided, so STD-003 stays an adapted draft and the
row stays open. The Engineering Lead decides at the design gate.

**A9. METHOD. How to sign one standard not-applicable (finding 8).**
Step 4 says to mark a standard not-applicable in `docs/dor/checklist.yml` with a reason and
`approver: Engineering Lead`. The checklist has one row, D11, for five standards. The procedure
gives no shape for one standard. Assumption: do not invent one. I removed D11.1 and left D11
open. The procedure should state the shape, or say that D11 is signed only when all five are.

**A10. METHOD. Fixing an earlier session's dry-run log (finding 13).**
The log is a test artifact written by the step 4 session. Assumption: the author corrects it
in place, and answers in this section rather than rewriting M3.

**A11. METHOD. Context from sibling clones again.**
My session context again held `CLAUDE.md` text from three clones, and the user's memory
snapshot. They differ in wording from the file on disk (the injected copy of this repo's file
has no "web app" and no draft markers). Assumption: the file on disk governs. The procedure
has no rule for it. I did not open any directory outside this repository.

**A12. METHOD. Where to record the answering result.**
Assumption: `STATE.md` "Left mid-task", as in step 4. The procedure names no place.
