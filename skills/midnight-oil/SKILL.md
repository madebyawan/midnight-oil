---
name: midnight-oil
description: "Prepare and run tasks overnight when the user says 'run this overnight', 'while I sleep', 'keep working until morning', or 'midnight oil'. Use for unattended execution or preparing such a run; exclude ordinary tasks that merely mention night or sleep."
---

# Midnight Oil

Turn an agreed task into bounded overnight work with verified deliverables and a morning handoff. Reuse the current conversation, specification, project instructions, and existing authorization.

## Recognize intent

- A direct instruction such as "run this overnight while I sleep" selects this skill. Briefly announce Midnight Oil and proceed with the known task; do not ask whether to use the skill again.
- A tentative statement such as "maybe we could leave this running tonight" should prompt a short offer to prepare a Midnight Oil run. Continue useful preparation without starting unattended work on a suggestion alone.
- "Prepare this for tonight" means prepare the run, not launch it. A request to create or change this skill is not an instruction to execute an overnight workload.
- Resolve "this" from the current conversation. If the task is missing, ask for it instead of selecting unrelated backlog work.

## Prepare the run

Build a short run brief from existing context: the task/spec, observable acceptance checks, intended deliverables, permitted repository and deployment destination, budget or reserve, and any deadline. Reuse the project's planning/status convention instead of introducing a parallel documentation system. Persist enough state for continuation when the task spans turns.

Ask only for missing information that materially affects scope, correctness, or spend, and bundle critical questions once. Keep completing authorized preparation while awaiting answers. Honor explicit approval gates; otherwise a clear instruction to run overnight is already authorization to execute the agreed task.

Check that the required repository, tools, credentials, and verification commands are available. Resolve routine setup issues before the user leaves when possible. Prepare code, artifacts, and checks before requesting any genuinely missing publication permission.

## Protect usage

- Read current account usage and reset times when a usage tool is available. Missing usage data is unknown, not zero. Track the allowance consumed since the run began, rather than treating current remaining allowance as the run's budget.
- Honor the user's explicit budget, reserve, and deadline. Ask for a missing numeric budget or morning reserve during preparation when preserving limits matters; do not silently turn "be economical" into an invented token allowance.
- A Goal token cap is not an exact account-allowance cap. Account usage can include other chats, and in-flight work can overshoot a threshold. Describe a reserve checked between milestones as best effort unless the runtime provides an enforced control. If the user requires a hard reserve and it cannot be enforced, explain the limitation and resolve it before starting the unattended loop.
- Prefer Standard speed and moderate reasoning for routine work when the host exposes per-run controls; escalate for demonstrated difficulty. Preserve explicitly chosen models and settings. Do not change global configuration or switch to paid API billing to implement this policy. If per-run controls are unavailable, report that the existing settings remain in effect.
- Default to one active worker and task at a time. Use additional agents only when the user or applicable instructions explicitly authorize delegation, and keep their work within the same budget.
- Check usage at meaningful milestones and before expensive follow-up work. Checkpoint and stop dispatching new work when the user budget or reserve is reached. Never buy credits, redeem resets, or enable paid fallback without explicit authorization.
- Delays spread work over time; they do not inherently reduce total usage. Avoid frequent model-driven polling, repeated broad scans, and rerunning checks without a relevant change.

## Continue reliably

Use the host's supported continuation mechanism; the skill itself is not a scheduler or a background service.

In Claude Code, read [references/claude-code.md](references/claude-code.md) before configuring continuation or usage controls. Keep Codex-specific tools and account usage separate from Claude's.

- When the user explicitly requests a persistent Goal or asks to keep working until the spec is complete, use Goal tools if available. Preserve an existing compatible Goal. Supply a token budget only when the user explicitly requested that token budget.
- Use a scheduled follow-up in the current chat for requested later work or CI/deployment follow-through that needs another turn. Inspect existing schedules first, preserve context, and avoid duplicate schedules or a new task for every check. A one-night request does not authorize an indefinite nightly automation. End any schedule owned by this run when the work is complete or its stopping condition is reached.
- Do not claim autonomous continuation has been configured unless the Goal or scheduling tool confirms it. If no supported continuation mechanism exists, finish useful authorized work and explain what the host still needs.
- For local execution, ensure the user knows the computer and app must remain running and the workspace available. Check or configure sleep prevention only through supported controls and within the user's request.

Work through the spec in verifiable milestones: implement, run the relevant checks, inspect the result, repair failures, and update the checkpoint. Use an isolated branch/worktree when appropriate. Reuse a suitable checkout and preserve unrelated local work.

Treat acceptance criteria as the finish line. Do not weaken tests, remove requirements, or label simulated behavior as real to obtain a passing result. Repeated attempts should use new evidence or a changed hypothesis; stop a stalled loop with the actual blocker instead of consuming the night on identical retries. Follow the host's Goal lifecycle rules when reporting a blocker or budget exhaustion.

## Deliver and hand off

Produce the agreed outputs within the authorized scope, including a PR and deployed prototype when requested. Honor the project's hosting instructions, verify the deployed URL, and clearly label simulated behavior. Opening a PR does not imply permission to merge it or deploy to production. A failed deployment is incomplete work, even if the build passed.

Leave a concise morning handoff with:

- Completion status against the spec, including unfinished acceptance criteria.
- PR and prototype links, plus the relevant branch/worktree or checkpoint.
- Verification performed and its results.
- Observed usage when available, and why execution stopped.
- Any blocker or decision needed and the next useful action.

If the budget or deadline arrives before completion, preserve the partial result and report it accurately. Mark a Goal complete only after all required outputs and acceptance checks are verified. Do not keep polishing after the agreed spec is satisfied.
