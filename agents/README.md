---
name: dev-team
description: Runs the 4-agent dev pipeline (dev-planner → dev-coder → dev-tester → dev-reviewer) to ship a feature or site from a rough idea. Use whenever the user says "dev team", "run the pipeline", "build this feature properly", or gives a feature/site idea and wants it planned, built, tested, and reviewed end to end.
---

# Dev-Team Pipeline

## Contract
All handoffs happen through the pipeline/ folder in the project root: spec.md, questions.md, build-notes.md, test-report.md, review-verdict.md. Create pipeline/ if missing and add "pipeline/" to .gitignore. Delete stale pipeline files from previous runs before starting.

## Flow
1. **Plan.** Invoke the dev-planner subagent with the user's idea. Website ideas → dev-planner must apply the website-stack skill.
2. **HUMAN GATE — mandatory.** Show the user pipeline/spec.md (or a faithful summary including ASSUMPTIONS and OUT OF SCOPE). Wait for explicit approval or edits. Never proceed without it.
3. **Build.** Invoke the dev-coder subagent. If it produces pipeline/questions.md, surface the questions to the user and re-run after answers.
4. **Test.** Invoke the dev-tester subagent.
5. **Review.** Invoke the dev-reviewer subagent.
6. **Verdict handling.**
   - APPROVED → report to the user: what was built, test summary, top risks from the review.
   - REJECTED → send the numbered reasons back to dev-coder (step 3), then re-test, then re-review. Maximum 2 rejection loops. After the 2nd rejection: HALT and write pipeline/failure-report.md summarizing what failed, why, and what human decision is needed. Never silently retry past the cap.

## Rules
- Never let one agent do another's job. The orchestrator routes; agents execute.
- Always use the dev-prefixed agents (dev-planner, dev-coder, dev-tester, dev-reviewer) — never the standalone coder.md agent or any other agent in the agents folder.
- Never skip the human gate at step 2, even if the user said "just build it" earlier in the session.
- Model gating is set in the agent files (opus for dev-planner/dev-reviewer, sonnet for dev-coder/dev-tester) — do not override it.
