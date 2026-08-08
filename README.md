# lean

[<img src="https://static2.klipy.com/ii/4e7bea9f7a3371424e6c16ebc93252fe/3a/9d/grRrgtiMZ4SuiEmv1.gif" width="320" alt="Ashe pours a purple drink">](https://klipy.com/gifs/ashe-1)

A development method for agent-driven work, expressed as a cyclic graph of eight phases and five gates.

The contract — types, names, signatures — is the durable artifact. A task is shaped, contracted, built, checked by an agent that has not seen the implementation, and recorded as a commit message. Failure conditions route backward to the phase that owns them rather than forward into rework.

## Install

```
.claude/skills/lean/
├── SKILL.md
├── method-graph.mmd
└── README.md
```

Drops into any project. `SKILL.md` is the whole method; `method-graph.mmd` is the same graph standalone, for rendering.

## When it fires

Any coding, refactoring or debugging task. The description is deliberately broad — this is the default path, not a specialist tool.

## What follows from it

Three practices fall out of the gates rather than being imposed:

- **No durable spec.** The plan covers the current task and becomes the commit message on merge. `git log` is the history, `git blame` the index. Nothing outside the repository holds state.
- **No comments.** If prose is needed to explain the code, the name or the type is wrong. A rule the type cannot express becomes a precondition in the signature.
- **No example-based unit tests.** Properties and invariants, run by an independent agent. A test written by whoever read the implementation is a mirror, and mirrors ratify bugs.

None of these is a goal. Each is what remains once the contract carries the meaning.

## What it costs

`P8 · STANDING TENSIONS` is the honest ledger. Comments capture what code cannot; theory dies with the session; unstated behaviour becomes a contract anyway; regulated work needs artifacts git does not hold; agent-authored code carries a measured maintenance cost.

These are accepted, not solved. When one fires, take a local exception with a recorded reason. Do not reverse the method globally on a single case.

## Reading the graph

Diamonds are gates. Solid edges advance. Dotted edges are backreferences and the label is the condition that fires them. Dashed nodes are tensions.

Every non-gate node cites its source. Name the anchor rather than describing the technique — "the invariant broke under a call sequence" is a specific obligation with a specific owner.
