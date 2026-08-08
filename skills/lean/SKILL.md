\---

name: lean

description: Method for building software. Use for any coding, refactoring or debugging task.

\---



The contract is the artifact. Everything else is input to it, a check on it, or a record of why it changed.



A task enters at `P1 · SHAPE` and leaves through `P5 · RECORD`, passing five gates. `P7 · CONTEXT ECONOMY` applies at every phase, not at one point in the sequence.



\## Gates



| Gate | Holds when |

|---|---|

| `one task in flight` | No second plan is live. Finish or abandon before starting. |

| `contract is the only durable description` | Types, names and signatures carry the meaning. A rule the type cannot express becomes a precondition in the signature. Nothing restates the code in prose. |

| `verifier has not read the implementation` | The checking agent works from the contract in a separate context with no shared history. A verifier that has seen the code inherits its assumptions. |

| `change closes net-negative, or states why not` | Superseded paths are unreachable and gone. Growth needs a reason on the record. |

| `contract satisfied and recorded` | Properties hold, and the commit message carries the reason the contract changed. |



\## Traversal



Walk each phase head to tail. Dotted edges are backreferences and the label is the condition that fires them — take them and re-walk from where you land. `P8 · STANDING TENSIONS` is dashed: those anchors are costs this method accepts, not problems it solves. When one fires, take a local exception and record the reason rather than reversing the method.



\## Graph



