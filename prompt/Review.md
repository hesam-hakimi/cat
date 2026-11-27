Pull request 23: revise the comment draft for head 3724a87. The limits of my last message apply. No new review work except step 1.

1. One number first. The backend total at this head (1,468 passed, 4 failed, 3 skipped) equals the total that the report recorded at 917b46a, although tests were added and removed since then. Tell me the commit of the worktree in which the head suite ran, and how many backend tests the commits after 917b46a added and removed. If the suite did not run at 3724a87, run it again there and correct the report and the draft.

2. Two decisions of mine. Record them in the report and apply them to the draft.
- R-02: the removal of the unused migration helper is accepted as the fix, without a test. It moves to the fixed items.
- P1-Q1: the two backend tests that fail on the base as well are not a condition for this merge. The question stays, with one sentence that it is a follow-up for the repository and does not block this pull request.

3. Revise asktd-reviews/pr23-comment-3724a87.md. The structure of the blocks is good and stays. Change this:
- The answer at the top. After the first line write "Can this merge with every Registry flag off? Not yet." and then a numbered list of what is left, one line each, that says who does what in words a new team member understands. Then one line on the catalogue (S1) with the number of open items, one line on what is not reviewed yet, and one line on the code-owner reviews. No chains of nouns such as "executed flag-off frontend evidence" or "migration-boundary evidence".
- Titles. A title says what is wrong in everyday words. For example, "Flag-off frontend compatibility has code and tests but no executed result" becomes "The frontend fix is in the code, but the re-check could not run its tests or the build", and "Static Chat execution still bypasses governed dependency reconciliation" becomes "A static Recipe can still run after a field that it requires has disappeared from the governed metadata". Rewrite every title of that kind.
- One block for P1-09 and P1-Q2, with both ids after "Ref:": the same frontend test run and build at this head answers both.
- P1-06: ask only for what you checked, the runtime document. Say in one sentence that the re-check could not read the description of the pull request.
- Questions carry "not answered" or "partly answered", not "not fixed".
- Number the blocks from 1 to the end through all parts, so that every number exists once.
- In every block, rewrite a sentence that a new team member would have to read twice: shorter sentences, everyday words, and a term explained where it first appears (for example "integrity mismatch", "static source path", "seed adapter", "publication-head generation").

Then show me the answer to step 1, the new top part of the draft down to the first heading, and the titles of all blocks. Stop there.
