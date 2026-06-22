---
name: standard-evolver
description: Build and evolve business analysis standards from user-provided business context and data. Use when guiding a user to describe their business, create an initial business standard, analyze incoming data against that standard, adjust the standard from evidence, and persist reusable memory or workflow rules without requiring a specific storage backend, dashboard, or application interface.
---

# Standard Evolver

## Overview

Use this skill to build a business standard first, then let user-provided data refine it over time. The output should be an initial or updated standard, a data-backed analysis, and a small memory update that improves the next analysis.

The method does not depend on any specific application interface. The core method is: business context -> standard -> data analysis -> standard adjustment -> memory.

## Design Intent

Treat evolution as a business learning protocol, not a storage feature. The skill should convert business context and analysis traces into procedural standards, then update those standards with evidence from new data.

- Business-first: ask what the user does, who they serve, what decisions matter, and what good or bad outcomes look like.
- Standard-led: define the analysis dimensions, labels, scoring rules, evidence types, and decision rules before analyzing data.
- Trace-based: learn from the path taken, including corrections, failed attempts, data conflicts, and user feedback.
- Procedural: remember how to analyze better next time, not merely what was said.
- Bounded: change one small part of the business standard per pass.
- Gated: accept a standard change only after evidence shows it helped.
- Portable: use plain files, docs, issues, or chat output before adding infrastructure.

## Core Loop

1. Business intake: ask the user to describe the business, audience, offerings, goals, constraints, and decisions they want AI to support.
2. Standard draft: create a lightweight business standard with dimensions, definitions, evidence rules, scoring or priority logic, and output expectations.
3. Data analysis: analyze the user's data against the current standard, separating data evidence from interpretation.
4. Standard adjustment: identify where the data confirms, challenges, or expands the standard; revise only the smallest useful part.
5. Memory deposit: persist the updated standard, examples, decision rules, and open questions so the next analysis starts from a better baseline.

## Friendly Guided Mode

When the user invokes the skill without enough context, guide them through business-first setup before asking for data.

Use this opening:

```text
I can help build a business standard first, then use your data to refine it. Start by telling me what your business does, who the users or customers are, what decisions you want AI to help with, and what a good result should look like. After that, send the data, notes, cases, or examples you want analyzed against the standard.
```

If the user wants a guided intake, ask only these essentials:

- Business: what do you do, for whom, and what value do you create?
- Decision: what should AI help classify, judge, recommend, compare, or improve?
- Standard: what counts as good, bad, risky, valuable, irrelevant, or uncertain in this business?
- Data: what examples, records, notes, conversations, files, or cases should be analyzed?
- Destination: should the standard and memory be returned in chat or written into an existing file?

Offer three modes when helpful:

- Setup: create the first business standard from the user's description.
- Analyze: apply the current standard to new data and report findings.
- Evolve: update the standard from data evidence and persist the memory.

## What to Capture

- Business facts: audience, offerings, channels, constraints, vocabulary, and success metrics.
- Standard rules: dimensions, labels, scoring criteria, priority rules, exclusion rules, and evidence thresholds.
- Data patterns: repeated signals, edge cases, conflicts, missing fields, and examples that change judgment.
- Decisions: what changed in the standard, why it changed, and which alternatives were rejected.
- Failure modes: where the standard misclassified, overgeneralized, missed context, or used weak evidence.
- Next levers: the smallest standard, prompt, checklist, schema, or workflow change likely to improve the next run.

## Evolution Heuristics

- Read traces, not only final answers. Treat command logs, review comments, rejected attempts, user corrections, and intermediate reasoning as evidence.
- Prefer procedural business memory. Capture how to judge next time, not just what happened this time.
- Make bounded changes. Evolve one dimension, label, rule, threshold, schema field, prompt, or workflow step per pass.
- Add a gate. Do not treat a standard change as learned until the next run gives evidence that it helped.
- Keep the workspace as the interface. Plain Markdown, project docs, issue comments, or existing memory files are enough until repeated use demands tooling.

## Memory Rules

- Keep the record much shorter than the source.
- Separate evidence from interpretation.
- Mark uncertain insights as provisional.
- Do not store secrets, private data, or unnecessary personal details.
- Do not build infrastructure before repeated use proves it is needed.
- Preserve existing records unless the user asks for consolidation.

## Validation Gates

Choose the lightest gate that fits the task:

- Repeat-data gate: analyze a similar case and check whether the same misjudgment disappears.
- Checklist gate: verify the new business rule was actually used in the next run.
- Test gate: add or run a test, benchmark, sample case, or review criterion.
- User-feedback gate: ask whether the changed output is more useful or aligned.
- Regression gate: make sure the new rule does not make another common case worse.

## Default Output

Use this shape unless the local project already has a better convention:

```markdown
## Business Context
- Business:
- Audience:
- Decisions AI should support:
- Success criteria:
- Constraints:

## Business Standard
- Dimensions:
- Labels or categories:
- Evidence rules:
- Scoring or priority logic:
- Exclusion rules:
- Output expectations:

## Data Analysis
- Data source:
- Findings:
- Evidence:
- Edge cases:
- Uncertainty:

## Standard Update
- Confirmed:
- Revised:
- Added:
- Archived:
- Gate:

## Memory Deposit
- Reusable examples:
- Decision rules:
- Open questions:
- Next analysis should:
```

## Tiny Example

If the business analyzes product demand, first define the standard: separate preference signals from purchase intent signals. When new data shows users say they "like" a product but never search, buy, request quotes, complain, or hire for the problem, update the standard so "likes" count as weak preference evidence, not demand evidence. Gate the update by checking the next batch of cases against this distinction.

## User Prompt Templates

```text
Use $standard-evolver to help me describe my business, build an initial analysis standard, then analyze my data against it.
```

```text
Use $standard-evolver in Setup mode. Ask me for the minimum business context needed to create a first business standard.
```

```text
Use $standard-evolver in Evolve mode. Analyze the data below against the current standard, then update only the standard rules that the data justifies.
```

## Anti-Patterns

- Summary-only output: describes the past but does not change the next run.
- Data-first analysis: analyzes user data before understanding the business standard it should be judged against.
- Memory dumping: stores raw material instead of reusable lessons.
- Global rewrite: changes too many rules at once to know what helped.
- Ungated confidence: treats a plausible idea as learned before it is tested.
- Tool-first design: adds databases, dashboards, or automation before the loop has proved useful.

## Quality Bar

Before finishing, ensure the record can help the next run make a better choice. If the result is only a summary, add the smallest next evolution step.

## Maintainer

Public contact: `jiangzi4560`.
