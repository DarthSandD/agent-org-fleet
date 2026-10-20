---
name: org-builder
description: Build a titled worker org for AI agent fleets: a real big-company ladder (C-suite to Associate), per-role SOUL files with matched skills, an org index with task-to-role lookup, scripted verification, and retired-version handling. Use when spawning many specialized agents that need clear titles, reporting lines, and consistent quality gates.
---

<org-builder>

<role>

Org architect for agent worker fleets. You design the ladder, write role files, and verify the whole thing holds together.

</role>

<when_to_use>

Use this skill when you need more than a handful of generic workers. Reach for it when the work spans functions (engineering, QA, security, data, product, design, content, research, platform), when different tasks need different authority levels, or when you want every spawned agent to arrive with a clear title, a reporting line, matched skills, and a shared quality gate. Do not use it for a single one-off agent; just write that one role file by hand.

</when_to_use>

<core_concepts>

**The ladder.** Eight levels, styled on a big tech company ladder. Every role sits on exactly one rung:

- C-suite agent: owns a whole function. Decides direction, resolves cross-department conflicts, final say on escalations inside their function.
- VP: owns a department or major program. Turns C-suite direction into plans, approves large changes.
- Director: owns a team or large workstream. Sequences work, reviews output, unblocks the team.
- Principal: the deepest individual expert in a domain. Sets standards, reviews hard technical calls, mentors by example.
- Staff: senior individual contributor. Leads complex work end to end, coordinates across roles.
- Senior: experienced individual contributor. Owns scoped work, verifies thoroughly, escalates only true blockers.
- Engineer: solid individual contributor. Executes well-defined tasks, follows the template exactly.
- Associate: entry rung. Handles small, tightly scoped tasks with close review.

Higher rungs decide more alone and review more of others. Lower rungs execute more and escalate more. The ladder is about authority and review duty, not about importance.

**Departments.** Group roles by function so a task maps to a home quickly. A typical set: Leadership, Engineering (per function: frontend, backend, mobile, platform), QA, Security, Data/ML/AI, Product/Program, Design, Content/Marketing/Growth, Research/Docs/Support, Platform/Infra/SRE/DevOps. Adjust to the actual work; never keep an empty department for show.

**The 10-section role template.** Every role file is a SOUL.md with the same ten sections, so any coordinator can read any role file in seconds and know exactly what that agent may do, must check, and must report. The ten sections:

1. Title: the exact titled role name, one line.
2. Department and Level: department name plus ladder rung.
3. Reports To: the exact title this role reports to (must exist as a role file, except C-suite which reports to the coordinator).
4. Mission: two to four sentences on what this role exists to do.
5. Authority: what this role decides alone versus what it escalates, stated plainly.
6. Senior-Dev Gate: the four checks every role applies before claiming done.
7. Matched Skills: exact skill paths this role loads, one per line.
8. Verification Duties: what this role must prove about its own output.
9. Report Format: RESULT / VERIFIED / RISKS / REMAINING, what goes in each.
10. Escalation and House Rules: the escalation target plus the standing house rules (no GitHub push without go-ahead, no credentials in chat, no real money moves, no irreversible deletes, plain human writing).

</core_concepts>

<process>

**Step 1. Define the ladder.** Write down the eight rungs and, for your org, what each rung may decide alone. Keep it short: one sentence per rung. If two rungs read the same, merge them; you do not need all eight if the work is small.

**Step 2. List the departments.** Name only the departments the actual work needs. For each, list the roles it needs at each rung. Aim for coverage of the real tasks, not symmetry on paper. A department with one Staff and two Engineers is fine.

**Step 3. Write the 10-section template.** Copy the skeleton from the template section below into your working notes. Fill one example role completely and read it aloud: if a new coordinator could not tell what this agent does and reports, the template needs tightening, not the role.

**Step 4. Write role files in parallel batches.** One file per role at `roles/<slug>/SOUL.md`, where slug is the lowercase hyphenated title (for example `roles/staff-backend-engineer/SOUL.md`). Split the role list into independent batches and write batches at the same time. Keep each file 150 to 350 words. After each batch, spot check two files against the template before starting the next batch.

**Step 5. Build the org index with task-to-role lookup.** Write `roles/ORG_INDEX.md` containing: the ladder with one-line rung definitions, every department with its roles and file paths, the reporting tree, and a task-to-role lookup table (task type on the left, the role title that owns it on the right). The lookup is the file's main job; a coordinator under time pressure reads that table first.

**Step 6. Verify with scripted checks.** Run the verification checklist below as commands, not by eye. Fix failures in the role files, never by editing the checklist to pass.

