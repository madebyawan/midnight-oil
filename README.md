<p align="center"><img src="icon.svg" width="112" alt="Midnight Oil icon"></p>

# Midnight Oil

Leave a spec. Wake up to a reviewable result.

Midnight Oil is an open-source overnight workflow skill for Codex and Claude Code. Prepare a task, define what done means, agree on a budget, and let your agent work through implementation, verification, and repairs. The morning handoff includes the requested PR or prototype, checks performed, and anything still unfinished.

This is a skill, not a standalone agent runner. Continuation, tools, credentials, and enforced limits come from the host running it. Completion depends on the task, available budget, and external dependencies.

## Install

Install it once for both agents across your local projects:

```sh
npx skills add madebyawan/midnight-oil --skill midnight-oil --global --agent codex --agent claude-code
```

For a project installation that teammates can use, run the same command from that project without `--global`. Review and commit the generated skill files and links.

The existing [skills CLI](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) handles installation and agent-specific paths. Midnight Oil does not require a separate installer, API key, or paid API fallback. Your agent still needs its usual authentication.

## Use

After agreeing on a task in the current conversation, say:

> Run this overnight while I sleep. Keep going until the acceptance checks pass, open a PR, and deploy the prototype to the preview destination we agreed on. Finish by 07:00 and leave a morning handoff.

Or prepare before launching:

> Prepare this for tonight. Help me define the acceptance checks and a usage budget first.

The skill description enables automatic selection. Selection is model-driven, so explicit invocation is also available:

- Codex: `$midnight-oil`
- Claude Code: `/midnight-oil`

A direct overnight request starts preparation and the authorized work. A tentative suggestion prompts an offer. A request to prepare does not launch unattended work. If the referenced task or an important budget constraint is missing, the agent asks for it.

## What the workflow does

- Reuses the current spec, conversation, and project instructions, including hosting rules.
- Defines observable acceptance checks and checkpoints progress.
- Uses supported Goals or scheduling to continue across turns.
- Implements, verifies, inspects, and repairs until the agreed stopping condition.
- Defaults to one active worker; additional agents require authorization.
- Produces requested PRs and prototypes and reports verified results.
- Preserves partial work when a budget, deadline, or persistent blocker ends the run.

It does not merge a PR, deploy to production, or expand the assignment merely because it runs overnight. Those actions need authorization within the task.

## Usage and runtime limits

Slowing down requests alone does not reduce their total usage. The workflow avoids repeated scans, unnecessary checks, and frequent model-driven polling. It uses economical per-run controls where supported and preserves explicit model choices.

An account reserve checked between milestones is best effort. It is not a hard spending cap: other sessions share the account, usage readings may be unavailable, and in-flight work can cross a threshold. Use runtime-enforced controls where an exact cap is required. A token budget or API dollar cap is not an exact percentage of subscription allowance.

Codex and Claude have separate usage allowances. Local runs require the machine and relevant session or app to remain running. Personal skill installation does not automatically make the skill available to hosted cloud sessions or Claude Cowork.

Claude-specific setup details are in [the Claude Code reference](skills/midnight-oil/references/claude-code.md). Host capabilities and account availability may change; the skill checks the available controls rather than assuming them.

## Contributing

Keep the shared workflow portable and put host-specific behavior in focused references. Preserve natural-language activation, preparation-only intent, project instructions, and honest reporting of incomplete work. Include realistic examples with changes to triggering or continuation behavior.

The skill lives in `skills/midnight-oil/`. Changes there apply to both agents when their installations link to the same checkout.

To try an unpublished change, use this checkout's absolute path instead of `madebyawan/midnight-oil` in the installation command.

## License

[MIT](LICENSE). Made by Awan.
