# Midnight Oil in Claude Code

The shared skill is available as `/midnight-oil`, and its description permits automatic selection for natural-language overnight requests. Personal skills live under `~/.claude/skills/`; a symlink to the shared skill directory keeps both hosts in sync. This local installation applies to Claude Code on this machine. Cowork and cloud sessions require a separate account-enabled skill or supported repository installation.

## Continuation

Prefer Claude Code's native `/goal` for work that should continue until acceptance criteria hold. Include the agreed deadline or turn limit in its condition when supplied. These clauses are model-evaluated stopping conditions, not enforced spend caps. A goal has its own evaluation cost and does not change permission settings.

Only claim a goal is active after the host confirms it. If the current agent cannot activate `/goal`, use available session scheduling tools for the requested continuation, or provide the user one concrete `/goal <condition>` command. Printing a slash command does not execute it. Do not launch a separate Claude process merely to simulate continuing this conversation.

For CI/deployment follow-up or bounded continuation, use the available `CronList`, `CronCreate`, and `CronDelete` tools. Use a prompt scoped to the agreed task, with its deadline and stopping conditions, and cancel schedules owned by this run when finished or stopped. Avoid a bare `/loop` default that could continue into unrelated cleanup after the spec is satisfied. Use a background monitor when available to receive build/deployment completion without repeated model polling.

Session scheduling requires a running session; a supported background session can continue without an open terminal, but still needs the machine running. Do not create a cloud task just because a local session cannot stay open: verify the skill, source, and tools are available there first. Preserve the user's permission settings; resolve concrete missing command permissions during preparation instead of enabling permission bypass.

## Usage

Claude subscription allowance is separate from Codex allowance. Use Claude's supported usage tools or `/usage` for plan limits and reset information; do not use Codex account readings as Claude's budget. When those readings are unavailable to the agent, say so and use the user's agreed bounded run policy.

The `claude --max-budget-usd` flag bounds API-call spending in non-interactive `--print` runs. It does not enforce a percentage reserve of a Claude Pro/Max allowance. Do not introduce API billing or start another session to obtain this control without the user's request. Honor explicitly fixed model constraints and use supported per-task model selection for the stronger diagnostic review required by the shared skill. Do not change global model settings; choose per-run effort only through available host controls, and do not assume Codex speed settings map to Claude.

References: [skills](https://code.claude.com/docs/en/skills), [goals](https://code.claude.com/docs/en/goal), [scheduling](https://code.claude.com/docs/en/scheduled-tasks), [usage](https://code.claude.com/docs/en/costs).
