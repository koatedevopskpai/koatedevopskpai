# Developing this portfolio with multiple coding agents

How the public repositories in this account are actually built, reviewed and
merged — with the defects that the process caught.

## The problem

I run more than one coding agent against these repositories: Codex, Claude Code and
OpenCode. Three writers on shared repositories fails in two ways, and the second is
the dangerous one:

1. **Mechanical collisions.** Two agents in one repository produce merge conflicts
   on generated files, duplicated work, and contradictory README wording.
2. **Confident results that mean nothing.** An agent reports "done, tests pass"
   and the claim quietly exceeds the evidence. This is worse than a failed build,
   because a red build is honest and a false green is not.

Everything below exists to make the second failure impossible to hide.

## The controls

| Control | Rule |
|---|---|
| **Ownership** | One agent owns a repository at a time. A task may move a repository between agents, never share it |
| **Isolation** | One branch and one git worktree per task, named `task/<ID>-<slug>`. Nothing is developed on `main` |
| **Handover format** | Every task returns a fixed status line: task, repository, branch, commit, the exact command run, evidence, ran versus skipped, claims affected, remaining limitations, spend |
| **Review gate** | A second agent verifies by **running the stated command**, not by reading the diff. Nothing merges on the author's word |
| **Evidence standard** | Every artefact names the command, the commit and the limitation. A skipped check is reported as skipped, never as passed |
| **No suppressions** | No added `skip`, `xfail`, `type: ignore`, `noqa` or coverage pragma to reach green. If something cannot pass, it is reported as blocked |
| **Fail closed** | Missing input raises before doing anything expensive. Unanswerable cases are scored as failures, never skipped |
| **Environment parity** | CI is Linux and is the authority. Behaviour involving subprocesses, signals, permissions or memory is reproduced there before handover |
| **Claim discipline** | A planned feature is never described as an existing result. Removing an unsupported claim is a deliverable |
| **Budget** | Per-task spend stated before a paid run, cheap models by default, and cloud resources deleted in the same session with the teardown command recorded |

## What the process caught

These are not hypotheticals. Each was found by the review gate, most of them after
an author had reported success.

| # | Defect | How it surfaced |
|---|---|---|
| 1 | The evaluation harness scored the **reference answer** instead of generated output, so a perfect score was guaranteed regardless of what the application produced | Source review, then fixed and proven: a wrong answer now fails against a real judge, where it had scored 1.000 |
| 2 | The live graph query returned a node **once per path length** (`UNION` of seeds and paths), so sorted results contained duplicates | A parity harness against a real Neo4j: 10/15 probes, then 15/15 after the fix |
| 3 | The same query shape **silently ignored a relationship filter**: `[LINKS*0..2]` is a variable named LINKS, not a type filter. The colon is required | A benchmark whose measured row count disagreed with its intent |
| 4 | A **memory-limit test passed by luck**: the submission finished in ~65 ms while the watchdog sampled every 50 ms | Same commit passed in a container and failed on the runner — the signature of a race |
| 5 | A **silently ignored `top_k`** parameter: the SDK had renamed `k` to `k_nearest_neighbors`, so the value was discarded with only a warning | Static review against the pinned SDK version |
| 6 | **Generated artifacts were committed**, so every pair of branches from the same base conflicted on `pytest.xml` and `test-output.txt` | A real add/add conflict during a merge, fixed at source by untracking them |
| 7 | Two tasks silently **collided on an ADR number**, and CI failed only because the merge was reviewed | A rebase conflict requiring a human decision, not a mechanical one |

A recurring pattern: in four of seven cases the thing that found the bug was a
**measurement disagreeing with the intent**. The code looked right; the number
said otherwise.

## Why this is relevant to prompt and workflow engineering

The same discipline applies to a prompt or an agent workflow:

- **Version it.** Two variants, run on the same cases, or there is no comparison.
- **Measure it.** Quality, failures, latency and cost — not a vibe.
- **Define the failure boundary.** State what happens when the model returns
  nothing, returns the wrong shape, and is asked for something it cannot do.
- **Publish the limits with the result.** Sample size included.
- **Never claim a green result you cannot reproduce from a command.**

A prompt change that "feels better" is the same class of claim as a test that
passes by luck.

## What this does not establish

- This documents a workflow **I designed and operated** on my own reference builds.
  It is not a commercial deployment or a team process.
- "Defects caught" is not a productivity metric, and I am not claiming one. The
  relevant claim is narrower: the review gate found real defects that had been
  reported as complete.
- The agents' failures are informative, not embarrassing: an agent cannot be blamed
  for a race condition it cannot observe. The process exists because that happens.
- No cost or time comparison against working solo is made here, because I have not
  measured one.

Related: [EVIDENCE.md](https://github.com/koatedevopskpai/enterprise-rag-pipeline/blob/main/EVIDENCE.md)
in the retrieval project is the per-project version of the same idea.
