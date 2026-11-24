---
name: ucsc-pull-request
description: Write and validate short pull request titles and descriptions that say what changed, why, and how to test it, using ASD-STE100 Simplified Technical English, without repeating the spec or the commit log and without AI attribution. Use when the user asks to open, draft, rewrite, or review a pull request or a PR description.
---
# UCSC Pull Requests

Create and validate pull request (PR) descriptions that tell a reviewer what changed, why it changed, and how to test it. Use ASD-STE100 Simplified Technical English (STE), link to the spec instead of repeating it, and omit AI self-attribution.

## Where the PR Fits

Three documents describe a piece of work. Each one has a different job.

| Document | Job | Detail |
| --- | --- | --- |
| Spec | Why the work exists and what the team agreed to | Most |
| Commit | One building block of the change | Least |
| Pull request | What changed as a whole, a short reason, and how to test it | Between the two |

A PR has more explanation than a commit, because a reviewer must understand the full change and must be able to test it. A PR has less explanation than the spec, because the spec is already written. Give the reason for the change in 1 or 2 sentences, and link to the spec for the full reason. If the PR starts to repeat the spec, make the text shorter and keep the link.

## When to Use

- The user asks to open or create a pull request
- The user asks to draft, rewrite, or review a PR title or description
- The agent prepares a PR after it pushes a branch

## Steps

### 1. Inspect the Branch and Spec Context

Find the base branch, then read the full change, not only the last commit.

```sh
git log --oneline <base>..HEAD
git diff <base>...HEAD
```

Find the spec. A spec is a GitHub issue with the label `spec` (see the `ucsc-spec` skill). Look for an issue number in the branch name and in commit trailers such as `Ref:` or `Fixes`. If you cannot find one, ask the user. Read the spec so that you know what to leave out.

### 2. Write the Title

Use the Conventional Commits format from the `ucsc-git-commit` skill: `<type>(<optional-scope>): <description>`.

- Describe the full change, not the last commit.
- Start the description with a lowercase imperative verb.
- Keep the title to 72 characters or fewer.
- Add `!` after the type or scope if the change is a breaking change.

### 3. Write the Body

Use this template. Remove an optional section if it has no content.

```markdown
## What changed and why
1 to 3 sentences. Say what is different after this PR merges and why.
Link to the spec (#<spec number>) for the full reason.

- One bullet for each change that a reviewer can see or must know about.

## How to test
1. A step that the reviewer can do.
2. Another step. Give the result that the reviewer must see.

## Notes for the reviewer (optional)
Facts that are not in the spec and not clear from the diff.

Closes #<spec number>
```

**What changed and why**

- Describe behavior and results. Group related commits into one bullet.
- Give the reason in 1 or 2 short sentences. A reviewer must not need to open the spec to know the purpose of the PR.
- Link to the spec where a reader needs more detail (for example, "See #128 for the full list of rules"). Do not copy the detail.
- Do not paste the commit log. The reviewer can read the commits.
- Do not describe each file. The reviewer can read the diff.
- Keep this section to 150 words or fewer.

**How to test**

- Write numbered steps that a person can follow without help from the author.
- Give exact commands, URLs, user roles, and test data.
- For each check, give the expected result.
- Include setup steps only if they are different from the usual setup of the project.
- Include only the automated tests that you ran. Do not say that tests pass if you did not run them.
- If there is no way to test a change by hand, say so and say what gives confidence instead.
- If the change is visual, ask the user for screenshots. Do not invent them.

**Notes for the reviewer**

Use this section only for facts that the reviewer cannot get from the spec or the diff:

- A choice in the implementation that is not obvious, and the reason for it
- A difference between the implementation and the spec
- A risk, or a part of the diff that needs a careful review
- Work that this PR does not include

**Spec link**

Follow the `ucsc-spec` skill: use `Closes #<number>` if this is the last PR for the spec, and `Refs #<number>` if it is not.

### 4. Filter Out Spec Duplication and AI Attribution

- Give the reason for the change in 1 or 2 sentences. Do not copy the goal, the background, the user stories, or the full reasons for the approach. Link to the spec for them.
- Do not copy the acceptance criteria. The test steps show how to check the work; the spec says what "done" is.
- Do not copy decisions from the spec. If the implementation differs from a decision, state the difference in the notes and tell the user that the spec needs an update.
- Never attribute the AI agent. Do not add model names, tool names, "Generated with..." footers, or `Co-authored-by:` lines.

