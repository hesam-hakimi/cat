# AskTD - project brief for developers and agents

This page holds only what a single Story does not carry and what changes how a Story is planned or coded. Add a line here only for that reason. The Story text in Jira decides what is delivered, and the code decides what exists. How the code is organised is in docs/work/APPLICATION_MAP.md.

## The product

AskTD answers business questions about governed data in a chat. A question ends in one of four ways:

- Recipe: a reviewed definition of how one kind of question is calculated.
- Fallback lane: when no Recipe fits, the model writes SQL from retrieved metadata.
- Clarification: the application asks back when the request is ambiguous.
- Refusal: the application declines what it cannot or may not answer.

Every query passes the SQL policy: one read-only SELECT, on tables the user may read. The Registry is the governed catalogue of datasets, fields, relationships and other definitions.

## The first target

The first data product is Deposits, with three tables: Accounts, Accounts Fees and Transactions.

## Where agents work

- Agents work in the development sandbox only.
- Work in SpruceX is done by a person. What a Story needs from there is entered into the Story log by that person, as aggregates and metadata only, never as customer-level rows.

## Rules for code

- No existing recipe code is retired.
- Orchestration stays on LangGraph.
- Model access, search and document sources stay behind interfaces.
- Four decisions are open until their decision records are merged (ASKTD-77): the Registry as the source of truth, the structure of a Recipe, relationships as data, and retrieval for the fallback lane. A Story does not settle one of them on the side: where the work needs one, it becomes an open question in the Story log.
