# Usage: Spawning Workers From the Fleet

For Muse operators: the main agent who coordinates work and spawns
short-lived subagents. This assumes your runtime can spawn subagents with a
custom instruction message, and that you keep a base SOUL.md for all workers.

## The spawn pattern

1. **Read the index.** Open `roles/ORG_INDEX.md`. Use the task-to-role lookup
   table first. If the task is not in the table, walk the org tree and pick
   the role whose mission matches.
2. **Pick one role per worker.** One worker, one role file. A worker spawned
   as Senior Backend Engineer should not also be doing the QA pass. Splitting
   build and verify into separate spawns is deliberate: nobody reviews their
   own work.
3. **Attach two documents in the spawn message.** The base SOUL.md (your
   shared rules for every worker) and the one role file. The role file points
   back to the base soul on its "Pairs with" line, so the worker knows both
   apply.
4. **Tell the worker to load its matched skills.** The role file lists exact
   skill paths. Have the worker read those SKILL.md files before it starts,
   not halfway through.
5. **Scope the task tightly.** State the outcome, the constraints, the
   deliverable, and what counts as done. The role supplies the judgment, you
   supply the job.
6. **Honor the escalation ladder.** If a worker hits something outside its
   authority (a cross-module change, a contract break, a push), it escalates
   to its reports-to role. As operator, you either answer it yourself,
   standing in for that level, or spawn the senior role to decide.
7. **Require the report format.** Every worker reports back in four parts:
   RESULT / VERIFIED / RISKS / REMAINING. No report in that shape, no merge.
8. **Verify before you merge.** Read the evidence in VERIFIED, not just the
   claim in RESULT. If the worker says a check could not be proven in its
   sandbox, believe it and run that check yourself or say so to the user.

## Staffing defaults that work well

- Whole build: a Senior of the matching function builds, a QA role verifies
  in a separate spawn.
- Small fix: one Engineer or Associate builds, QA still verifies separately.
- Cross-function work or a hard blocker: add the leadership role above the
  workers (Director, Principal, or VP level) to make the call.
- Run independent parts in parallel: spawn the frontend, backend, and docs
  workers at the same time, then merge as coordinator.

## Example spawn message

```text
You are the Senior Frontend Engineer. Your role file is attached below,
along with the base SOUL.md. Both apply.

[base SOUL.md content]

[roles/Senior_Frontend_Engineer.md content]

Before you start, read every skill listed under Matched skills in your
role file.

Task: Rebuild the settings page so the save flow works on mobile.
Outcome: settings save and persist after reload, on a 390px wide screen.
Constraints: surgical changes only, no new dependencies, no push.
Deliverable: the edited files in the workspace, with paths.
Acceptance: you ran the build, you checked the page at mobile width,
and your report shows the exact steps you verified.

House rules from your role file apply: pause before any GitHub push,
no credentials, no real money, no irreversible deletes.
Escalate to Staff Frontend Engineer (through me) if the fix needs
changes outside the settings module.

Report back as: RESULT / VERIFIED / RISKS / REMAINING.
```

## Notes

- Role files reference skill paths from the Darren Labs setup. If a path
  does not exist in your setup, swap in your own equivalent skill or drop
  that line. The shape matters more than the exact paths.
- Keep the fleet files where your operator can read them at spawn time.
  A role file the operator cannot find is a role you do not have.
- When a role turns out wrong for the work you actually do, edit the role
  file, not just the next spawn message. The fleet is the memory.
