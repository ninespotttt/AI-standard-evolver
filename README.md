# Standard Evolver

Standard Evolver is a lightweight skill for building and evolving business analysis standards.

The core idea is simple:

1. Understand the user's business first.
2. Build an initial analysis standard.
3. Analyze user-provided data against that standard.
4. Adjust the standard only when the data justifies it.
5. Persist the updated rules, examples, and open questions for the next analysis.

This is the same logic behind a business graph system: the graph is only one possible interface. The real method is letting business standards become clearer through repeated data analysis.

## Use It

```text
Use $standard-evolver to help me describe my business, build an initial analysis standard, then analyze my data against it.
```

## Modes

- Setup: create the first business standard from the user's business description.
- Analyze: apply the current standard to new data and report findings.
- Evolve: update the standard from data evidence and persist the memory.

## Skill File

The actual Codex skill instructions live in [`SKILL.md`](./SKILL.md).

## Contact

Public contact: `jiangzi4560`.
