/story-plan ASKTD-77

If the line above did not load the skill story-plan, load it now and follow it.

This run corrects the existing plan before its gate. It is not a new plan: change only what the notes below name in docs/work/ASKTD-77/plan.md, read again only what a note needs, add one plan entry to the log, commit, and stop at the gate.

Notes from the lead:
1. Decision 2 is worded wrongly in the table of decided statements. The decision is: "The application creates no table. The table-creation scripts are kept in one folder of the repository, and running them against a database is separate work." Use these words in the plan and in record 0014.
2. The open Registry pull request (number 23) is to be corrected for the same decisions before it merges: its author moves table creation out of the application into one folder of scripts, and states in its decision record that a Recipe defined in code gets no special case. So records 0014 and 0015 do not present these two points as a lasting difference from the records of that pull request. Each states the decision, and says that the pull request, at the commit named in the plan, still shows otherwise and is to be corrected.
3. Wherever a new record cites a record or the code of that pull request, it names the commit at which it was read.
4. DW-4 holds for all four records, not for 0014 only.
5. Questions 1 to 8 get no answer now. Each goes, with its options, into "What Is Not Decided" of the record or records it belongs to. Question 9 is the person item of DW-1 and is not content of a record.

Before you stop, show me at most 8 lines: what changed in the plan, in short; the gate line to copy; and what "inherited canary refusal" in your last summary means.