### 5. Draft Using ASD-STE100 Simplified Technical English

Apply the same STE rules as the `ucsc-git-commit` skill:

- **Use approved, simple words:** "use" not "utilize", "make sure" not "ensure", "change" not "modify", "remove" not "eliminate", "start" not "initiate", "need" not "require".
- **One word, one meaning:** Use each word in one part of speech and with one meaning.
- **Use active voice:** Write test steps as commands ("Open the page", "Run the tests"). Write descriptions with a subject that does the action.
- **Keep sentences short:** 20 words or fewer for instructions, 25 words or fewer for descriptions.
- **One instruction for each step:** Do not put two actions in one test step unless they occur at the same time.
- **Avoid long noun clusters:** Do not put more than 3 nouns together.
- **Allow Technical Names:** Keep code identifiers, file paths, commands, and project terms exact.
- **Avoid filler:** Omit "this PR", "in order to", "basically", and "various improvements".

### 6. Validate Against the Checklist

- Title has a valid Conventional Commits prefix and is 72 characters or fewer.
- "What changed and why" describes the result of the full branch, gives a short reason, and is 150 words or fewer.
- "How to test" has numbered steps, and each check has an expected result.
- A reviewer who has not read the code can follow the test steps.
- The reason is 1 or 2 sentences. No text is a copy of the spec. The spec has a link.
- The body is not a list of commits or a list of files.
- No AI self-attribution is included.
- Every sentence is in active voice and uses simple STE vocabulary.

### 7. Show the Draft, Then Create the PR

Show the title and body to the user and wait for approval before you create or edit a PR.

```sh
gh pr create --base <base> --title "<title>" --body-file <file>
```

To change an existing PR, use `gh pr edit <number> --title "<title>" --body-file <file>`. Give the user the PR link.

If `gh` is not installed or not signed in, tell the user and give them the title and body as Markdown to paste.

## Examples

**Bad (repeats the spec, lists commits, no test steps, non-STE, AI attribution):**

```markdown
Event calendar updates

## Background
Campus units have long requested the ability to filter the events calendar
by department, since visitors currently have to scroll through all events.
Per the spec, the filter must be keyboard accessible, must persist in the
URL, and must support multiple departments.

## Commits
- add department taxonomy query
- add filter component
- fix lint
- address review feedback

This PR utilizes a new REST parameter in order to facilitate filtering.
Tests were added.

🤖 Generated with an AI assistant
```

**Good (says what changed, why, and how to test it, links the spec, ASD-STE100, no AI attribution):**

```markdown
feat(events): add department filter to calendar

## What changed and why
Visitors can filter the events calendar by one or more departments. Before,
they had to scroll through all events to find their department (see #128).

- The calendar shows a "Department" filter above the event list.
- The `events` REST route accepts a `department` parameter.
- The selected departments stay in the URL as `?department=`.

## How to test
1. Run `npm run test:unit`. All tests pass.
2. Open `/events` on a site with events in two or more departments.
3. Select one department. The list shows only the events of that department.
4. Select a second department. The list shows the events of the two departments.
5. Reload the page. The same departments stay selected.
6. Use only the keyboard to open the filter and clear it. The list shows all events.

## Notes for the reviewer
The filter reads departments from the `department` taxonomy, not from event
meta, because the meta field is empty on older events.

Closes #128
```

## Gotchas

- **Retelling the spec:** The reason is 1 or 2 sentences. If it grows into a paragraph, stop and link the spec.
- **Retelling the commits:** A PR body that is a commit list adds nothing. Describe the result of the commits together.
- **Vague test steps:** "Test the filter" is not a step. Say what to do and what result to expect.
- **Tests that did not run:** Report only the tests that you ran, with their real results.
- **A PR with no spec:** For a small change with no spec, make sure that "What changed and why" gives the full reason in 1 or 2 sentences. Do not write a spec inside the PR.
- **A PR that needs a long explanation:** If the notes grow past a few sentences, the content belongs in the spec. Tell the user and propose a spec update.
- **Breaking code identifiers for STE:** Never change function names, file names, or commands to fit STE vocabulary.
- **Self-attribution footers:** Never append "Generated with..." lines, model names, or `Co-authored-by:` lines.
