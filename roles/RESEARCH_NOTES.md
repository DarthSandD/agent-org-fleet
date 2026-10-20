# Research Notes: Engineering Role Patterns for Agent SOUL Files

Purpose: patterns only, in original wording, to shape worker roles. No source text copied.

## (a) Level ladder pattern

- Associate / Engineer I-II: guided work on a single component, learns codebase and craft, needs regular review.
- Mid / Engineer: owns whole features end to end in a familiar service, self-directed on known work, escalates the unfamiliar.
- Senior: owns ambiguous problems across several systems, defines how work is done, leads design reviews, mentors others.
- Staff: works across teams, sets direction for a domain, raises standards for many engineers at once.
- Principal: org-wide scope, defines what and why, owns the hardest trade-offs and multi-year architecture bets.
- Distinguished / Fellow: company or industry scope, shapes long-term roadmap and external reputation. Rare by design.
- Specialist tracks run parallel to this ladder, not below it: security, data, platform, QA, and domain experts can advance to Staff or Principal depth without becoming managers. A separate management track mirrors IC scope at each band.

Sources: https://networkinterview.com/nvidia-designation-hierarchy-explained/ and https://www.awana.io/job-leveling-matrix

## (b) Transferable patterns

1. Level by scope and autonomy, not tenure: promotion signal is how much ambiguity a person absorbs without help. Source: https://www.awana.io/job-leveling-matrix
2. Description as routing key: a role file needs a precise one-line specialty so an orchestrator can delegate correctly; vague labels route badly. Source: https://dev.to/proflead/github-copilot-ai-agents-the-complete-technical-deep-dive-m86
3. Least-privilege tool boundary: give each role only the tools its scope needs; capability limits are part of the role definition. Source: https://dev.to/proflead/github-copilot-ai-agents-the-complete-technical-deep-dive-m86
4. Behavior contract, not vibe: state scope, process, and required output format explicitly so behavior is testable. Source: https://dev.to/dowhatmatters/escalation-rules-for-agents-ask-vs-refuse-vs-unknown-scope-is-a-contract-not-a-vibe-4gj6
5. Surgical change discipline: smallest change that solves the assigned problem, ignore unrelated faults, validate early with existing tests and linters. Source: https://gist.github.com/CypherpunkSamurai/a0c732ea5042e9fd72d8c6a1a9a30625
6. Delegate to specialists first: a lead scans for a matching specialist before using general tools, passes full context, and only falls back if the specialist result is inadequate. Source: https://gist.github.com/CypherpunkSamurai/a0c732ea5042e9fd72d8c6a1a9a30625
7. Evidence over claims: check the artifact itself, label verified fact versus inference, and report what was not verified. Source: ~/workspace/soul-forge-full/SUBAGENT_SOUL.md
8. Plan gates before building: analysis, planning, approval, implementation, verification, with input, output, verify criteria and rollback per task. Source: ~/workspace/soul-forge-full/SOUL_FULL_V2.md
9. Shared protocols plus thin identity: keep common safety, comms, and escalation rules in one shared layer; keep each role file to its distinct identity and tools. Source: https://dev.to/miso_clawpod/how-to-manage-prompts-across-10-ai-agents-a-complete-guide-5304
10. Multiplier effect at senior levels: higher roles are judged on raising other engineers output, not only personal output. Source: https://briankung.dev/2023/07/27/staff-engineer-by-will-larson/

## (c) Principal vs Senior vs Mid

- Mid: reliable delivery. Scope is a feature. Autonomy is self-direction on familiar ground. Success is correct, tested work shipped on time.
- Senior: reliable direction inside a team. Scope is a project or subsystem. Autonomy includes choosing the approach under ambiguity, spotting priority problems, and mentoring. Success includes design quality and unblocking peers.
- Principal: reliable direction across an org. Scope is multiple teams and long horizons. Autonomy includes choosing which problems matter, making contested architecture calls, and writing the framing doc before others see the need. Success is system health, avoided risk, and teams shipping better because of shared direction, not personal code volume.

Sources: https://dev.to/pixari/what-is-a-staff-engineer-or-principal-engineer-and-how-do-you-get-there-5475 and https://networkinterview.com/nvidia-designation-hierarchy-explained/

## (d) Review and escalation patterns

- Layered review: self-check with tests and linters first, then peer or code review, then a security scan before finalizing; fix and re-run after each layer. Source: https://gist.github.com/CypherpunkSamurai/a0c732ea5042e9fd72d8c6a1a9a30625
- Conditional reviewers: add a test reviewer for code changes and a security reviewer for auth, infra, or data handling; severity gates block merge for critical and high findings. Source: ~/workspace/soul-forge-full/SOUL_FULL_V2.md
- One complete review pass: give all feedback in one round, avoid drip-feed comments across rounds. Source: ~/workspace/soul-forge-full/SOUL_FULL_V2.md
- Escalation router with four outcomes: ask when the user can unblock with missing info, refuse when unsafe or unauthorized, return unknown when out of scope or low confidence, otherwise proceed. Keep the decision structured and logged. Source: https://dev.to/dowhatmatters/escalation-rules-for-agents-ask-vs-refuse-vs-unknown-scope-is-a-contract-not-a-vibe-4gj6
- Bounded autonomy: act alone on reversible, low-risk, in-scope work; require explicit authorization for destructive, external, financial, or credential actions; if unsure, surface it in the report instead of acting. Source: ~/workspace/soul-forge-full/SUBAGENT_SOUL.md
- Stall handling: on failure or stall, reassign or escalate with context and a recommendation; do not retry the same method indefinitely. Source: ~/workspace/soul-forge-full/SOUL_FULL_V2.md
