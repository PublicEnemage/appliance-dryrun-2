# Dry-run questions, challenger session (test of the bootstrap procedure; remove before real use)

Session: fresh Verifier seat, branch `bootstrap`, 2026-10-01. BOOTSTRAP.md step 5.
Label: PRODUCT = only the human can decide. METHOD = the procedure should have answered it.

## PRODUCT questions (3)

**P1. Is the mission's "web app" what the human said?**
Source: step 5 manifest includes "the product description the human gives". The challenger
was not given it. Assumption: judged internal consistency only (mission against `STATE.md`
decision 2). Raised as review finding 1.

**P2. Is STD-003 really not-applicable?**
Source: floor row D11 and checklist row D11.1. Depends on whether members upload tool photos
or files, and on the reminder provider's delivery data. Only the human knows the product.
Assumption: not decidable now. Raised as finding 5.

**P3. Is `@PublicEnemage` the right handle?**
Source: step 3 (the human names the seat holders, outside every manifest). Assumption: the
handle matches the repository owner (`PublicEnemage/appliance-dryrun-2`), so accepted. Not
raised as a finding.

## METHOD questions (10)

**M1. Where does the challenger get the product description?**
Source: step 5 says the manifest is "the same as step 4", and step 4 lists the product
description "the human gives". A fresh session has no way to receive it.
Assumption: proceed without it. See P1.

**M2. Which commit is "the template commit"?**
Source: step 5. BOOTSTRAP.md does not name it. The task prompt supplied 8660f2d, and the
history shows the same. Assumption: 8660f2d.

**M3. Review file name and front matter.**
Source: `docs/templates/review.md` says save beside the artifact as
`{{PREFIX-NNN}}-{{slug}}.review.md` with `artifact: PREFIX-NNN`. Step 5 says
`docs/bootstrap.review.md`. The bootstrap has no artifact id, and `docs/artifact-types.yml`
describes review files only as sitting beside an artifact. Assumption: the step's path wins,
`artifact: "bootstrap"`, `session: "fresh Verifier session, <date>"`.

**M4. Initial `open_findings`, and who answers.**
Source: review template ("counts findings with no answer, plus every high not yet fixed")
and step 5 ("the bootstrap author then answers"). The author session has ended, so the answerer
is unclear. Assumption: set `open_findings` to the total, because nothing is answered yet.
A new author session answers.

**M5. Severity calibration for a bootstrap.**
Source: review template defines high as "blocks approval until fixed" with no criteria.
Assumption: high only when merging would put something wrong or unsafe into governance
(a fabricated qualification or approval, a broken check, a wrong seat holder). None found.

**M6. What may a challenger read and run beyond the manifest?**
Source: session protocol 1 versus the need to verify claims. I read `docs/dor/checklist.yml`
and `docs/dor/floor.yml` in full (the checklist is edited in the diff but is not in the
manifest), the full data standards files, and `DRYRUN-QUESTIONS.md` (it is in the diff). I
ran `run_all.py` and the case and design gates but did not open `tools/` source or `docs/method/`.
Assumption: running the checks is allowed, reading their source is not.

**M7. Is this session fresh and independent?**
Source: step 5 ("A fresh session"). My attribution reminder carries the same Claude-Session
URL as the author's commit trailer (`session_01RMMkuMJPqF4Zr2nWSVrNwh`). My context also held
`CLAUDE.md` text from two sibling clones and `agentic-dev-appliance`, plus the user's memory
profile. Nothing says how to verify freshness or isolate a session. Assumption: proceed, did
not open any directory outside this repository, and disclose here.

**M8. Which `CLAUDE.md` governs when the injected copy differs from disk?**
Source: session protocol 1. The copy injected at session start had different mission wording
from the file on disk. Assumption: the file on disk, as the author did (author log M1).

**M9. Depth of review of the adaptation sections.**
Source: step 5 ("does not judge the draft standards' clauses in detail"). The adaptations are
new text on those standards. Assumption: judged for consistency with the constitution,
roles and `STATE.md`, not for clause quality.

**M10. Update `STATE.md`, and push.**
Source: session protocol 4 requires a `STATE.md` update, but the task says not to fix the
author's work. Step 5 says commit only; the task says push `bootstrap`. Assumption: edit only
the "Left mid-task" section to point at the review, and push the branch as the task says.
Whether the review file passes check E10 in `docs/` is checked after writing it.
