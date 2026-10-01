# Dry-run questions, smoke session (test of the bootstrap procedure; remove before real use)

Session: fresh agent, `BOOTSTRAP.md` steps 7 and 8, main at bff79c5, 2026-10-01.
Label: PRODUCT = only the human can decide. METHOD = the procedure should have answered it.

## PRODUCT questions (0)

None. The smoke cycle touches no product decision.

## METHOD questions (12)

**M1. Item 7 (E15): is the edit committed or not?** The text says "commit a migration, then
run ... after editing it". Assumption: tried both. Uncommitted edit passes (check diffs
`--base..HEAD`); committed edit refuses. The procedure should say "commit the edit too".

**M2. Items 1, 2, 8: what is a valid artifact to break?** No text says which type to use,
or what front matter makes it valid apart from the break. A hand-made ADR from the template
carries `parents: [ARCH-001]`, which does not exist, so it fails for a second reason.
Assumption: used a `role-proposal` (root type, no parents) so each break fails alone. Added
a passing control for each. The procedure should name a type per item or ship fixtures.

**M3. Item 2: which seats?** An approver must be human for most types. Author and approver
both `Engineering Lead` gave exactly one finding. Both `Architect` gave a second one
(needs a human approver). Assumption: used the first. Not stated in the text.

**M4. Item 3: which row to delete?** Text says "a deleted floor row". Assumption: C3.

**M5. Item 4: where does the test file go and what shape?** Assumption: `tests/test_*.py`
with an `if True: return` body. The lint scans the whole repo outside `tests/fixtures`.

**M6. Item 5: what makes a complete entry?** The format is in `docs/templates/registry-entry.md`
and the docstring of `check_registry.py`, not in BOOTSTRAP.md. Assumption: two complete
entries RG-001 and RG-003, so the gap is the only fault. A near-miss must name a check.

**M7. Item 6: contract format and folder.** Not in BOOTSTRAP.md. Found the example in
`docs/standards/data/STD-002-data-contracts.md` and the folder in `appliance.yml`
(`contracts/`, which does not exist until created). Assumption: created it with one file.

**M8. Item 7: migration file name and type.** Not stated, and no store is chosen.
Assumption: `migrations/001-init.sql` in the default folder. Any file name works.

**M9. Item 8: how to build the architecture artifact.** "In review" means front matter
`status: in-review`, not stated. The template has `{{...}}` slots, dummy layer seats and
parents CD-001, NFR-001 that do not exist. Assumption: filled only id, title and status and
ran `check_diagrams.py` alone, since the full run would fail on E10 and SEATS too. Added a
control with all diagrams. The procedure does not say whether to run one check or all.

**M10. Item 9: "the pre-push hook, run directly".** Assumption: `.githooks/pre-push` with no
arguments (git passes remote name and URL; the hook ignores them). Which breaking change is
not stated. Assumption: the wrong-folder RP from item 1a. The hook stops at the first
failing command, so pytest never ran in the refused case.

**M11. Step 7 and the log file.** The hook refuses on untracked files, and the task asks for
a log file in the repo. Assumption: kept the log outside the repo until the final commit,
and ran the hook only on clean trees.

**M12. Where the results go and the date.** The procedure names `docs/archive/smoke-<date>.md`
but not the date format. Assumption: `2026-10-01`, as in `STATE.md`. It also says the file
reaches `main` by pull request and `STATE.md` links to it. This session was told not to open
one, so neither was done. Not run: the `STATE.md` link, the pull request.

## Items I could not run from the text alone

None blocked. Items 1, 2, 3, 4, 5, 6, 7, 8, 9 all ran, each with the assumptions above.
Items 7 and 8 needed the most outside reading (the docstring of `check_migrations.py`,
the architecture template).