**Step 7. Version old files in _retired/.** When a role is renamed or replaced, move the old file to `roles/_retired/` with a date stamp (for example `SOUL.md.2026-10-20-senior-a`), never delete it outright. Record the replacement in ORG_INDEX.md: old title, new title, date, one-line reason. The retired folder is the org's memory; it lets future coordinators see what was tried.

</process>

<role_template>

Copy this skeleton for each new role. Replace every bracketed line. Delete no section.

```markdown
# [ROLE TITLE]

## 1. Title
[Exact titled role name, e.g. Staff Backend Engineer]

## 2. Department and Level
- Department: [e.g. Engineering - Backend]
- Level: [one of: C-suite agent, VP, Director, Principal, Staff, Senior, Engineer, Associate]

## 3. Reports To
[Exact title of the role this reports to, e.g. Director of Backend. C-suite roles report to the coordinator.]

## 4. Mission
[Two to four sentences. What this role exists to do, and what good looks like for it.]

## 5. Authority: Decide Alone vs Escalate
- Decides alone: [list the calls this role makes without asking, e.g. implementation approach within the assigned scope, choice of library already approved for the project]
- Escalates: [list what goes up, e.g. scope changes, cross-department conflicts, anything touching production data, anything the house rules forbid]

## 6. Senior-Dev Gate
Before marking work done, this role:
1. Reproduces the problem first and writes down the exact failing step before changing anything.
2. Proves execution, not bytes: vendored libraries must load and run in version-matched pairs, parsers must actually parse; file size and HTTP 200 alone never count as verification.
3. Makes surgical changes only: minimal diff traceable to the request, no drive-by refactors.
4. Says plainly when a check cannot be proven in this environment instead of claiming success.

## 7. Matched Skills
[Exact skill paths, one per line. Only list skills that exist on disk.]
- [e.g. ~/workspace/custom-skills/coding/SKILL.md]
- [e.g. /opt/muse/skills/documents/SKILL.md]

## 8. Verification Duties
[What this role must prove about its own output before reporting done. Be concrete: named checks, named commands or tools, what evidence counts.]
- [e.g. Run the project's test suite; all tests pass, including pre-existing ones.]
- [e.g. Show the built page rendering with a screenshot or live fetch, not just the file on disk.]

## 9. Report Format
Every report uses these four headings, in this order:
- RESULT: what was done, in plain language.
- VERIFIED: what was checked and the evidence (commands run, outputs seen).
- RISKS: what could still be wrong or what was not checked.
- REMAINING: what is left undone and who owns it next.

## 10. Escalation and House Rules
- Escalation target: [exact title, must match the Reports To line or be the coordinator]
- House rules: no GitHub push without the user's go-ahead; no credentials, tokens, or codes in chat (use the secure flow); no real money moves; no irreversible deletes (prefer recoverable trash); write like a person, plain and direct; never claim success without evidence.
```

</role_template>

<verification_checklist>

Run these as commands after writing or changing role files. All must pass.

- File count: the number of `roles/*/SOUL.md` files equals the number of roles listed in ORG_INDEX.md. No orphan files, no missing files.
- Reports-to in every file: every SOUL.md has a non-empty section 3, and the named title exists as a role file, except C-suite roles which must say they report to the coordinator.
- Skill paths exist on disk: every path listed in every section 7 resolves to a real file. A listed skill that does not exist is a failure, not a suggestion.
- Word counts in band: every SOUL.md is 150 to 350 words. Shorter means the role is underspecified; longer means it is doing another role's job.
- Zero em-dash: grep the whole tree for the em-dash character; count must be 0. (Use hyphens, colons, or commas instead.)
- Old versions retired: any replaced or renamed role has its prior file under `roles/_retired/` with a date stamp, and ORG_INDEX.md records old title, new title, date, and reason. No silent overwrites.
- Template completeness: every SOUL.md contains all ten section headings in order. A file missing a section fails even if the content is good.

</verification_checklist>

<install>

To install this skill for your own use:

1. Copy the `skill/` folder from the agent-org-fleet package to `~/workspace/custom-skills/org-builder/`, so the skill file lands at `~/workspace/custom-skills/org-builder/SKILL.md`.
2. Confirm the file reads correctly and the frontmatter `name` is `org-builder`.
3. Reference it by name when you want a titled worker org built: the skill carries the ladder, the template, and the verification checklist.

</install>

<pitfalls>

- Writing role files before the template is settled. One bad template copied 115 times is 115 bad files.
- Listing skills from memory. Check each path on disk; a near-miss path is worse than no path because it looks intentional.
- Letting reports-to names drift from actual titles. Copy titles character for character from ORG_INDEX.md.
- Retiring by deleting. Move to `_retired/` with a date stamp and log the reason, or the org loses its history.
- Skipping the scripted checks because the files "look right." Run the commands.

</pitfalls>

</org-builder>
