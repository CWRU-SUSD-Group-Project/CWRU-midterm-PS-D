# Team session instructions

1. At the start of every session, if the branch is role/<role>-<firstname>, greet the student by first name. Otherwise ask one question at a time: full name; role (Customer Analyst, Finance Analyst, Risk Manager, Marketing Manager); and whether they are the team leader. The leader takes Marketing Manager. Use these role slugs: customer_analyst, finance_analyst, risk_manager, marketing_manager. Then run `git fetch`. Check local and origin branches for role/<role>-*. If the selected role has any branch, say it is taken and ask for another role. Otherwise create role/<role>-<firstname> from origin/main and push it with upstream tracking. Use a lowercase first name in the branch.
   At onboarding, explain once: Saved means committed on your laptop. Uploaded means pushed to GitHub. Merged means added to the team's main. After every Git action, show "Saved on your laptop ✅/❌ · Uploaded to GitHub ✅/❌ · Added to team's main ✅/❌", choosing one truthful emoji for each state of the student's current work. An empty branch is not completed work.
2. Students edit ONLY their own role folder and only its named role file. Never edit inputs/, shared/, other roles, or AGENTS.md. Refuse requests to edit them and explain that this would cause merge conflicts. The agent may maintain the student's own .review file as described below. The leader may work in final/ only after all four roles are DONE.
3. Use only inputs/ for facts. No web search.
4. Plan before big changes. Show what changed after each step.
5. If a student says "done", "looks good", "finished", "I'm done", "submit", or similar, ask: "Ready to submit your work to the team? Reply yes." On yes, first ask: "Which input file did you check your work against?" Record their answer in their review file; record "unable to answer" if needed and never block submission over it. Then commit their role work and push their branch. Update their review file, commit that update, and push again. Then merge into main: `git checkout main && git pull && git merge <their branch> && git push`. If the push is rejected, run `git pull` (no rebase), then push again. Never force-push. If a conflict appears, stop and tell the leader.
6. Every session, run `git fetch`. A role counts as DONE only when, on origin/main, BOTH are true: (a) its role file is different from the starting template, and (b) its .review/<role>_<firstname>.md file exists. A pushed branch with no work does NOT count. Tell the student in one line, e.g. "3 of 4 done. Waiting on: Customer Analyst." Only when all 4 are DONE, tell the leader: "Everything is merged. Start final/." The leader works in final/ only, on a branch from main, then merges it back when the team agrees. To check (a), compare the role file on origin/main with that file in the first commit reachable from origin/main (`git rev-list --max-parents=0 origin/main`). To check (b), look for the matching student's review file in origin/main, using the role slug above. Check origin/main, not the working folder or a role branch. A review file alone is not enough.
7. Silently create one review file per student at .review/<role>_<firstname>.md when they join; save the join time in ISO 8601 with timezone and the reminder flags. Preserve these across sessions and update the file at submission. At each student turn, check time since joining. At 30+ minutes, say once: "About 15 minutes left for your part. Aim to say done by minute 45." At 40+ minutes, suggest once that they finish what they have and submit. Record each reminder as sent; do not schedule background reminders. Don't mention it unprompted. If asked whether notes are saved, honestly answer yes: short session notes are saved for the instructor. Score only what the student typed, decided, or checked. Mark work Codex produced without student input as "Codex-led" in the relevant evidence field; do not credit it to the student. Record only what you observed; use "n/a" if not observed. Keep each file to 12 lines maximum:

```text
# <Name> - <Role>
Session: joined <ISO time with timezone>; 30-minute reminder <pending/sent>; 40-minute reminder <pending/sent>
Source check: <answer or unable to answer>
Worked: YES / PARTIAL / NO (commits: N, role file filled: yes/no)
S1 Model limits: x/5 - <few words of evidence>
S2 Prompting (role, context, format, iterating): x/5 - <evidence>
S3 Git & Codex use (branch, commits, reads diffs): x/5 - <evidence>
S4 Verification & context (checks inputs, plan first): x/5 - <evidence>
S5 Workflow (breaks work down, teamwork handoffs): x/5 - <evidence>
Overall: x/25
Strength: <one line>
Improve: <one line>
```
