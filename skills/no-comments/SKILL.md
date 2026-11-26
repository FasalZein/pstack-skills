---
name: no-comments
description: "Spawn Comment Sicko, fix accepted findings, and offer encodings for claimed constraints."
disable-model-invocation: true
---

# No comments

Spawn Comment Sicko. Act on accepted findings.

Defer to Comment Sicko's fresh perspective.

## Scope

Use the caller's files or diff. Otherwise use the current diff against the base branch, default `main`, including the working tree.

## Steps

1. Launch one child with the `subagent` tool. In a brownfield project (code that existed before this work), launch `scout`. In a new project, launch `worker`. The child sees only its task, so the task holds the scope, the mode, and the absolute paths of [references/comment-sicko.md](references/comment-sicko.md) and the [why](../why/SKILL.md) skill. It tells the child to read Comment Sicko and act as Comment Sicko. Scout mode: edit no file, and report `file:line` and the text of each comment to delete, each `MUST KILL` flag, and the skips. Worker mode: delete the comments, edit no other code, and report the touched files, the deletion count, each `MUST KILL` flag, and the skips. With `scout`, apply the accepted deletions yourself after this step's review. The agent file owns the model. Do not restate Comment Sicko's rules.
2. Inspect its report and diff. Reject application-code edits, scope escapes, exception-protected deletions, misstated `MUST KILL` reasons, and flags that treat kept intentional code as guilty. Reshape flags on our-code surprises stay actionable. Do not restore those comments. A keep survives only with proof it is about something we cannot change. Audit missed scoped lint and TypeScript suppressions. Correctness or safety suppressions stay actionable `MUST KILL`s. Restore deletions only with exact exceptions and scoped proof. Before accepting thin `IMPORTANT` or `do not remove` kills or keeps, trace their symbol or apply the [why](../why/SKILL.md) skill to it. If a kill is ambiguous, do not restore. If a keep is refuted or still ambiguous, delete it. Revert only the child's edits, never the caller's existing diff, and rerun one rejected report with the failure named. Reject a second, report it open, and fail the no-comments run.
3. Fix trivial accepted flags directly by deleting a dead path, dropping a parameter, or using the real API. If any fix needs a shape, design it once for the accepted set and surrounding code. Trace every system the change touches, then sketch two different shapes (types, signatures, module boundaries) and pick the one where each piece of state has one owner, each task has one way to do it, and callers need to know least. Redesign instead of patching if workarounds repeat. For a large or contested design, report it open for the `architect` agent instead of sketching alone. Stop at the sketch. Step 3 shapes. Step 4 implements.
4. Implement the smallest root-cause fix in scope. Remove every named workaround. If the root cause is out of scope, land the smallest in-scope fix and report the rest open. The **principle-fix-root-causes** and **principle-redesign-from-first-principles** skills guide intent only. Neither authorizes widening the fence nor fixing instances outside it. Never bolt on symptom guards.
5. Constraint comments say `do not remove`, `do not change wording`, or `talk to X before changing`. Leave keeps about things we cannot change. Offer the cheapest in-scope type, runtime, test, or CI lint. Wait for interactive approval. Unattended and eval require caller pre-approval. If approved, encode then delete. Otherwise delete, report the constraint open, and sketch out-of-scope work.
6. Report the deletion count, restored comments, reruns, shape sketch, fixes, encoding offers, encodings, unenforced constraints, and other open work.
