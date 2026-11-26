---
name: swarm
description: "Fan out N parallel workers, drain them, and return one report. Use for /swarm, 'swarm this', or parallel coverage, races, gauntlets, and exploration."
disable-model-invocation: true
---

# Swarm

## Start

Open a todolist with one entry per phase before launching anything.

1. Frame
2. Fan out
3. Aggregate
4. Report

## Phase A: Frame

1. State the done predicate and the artifact or report the swarm must return.
2. Choose the shape. Partition into slices, race N workers on identical briefs, or mix both. For a race or mixed shape, declare `first pass`, `rank all`, or `best-of` before spawning.
3. Run this skill in the parent session: scout, worker and reviewer cannot launch children. Launch workers that write as `worker` children and workers that only verify or measure as `scout` children. For slices, the agent file owns the model. For a race, give each arm a different model family from the `allowed-models` list of its agent file (`~/.pi/agent/agents/<agent>.md`), passed as the child's `model`. The entry sets the reasoning level. Never give two arms the same family. When the list has fewer families than arms, launch one arm per family and report the unfilled arms. Name each arm's model up front.
4. Give each worker its own writable output when it writes. When workers verify or measure commits, each brief names the exact SHAs. A measurement brief also names the method (sample count, what one sample is, order). The worker records both in its result.

## Phase B: Fan out

Launch the N workers with the `subagent` tool, each writing worker in its own local git worktree, with the step 3 model. A child has no working-directory parameter, so each writing child's task holds the absolute path of its own worktree and says to edit only inside it. Run at most 3 `worker` children at once (the host limit for children that build or test) and launch the rest in batches as slots free. `scout` children edit no file and launch in batches no wider than the spawn width (16).

When a worker must start from a non-default branch, create its worktree from that branch.

Every brief stands alone. Include the goal, scope, exact slice or race arm, how to verify, and what to report. Reports use `PASS`, `ISSUES`, or `BLOCKED` with evidence. A worker that can prove a defect reports `ISSUES` and lists every issue it can prove, not only the first.

If a worker drops out, proceed with N-1 and note it.

## Phase C: Aggregate

Read the terminal results. Drop a result that does not record the SHAs and method its brief names, and respawn that worker once. After a second miss, record a gap. A gap does not count as a pass. For coverage, every required slice needs a result. For a race, apply the selection rule declared up front. Use first pass, rank all, or best-of. Do not paste raw worker dumps.

## Phase D: Report

Return one consolidated in-chat report with a result table, issue one-liners, gaps or dropouts, and the race rule when used.