```mermaid

flowchart TB



%% solid = forward step   dotted = backreference, label is the condition that triggers it

%% diamond = gate: a condition that must hold before the phase advances



&#x20; G\_START{"one task in flight"}

&#x20; G\_CONTRACT{"contract is the only durable description"}

&#x20; G\_INDEP{"verifier has not read the implementation"}

&#x20; G\_NET{"change closes net-negative, or states why not"}

&#x20; G\_DONE{"contract satisfied and recorded"}



&#x20; subgraph P1\["P1 · SHAPE"]

&#x20;   direction TB

&#x20;   JTBD\["Jobs To Be Done — Clayton Christensen"]

&#x20;   XYPROB\["XY Problem"]

&#x20;   EARS\["EARS Requirements Syntax — Alistair Mavin"]

&#x20;   INVEST\["INVEST — Bill Wake"]

&#x20;   THINSLICE\["Thin Vertical Slice — Alistair Cockburn"]

&#x20;   SPIKE\["Spike Solution — Kent Beck"]

&#x20;   YAGNI\["YAGNI — Ron Jeffries"]

&#x20;   LIVEPLAN\["Live Plan, Current Task Only"]

&#x20;   JTBD --> XYPROB --> EARS --> INVEST --> THINSLICE

&#x20;   THINSLICE --> SPIKE --> YAGNI --> LIVEPLAN

&#x20; end



&#x20; subgraph P2\["P2 · CONTRACT"]

&#x20;   direction TB

&#x20;   UBIQ\["Ubiquitous Language — Eric Evans"]

&#x20;   CLEANNAME\["Intention-Revealing Names — Robert C. Martin"]

&#x20;   MILNER\["Well-Typed Programs Cannot Go Wrong — Robin Milner"]

&#x20;   ILLEGAL\["Make Illegal States Unrepresentable — Yaron Minsky"]

&#x20;   PARSEDV\["Parse, Don't Validate — Alexis King"]

&#x20;   WADLER\["Theorems for Free — Philip Wadler"]

&#x20;   DBC\["Design by Contract — Bertrand Meyer"]

&#x20;   CQS\["Command-Query Separation — Bertrand Meyer"]

&#x20;   PARNAS\["Information Hiding — David Parnas"]

&#x20;   DEEPMOD\["Deep Modules — John Ousterhout"]

&#x20;   ACCEPTPORT\["Ports and Adapters — Alistair Cockburn"]

&#x20;   COMMENTSMELL\["A Comment Is a Deodorant for Bad Smells — Fowler and Beck"]

&#x20;   UBIQ --> CLEANNAME --> MILNER --> ILLEGAL --> PARSEDV --> WADLER

&#x20;   WADLER --> DBC --> CQS --> PARNAS --> DEEPMOD --> ACCEPTPORT

&#x20;   CLEANNAME --> COMMENTSMELL

&#x20; end



&#x20; subgraph P3\["P3 · BUILD"]

&#x20;   direction TB

&#x20;   TOTALITY\["Total Functional Programming — David Turner"]

&#x20;   GUARD\["Guard Clause — Martin Fowler"]

&#x20;   SLAP\["Single Level of Abstraction — Kent Beck"]

&#x20;   STRUCTPROG\["Structured Programming — Edsger Dijkstra"]

&#x20;   IMMUT\["Purely Functional Data Structures — Chris Okasaki"]

&#x20;   OWNERSHIP\["Ownership and Borrowing — Matsakis and Klock"]

&#x20;   DRY\["Don't Repeat Yourself — Hunt and Thomas"]

&#x20;   KISS\["KISS — Kelly Johnson"]

&#x20;   TOTALITY --> GUARD --> SLAP --> STRUCTPROG

&#x20;   STRUCTPROG --> IMMUT --> OWNERSHIP --> DRY --> KISS

&#x20; end



&#x20; subgraph P4\["P4 · VERIFY"]

&#x20;   direction TB

&#x20;   DIJKSTRATEST\["Testing Shows Presence, Never Absence — Edsger Dijkstra"]

&#x20;   ORACLEBIAS\["Implementation-Biased Test Generation — LLM test-generation study"]

&#x20;   INDEPVER\["Independence-Based Verification — Grabowski"]

&#x20;   ADVERSARIAL\["Adversarial Red-Blue Agent Verification — Thukkaram"]

&#x20;   HUGHES\["QuickCheck Property-Based Testing — Claessen and Hughes"]

&#x20;   PBTAGENT\["Agentic Property-Based Testing — Hypothesis agent study"]

&#x20;   INVARIANTRUN\["Stateful Invariant Runs over Random Call Sequences — Foundry and Hypothesis"]

&#x20;   METAMORPH\["Metamorphic Testing — T. Y. Chen"]

&#x20;   FUZZ\["Coverage-Guided Fuzzing — Michał Zalewski"]

&#x20;   CONTRACTTEST\["Consumer-Driven Contract Test — Ian Robinson"]

&#x20;   CHARTEST\["Characterization Test, Legacy Only — Michael Feathers"]

&#x20;   AGENTQA\["Agent-Native QA over MCP"]

&#x20;   LLMJUDGE\["LLM as a Judge"]

&#x20;   SANITIZE\["Sanitizer and Static Analysis Gate"]

&#x20;   DIJKSTRATEST --> ORACLEBIAS --> INDEPVER --> ADVERSARIAL

&#x20;   ADVERSARIAL --> HUGHES --> PBTAGENT --> INVARIANTRUN --> METAMORPH --> FUZZ

&#x20;   FUZZ --> CONTRACTTEST --> CHARTEST

&#x20;   AGENTQA --> LLMJUDGE --> SANITIZE

&#x20; end



&#x20; subgraph P5\["P5 · RECORD"]

&#x20;   direction TB

&#x20;   CONVCOM\["Conventional Commits"]

&#x20;   RULE5072\["50/72 Commit Format — Tim Pope"]

&#x20;   WHYNOTWHAT\["The Diff Records What, the Message Records Why"]

&#x20;   GITSTATE\["Git Is the State — stateless runtime, Kapale"]

&#x20;   BLAME\["git blame as the Index"]

&#x20;   BISECT\["git bisect as the Regression Oracle — Linus Torvalds"]

&#x20;   SEMVER\["Semantic Versioning — Tom Preston-Werner"]

&#x20;   ADRN\["ADR, Irreversible Forks Only — Michael Nygard"]

&#x20;   CONVCOM --> RULE5072 --> WHYNOTWHAT --> GITSTATE --> BLAME --> BISECT

&#x20;   BISECT --> SEMVER --> ADRN

&#x20; end



&#x20; subgraph P6\["P6 · PRESSURE"]

&#x20;   direction TB

&#x20;   NODELETE\["Agents Avoid Deleting Code — Ebrahimi et al."]

&#x20;   GUARDANDGO\["Guard-and-Go Fallback Accumulation — Vector Labs"]

&#x20;   TYPE4\["Type-4 Semantic Clones in Agent Pull Requests"]

&#x20;   CHURN\["Rising Churn and Duplication — Harding and Kloster, GitClear"]

&#x20;   SLOPDRIFT\["Behavioural Drift over Long Trajectories — Orlanski et al."]

&#x20;   DELETIONGATE\["Deletion-Completeness Check"]

&#x20;   DIFFBUDGET\["Net-Negative Diff Target"]

&#x20;   REACHABLE\["Reachability Analysis"]

&#x20;   TARPIT\["Out of the Tar Pit — Moseley and Marks"]

&#x20;   LEANSW\["A Plea for Lean Software — Niklaus Wirth"]

&#x20;   KOLMOGOROV\["Kolmogorov Complexity — Kolmogorov and Chaitin"]

&#x20;   NODELETE --> GUARDANDGO --> TYPE4 --> CHURN --> SLOPDRIFT

&#x20;   SLOPDRIFT --> DELETIONGATE --> REACHABLE --> DIFFBUDGET

&#x20;   TARPIT --> LEANSW --> KOLMOGOROV

&#x20; end



&#x20; subgraph P7\["P7 · CONTEXT ECONOMY"]

&#x20;   direction TB

&#x20;   SMALLESTSET\["The Smallest Set of High-Signal Tokens"]

&#x20;   CONTEXTROT\["Context Rot — Hong et al."]

&#x20;   REWORK\["Rework Loops Dominate Token Spend"]

&#x20;   PROGDISC\["Progressive Disclosure via SKILL.md"]

&#x20;   HEADERONLY\["Header Loads, Body Fires on Trigger"]

&#x20;   AGENTSMD\["AGENTS.md Hierarchical, Not Encyclopaedic"]

&#x20;   NODUPEDOC\["Reference, Never Restate"]

&#x20;   SUBAGENT\["Subagent Context Isolation"]

&#x20;   COMPACT\["Phase-Boundary Compaction"]

&#x20;   OBSCOMPRESS\["Observational Context Compression"]

&#x20;   MEMTOOL\["Server-Side Memory Across Sessions"]

&#x20;   STABLEPREFIX\["Stable Prefix for Cache Hits"]

&#x20;   TOOLBUDGET\["Tool and MCP Definition Overhead"]

&#x20;   GREPFIRST\["Exact-String Retrieval Before Embedding Retrieval"]

&#x20;   SMALLESTSET --> CONTEXTROT --> REWORK

&#x20;   REWORK --> PROGDISC --> HEADERONLY --> AGENTSMD --> NODUPEDOC

&#x20;   NODUPEDOC --> SUBAGENT --> COMPACT --> OBSCOMPRESS --> MEMTOOL

&#x20;   MEMTOOL --> STABLEPREFIX --> TOOLBUDGET --> GREPFIRST

&#x20; end



&#x20; subgraph P8\["P8 · STANDING TENSIONS"]

&#x20;   direction TB

&#x20;   OUSTERHOUTC\["Comments Capture What Code Cannot — John Ousterhout"]

&#x20;   NAURTHEORY\["Programming as Theory Building — Peter Naur"]

&#x20;   TACIT\["Tacit Knowledge Resists Specification"]

&#x20;   HYRUM\["Hyrum's Law — Hyrum Wright"]

&#x20;   REGEVIDENCE\["Regulated Environments Need an Evidence Trail"]

&#x20;   MAINTCOST\["Measured Maintenance Cost of Agent Code"]

&#x20;   SPECDRIFT\["Silent Spec-Code Drift — Grabowski"]

&#x20;   CTXEXPLODE\["Context Explosion in Whole-Repo Reasoning — Grabowski"]

&#x20;   OUSTERHOUTC --> NAURTHEORY --> TACIT

&#x20;   HYRUM --> REGEVIDENCE --> MAINTCOST

&#x20;   SPECDRIFT --> CTXEXPLODE

&#x20; end



&#x20; %% ===== SPINE =====

&#x20; G\_START --> JTBD

&#x20; LIVEPLAN --> G\_CONTRACT --> UBIQ

&#x20; ACCEPTPORT --> TOTALITY

&#x20; KISS --> G\_INDEP --> DIJKSTRATEST

&#x20; SANITIZE --> G\_NET --> NODELETE

&#x20; DIFFBUDGET --> CONVCOM

&#x20; ADRN --> G\_DONE

&#x20; SMALLESTSET -.-> G\_START



&#x20; %% ===== CROSS-PHASE =====

&#x20; KOLMOGOROV --> PARNAS

&#x20; DBC --> INDEPVER

&#x20; ILLEGAL --> HUGHES

&#x20; ACCEPTPORT --> CONTRACTTEST

&#x20; WHYNOTWHAT --> BLAME

&#x20; MAINTCOST --> DELETIONGATE

&#x20; PROGDISC --> AGENTQA



&#x20; %% ===== BACKREFERENCES =====

&#x20; XYPROB -.->|"the stated problem is not the real one"| JTBD

&#x20; EARS -.->|"the requirement is not falsifiable"| DBC

&#x20; INVEST -.->|"the task depends on another task"| THINSLICE

&#x20; THINSLICE -.->|"the slice cuts across a module boundary"| PARNAS

&#x20; SPIKE -.->|"the unknown survived the spike"| LIVEPLAN

&#x20; YAGNI -.->|"generality has one caller"| TARPIT

&#x20; LIVEPLAN -.->|"the plan outlived its task"| G\_START

&#x20; G\_CONTRACT -.->|"a second durable description appeared"| SPECDRIFT

&#x20; UBIQ -.->|"the domain term is absent from the type"| ILLEGAL

&#x20; CLEANNAME -.->|"the name cannot carry the meaning"| UBIQ

&#x20; COMMENTSMELL -.->|"prose was needed to explain the code"| CLEANNAME

&#x20; MILNER -.->|"a stuck state is reachable"| ILLEGAL

&#x20; ILLEGAL -.->|"the type cannot express the rule"| DBC

&#x20; PARSEDV -.->|"validation repeats in the interior"| ILLEGAL

&#x20; WADLER -.->|"the signature permits what the contract forbids"| MILNER

&#x20; DBC -.->|"the contract lives in prose, not in the signature"| WADLER

&#x20; CQS -.->|"a query mutated state"| DBC

&#x20; PARNAS -.->|"a decision is not hidden by any module"| DEEPMOD

&#x20; DEEPMOD -.->|"the interface needs prose to be usable"| OUSTERHOUTC

&#x20; ACCEPTPORT -.->|"an adapter leaked into the core"| PARNAS

&#x20; TOTALITY -.->|"a partial function escaped its domain"| PARSEDV

&#x20; GUARD -.->|"the branch structure still needs explanation"| SLAP

&#x20; SLAP -.->|"the function mixes abstraction levels"| DEEPMOD

&#x20; STRUCTPROG -.->|"control flow is untraceable"| GUARD

&#x20; IMMUT -.->|"shared mutable state crossed a boundary"| OWNERSHIP

&#x20; OWNERSHIP -.->|"a borrow outlived its owner"| IMMUT

&#x20; DRY -.->|"one fact has two representations"| KOLMOGOROV

&#x20; KISS -.->|"the solution exceeds the problem"| YAGNI

&#x20; G\_INDEP -.->|"the verifier read the implementation"| INDEPVER

&#x20; DIJKSTRATEST -.->|"green does not mean correct"| INVARIANTRUN

&#x20; ORACLEBIAS -.->|"the assertion mirrors the code"| G\_INDEP

&#x20; INDEPVER -.->|"the two agents shared context"| ADVERSARIAL

&#x20; ADVERSARIAL -.->|"the verifier adopted the implementer's assumptions"| ORACLEBIAS

&#x20; HUGHES -.->|"the property is falsified"| ILLEGAL

&#x20; PBTAGENT -.->|"the proposed property restates the code"| METAMORPH

&#x20; INVARIANTRUN -.->|"the invariant broke under a call sequence"| DBC

&#x20; METAMORPH -.->|"no oracle exists for the direct output"| LLMJUDGE

&#x20; FUZZ -.->|"the input crashed the parser"| PARSEDV

&#x20; CONTRACTTEST -.->|"a consumer broke on an unpromised behaviour"| HYRUM

&#x20; CHARTEST -.->|"current behaviour is the only description left"| SPECDRIFT

&#x20; LLMJUDGE -.->|"judge and author are the same model"| INDEPVER

&#x20; AGENTQA -.->|"verification needs a human dashboard"| SANITIZE

&#x20; SANITIZE -.->|"a sanitizer or analyser reports"| TOTALITY

&#x20; CONVCOM -.->|"the message says what, not why"| WHYNOTWHAT

&#x20; RULE5072 -.->|"the subject does not stand alone"| CONVCOM

&#x20; WHYNOTWHAT -.->|"the reason is unrecoverable from history"| ADRN

&#x20; GITSTATE -.->|"state exists outside the repository"| LIVEPLAN

&#x20; BLAME -.->|"the introducing commit explains nothing"| RULE5072

&#x20; BISECT -.->|"no commit isolates the change"| LIVEPLAN

&#x20; SEMVER -.->|"a promise broke without a major bump"| CONTRACTTEST

&#x20; ADRN -.->|"a reversible decision was recorded"| YAGNI

&#x20; G\_NET -.->|"the artifact grew"| DIFFBUDGET

&#x20; NODELETE -.->|"the old path survives beside the new"| DELETIONGATE

&#x20; GUARDANDGO -.->|"a fallback was added, not removed"| DELETIONGATE

&#x20; TYPE4 -.->|"two functions mean the same thing"| DRY

&#x20; CHURN -.->|"the diff is net-positive again"| G\_NET

&#x20; SLOPDRIFT -.->|"behaviour drifted across iterations"| INVARIANTRUN

&#x20; DELETIONGATE -.->|"superseded code is still reachable"| REACHABLE

&#x20; REACHABLE -.->|"an entry point has no caller"| DIFFBUDGET

&#x20; TARPIT -.->|"the state is accidental"| ILLEGAL

&#x20; LEANSW -.->|"size grew without a reason"| KOLMOGOROV

&#x20; KOLMOGOROV -.->|"the description exceeds the content"| DEEPMOD

&#x20; SMALLESTSET -.->|"context grew without new signal"| COMPACT

&#x20; CONTEXTROT -.->|"quality fell as the window filled"| SUBAGENT

&#x20; REWORK -.->|"iteration, not generation, spent the budget"| G\_INDEP

&#x20; PROGDISC -.->|"the body loaded when it was not needed"| HEADERONLY

&#x20; HEADERONLY -.->|"the header does not predict the trigger"| AGENTSMD

&#x20; AGENTSMD -.->|"the file restates the README"| NODUPEDOC

&#x20; NODUPEDOC -.->|"two documents describe one fact"| DRY

&#x20; SUBAGENT -.->|"the subagent returned raw output"| OBSCOMPRESS

&#x20; COMPACT -.->|"compaction cut an active subgoal"| OBSCOMPRESS

&#x20; OBSCOMPRESS -.->|"an exact string was paraphrased away"| GREPFIRST

&#x20; MEMTOOL -.->|"history is replayed each session"| COMPACT

&#x20; STABLEPREFIX -.->|"the cache is missing"| TOOLBUDGET

&#x20; TOOLBUDGET -.->|"tool definitions dominate the prompt"| PROGDISC

&#x20; GREPFIRST -.->|"retrieval returned approximate matches"| SMALLESTSET

&#x20; OUSTERHOUTC -.->|"the knowledge has no home in the code"| WHYNOTWHAT

&#x20; NAURTHEORY -.->|"the theory died with the session"| MEMTOOL

&#x20; TACIT -.->|"the constraint was never stated anywhere"| ADRN

&#x20; HYRUM -.->|"an unpromised behaviour became a contract"| CONTRACTTEST

&#x20; REGEVIDENCE -.->|"the audit needs an artifact git does not hold"| ADRN

&#x20; MAINTCOST -.->|"merged code costs more than it saved"| G\_NET

&#x20; SPECDRIFT -.->|"two descriptions disagree"| G\_CONTRACT

&#x20; CTXEXPLODE -.->|"the agent must read the whole repository"| PROGDISC

&#x20; G\_DONE -.->|"the contract is not satisfied"| G\_INDEP



&#x20; classDef gate stroke-width:3px

&#x20; classDef tension stroke-dasharray:5 3

&#x20; class G\_START,G\_CONTRACT,G\_INDEP,G\_NET,G\_DONE gate

&#x20; class OUSTERHOUTC,NAURTHEORY,TACIT,HYRUM,REGEVIDENCE,MAINTCOST,SPECDRIFT,CTXEXPLODE tension

```



\## Context economy, by measured effect



1\. \*\*Cut iteration, not output.\*\* Review-and-rework outweighs initial generation in token spend. An independent verifier working from the contract is the largest single saving available.

2\. \*\*Progressive disclosure.\*\* Header at session start, body on trigger.

3\. \*\*Subagent isolation.\*\* Repo reads, search and logs return compressed; the main thread keeps depth.

4\. \*\*Compact at phase boundaries.\*\* Reactive compaction fires too late, periodic compaction cuts mid-subgoal.

5\. \*\*Grep before embeddings.\*\* Error strings, paths and test names survive verbatim or not at all.

6\. \*\*Stable prefix.\*\* Invariant content first, variable content last.

7\. \*\*Reference, never restate.\*\* A duplicated description is paid for on every task.

