Pull request 23: re-check at the new head, and a comment draft that the team can read. Do not start pass 3.

Read asktd-reviews/pr23-review.md first, in full. Its last re-check was at head 1b4713a, and a comment with that result is on the pull request. The author says that the open items are fixed now. Treat that as a claim.
Author's note (optional): <paste the author's reply here, or delete this line>

Limits
- Read-only. No commit, push, merge or approval. Nothing is posted to the pull request or to Jira. No tracked file changes.
- The working tree in this folder stays exactly as it is: fetch only, and no checkout, switch, stash, reset, restore, clean, pull or merge here. Run code in a separate git worktree outside this folder and remove it when you finish.
- Run only the tests and checks that the repository defines, in that worktree, on fixtures and the SQLite reference backend. No connection to any service: if a run tries to reach one, stop it and tell me. Never run a .sql script, and never run the importer with --apply. Ask me before anything that installs or downloads.
- Never open, view, search, list, copy or print an environment file, with any tool or command.
- No subagents.
- The report, the draft and your answers hold no secret, server name, connection string, customer-level row or URL, and no name or account of a person. For an error give its text with URL, HOST, ORG, REPO and USER as placeholders. Write "not confirmed" instead of a guess.

Steps
1. Fetch the pull request and record the new head. If there is no commit after 1b4713a, tell me and stop. List the commits after 1b4713a with their files and line counts, in two groups: fix for a named finding, other change. For every other change say what it does and whether it alters behaviour with all Registry flags off.
2. Give every finding and question that the report does not show as closed a status at the new head: fixed, partly fixed, not fixed or not addressed. "Fixed" needs three things: you repeated the run or request that showed the problem and it no longer shows; you read the change and it removes the cause, not only the symptom; a test exists that fails without the fix. Say where a fix changed a test, a fixture, an expected value or a document instead of the code.
3. Repeat the merge-safety checks at the new head: every switched-off route with all Registry flags unset (no file or connection created, one uniform response); an invalid flag chain at start-up; base against head with both metadata settings off (payload hashes, SQL, the 22 fixtures); the full backend suite on base and head, with the numbers.
4. Look for new problems only in the code that changed since 1b4713a. Continue the R- numbering of the report.
5. Report: add a section "Re-check at <head>" with a table (finding, earlier severity, status, evidence, what is still needed). Mark the closed findings as closed with the evidence, and update the summary and the verdict for each stage.
6. Write the comment draft to asktd-reviews/pr23-comment-<short head>.md in the form below. Do not post it: I read it and post it myself.

The comment draft

The reader is a developer of this team who has not seen the report or my prompts. The earlier comment was hard to read for that developer: it named each problem by its id, it gave an order without saying what is wrong today, and it listed one finding in up to three places. Write Markdown.

Parts, in this order:
1. The first line: "Automated re-check at head <short head>, run for the lead. It replaces the re-check comment at 1b4713a."
2. The answer, in at most five lines: can this merge with every Registry flag off (yes, no, or after the items of part 3, with their number); can the catalogue (S1) be switched on after that (with the number of items in part 4); what is not reviewed yet (the persistence layer, the SQL scripts and the stages S2 to S5); and that the reviews by the code owners for security and data governance are still required.
3. "Needed before the merge (all Registry flags off)": one block for each open item.
4. "Needed before the catalogue (S1) is switched on; not needed for the merge": one block for each open item, grouped under plain headings such as access, page tokens, configuration and secrets, data and bindings, user interface. Put this part inside a collapsed <details> block.
5. "Open questions": each question with the role that can answer it.
6. "Fixed since the last re-check": one line for each item: what was wrong, and what shows that it is fixed.

One block:
**<number>. <the problem in one plain sentence>** - <not fixed | partly fixed | new> - for <the author | the lead | another role>
- Now: what the code does today, and how the re-check saw it.
- Why it matters: the consequence.
- Needed: the smallest change or decision that closes it.
- Done when: a check that anyone can repeat.
- Where: at most two file:line references. Ref: <finding id>.

Rules
- The draft covers every finding that is not closed. Each finding appears once, in the part for what is still open about it. Its id appears only after "Ref:"; never name a problem or point to another block by an id.
- Each line of a block is one or two complete sentences. No slash pairs, no chains of nouns, no shorthand: "4 datasets, 199 fields and 0 relationships", not "4/199/0"; "a test with a caller whose access is deny all", not "deny-all tests".
- A name from the code (a route, setting, file or function) stays as it is, in backticks. Explain every other term in a few words where it first appears.
- No word that only my prompts or the report use, such as "decision 1", "pass", "addendum" or "probe".
- No greeting and no @mention.
- Only what the report supports.

Example of one block. It is invented and is not about this pull request: use it for form and tone only.
**3. The export route ignores the page size limit** - not fixed - for the author
- Now: a request with `page_size=100000` returns every row in one response. The re-check sent that request against the fixture data and received 12,400 rows.
- Why it matters: one request can use up the memory of the service.
- Needed: refuse a page size above the documented limit of 500 with the standard validation error.
- Done when: a test asks for 501 rows and gets that error, and the test fails without the change.
- Where: `src/backend/app/export/routes.py:88`. Ref: X-07.

When the draft is written, read it once from top to bottom as that developer. Rewrite every block that needs the report, another block or this prompt to be understood.

Then show me, in at most 15 lines: the new head; the number of findings by status; your answer on a merge with all Registry flags off (yes, no, or after which items, each named by its plain title); each new finding in one line; each decision that only I can take; what you could not check. Stop there
