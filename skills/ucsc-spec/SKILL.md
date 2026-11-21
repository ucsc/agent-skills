---
name: ucsc-spec
description: Write and maintain feature specs as GitHub issues. Use when the user wants to spec, plan, or scope a feature or change, update or review an existing spec, record a decision about planned work, or when a repo has a ROADMAP.md that needs to be moved into specs.
---

# Specs as GitHub issues

A spec is one GitHub issue, in the repo where the work will happen, with the label `spec`. This skill uses the `gh` command line tool.

## Rules

1. **One spec, one topic.** If a spec grows a second topic, ask to split it into a second issue and link the two.
2. **The issue body is the current agreement.** It always says what the team has agreed to right now.
3. **Comments are the discussion.** Never edit or delete comments. Questions, options and arguments go in comments, not in the body.
4. **Decisions are permanent.** The body has a `Decisions` list. Only add to it. If a decision is reversed, keep the old line, mark it `(superseded by the decision of YYYY-MM-DD)`, and add the new one.
5. **Never overwrite a spec.** Before any edit, read the current body and all comments. Change only the sections that need it. Leave every other section exactly as it is.
6. **Do not guess.** Anything the user has not answered goes under `Open questions`. Do not fill gaps with assumptions.
7. **Ask before you publish.** Show the user the draft or the change and wait for a yes before you create or edit an issue.

## Write a new spec

1. **Look for an existing spec.**
   `gh issue list --label spec --state all --search "<keywords>"`
   If one exists, update it instead (see below).
2. **Interview the user.** Ask only what the conversation has not already answered. Keep it to about five questions:
   - What problem does this solve, and for whom?
   - How will we know it is done?
   - What is out of scope?
   - What limits apply (hosting, deadlines, accessibility, other sites or plugins it touches)?
   - Is there an approach already in mind, or one already ruled out?
3. **Draft the spec** with the template below and show it to the user.
4. **Create the issue** after the user approves.
   `gh issue create --title "<short name>" --label spec --body-file <file>`
   If the label does not exist: `gh label create spec --description "Feature or change specification"`
5. **Give the user the issue link.**

## Template

```markdown
## Goal
3–5 sentences in terse, nontechnical language, describing what is wrong or missing, who it affects, and what will be true when this is done.

## Approach
How we plan to do it. Leave short if not yet agreed.

- List changes with descriptions for what will change
- Do not focus on backward compatibility.
- Pay close attention to upgrade paths and if possible avoid any change that requires client effort.

## Decisions
- YYYY-MM-DD: The decision, and the reason in one sentence. (link to the comment where it was discussed, if any)

## Acceptance criteria
- [ ] A result someone can check

## Open questions
Any question that still needs an answer

## References
Issues, PRs, docs, or other resources that are relevant to the spec.
```

Leave a section empty with "None yet" instead of removing it.

## Update a spec

1. Read it first: `gh issue view <number> --comments`
2. Work out what changed: a new decision, an answered question, a change of scope, a finished criterion.
3. Show the user the exact change.
4. Edit only those sections: `gh issue edit <number> --body-file <file>`. The file must contain the full current body with only your changes applied.
5. Add a comment that says what changed and why: `gh issue comment <number> --body "<summary>"`

When a question is answered, remove it from `Open questions` and add the answer to `Decisions`.

## Close a spec

- Pull requests refer to the spec: `Closes #<number>` for the last one, `Refs #<number>` for the others.
- When work ships, check that every acceptance criterion is ticked, then close the issue.
- If the work is dropped, add a decision that says why, then close the issue as not planned.

## Move a ROADMAP.md into specs

Do this when a repo has a `ROADMAP.md`. Specs replace it.

1. Read the whole file. Split it into separate topics, one per future spec.
2. Show the user a list: the proposed issue title and one line for each. Mark items that look finished or out of date, and ask whether to drop them. Wait for approval.
3. Create one issue per approved item with the template. Copy decisions and reasons from the file word for word into `Decisions`. Put anything unclear under `Open questions`.
4. Ask the user before you delete the file. Then delete `ROADMAP.md` in its own commit. List the new issue numbers in the commit message. The old text stays in git history.
5. Do not create a new `ROADMAP.md`. The list of specs is: `gh issue list --label spec`

## If `gh` does not work

If `gh` is not installed or not signed in, tell the user and stop. Offer the draft as Markdown that they can paste into a new issue. Do not save the spec to a file in the repo instead.
