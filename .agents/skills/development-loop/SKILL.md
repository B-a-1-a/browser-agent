---
name: development-loop
description: Understand existing code, make focused changes, and verify behavior for Browser Agent features, bug fixes, and refactors. Use during implementation and development handoffs, with effort proportional to the change.
---

# Development Loop

Help the contributor deliver a change they understand and can explain, with evidence that the affected behavior works. Adapt the depth to the task. A small fix needs less process than a shared-contract or permission change.

## Establish the task and context

Read the repository's [AGENTS.md](../../../AGENTS.md) and any nearer instructions. Follow [CONTRIBUTING.md](../../../CONTRIBUTING.md#claiming-and-coordinating-work) for ownership and dependency checks. GitHub issues hold shared assignments and progress. Personal agent memory is not team approval or an assignment record.

For an issue-based task, read its outcome, scope exclusions, acceptance criteria, and dependencies. Respect Bala's Step One gate. Do not take over another contributor's work. Posting comments, assigning issues, opening PRs, and merging require the user's authorization for those actions.

Read the files to change, related contracts and tests, and an existing example of the same pattern. Trace the relevant caller and consumer when crossing a boundary. Use only the relevant [PRD](../../../docs/product/PRD.md) sections. Do not infer behavior from a filename or an agent's previous summary alone.

State the intended outcome and likely approach briefly. Resolve routine details from existing patterns. Ask when a missing decision changes behavior, scope, ownership, or compatibility. Continue independent work when possible.

## Make a focused change

Reuse the existing services and adapters. Keep changes within the issue's ownership boundary and preserve unrelated edits. Coordinate shared contracts before changing dependent implementations.

Choose a reviewable increment that leaves a coherent path through the affected code. Avoid unrelated cleanup and speculative abstractions. Contributors choose their planning format, tools, and commit cadence. No extra plan document, line-count limit, or automatic commit is required by this skill.

## Verify the affected behavior

Choose checks that can reveal a real failure:

- For a logic, state, data, or protocol bug, reproduce the failure with a focused regression test as required by AGENTS.md. Then demonstrate that the fix passes.
- For new behavior, extend the relevant behavior tests, including important error or boundary cases. Do not add tests that only repeat the implementation.
- For UI behavior, check the actual interaction when authorized. For visual-only changes, use before/after captures rather than implementation-mirroring tests.
- For shared contracts or migrations, check affected consumers, compatibility, and recovery paths. For permissions or external actions, include denial and stale-state cases.
- For documentation-only changes, check examples, commands, links, and the skill format where relevant. Application tests are unnecessary unless behavior also changes.

Use repository commands and the smallest relevant test set. Examples include `vp test run <test-files>` during implementation and `vp run check:changed <baseline-ref>` before pushing. Select a real comparison base for the change. Let CI own repo-wide suites unless the user requests them.

Investigate a failure before retrying or expanding checks. Do not weaken tests to get a pass. If tools, credentials, or platform access prevent a check, record what remains unverified. Never report an unrun check as passing.

## Review and hand off

Inspect the final diff for scope, regressions, accidental secrets, and unrelated edits. Compare the result with the acceptance criteria. Explain anything the evidence does not establish.

Summarize what changed and why, the checks actually run and their results, and remaining limitations or follow-up. When authorized to update GitHub, put the evidence and current status on the issue or linked PR. An implementation awaiting review is not a completed issue.
