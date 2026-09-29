---
name: shipshape
description: After a Graphite stack is queued to merge, confirm it landed on main, tidy the local branches, and bring Linear up to date.
argument-hint: "Optional: PR numbers or a ticket ID, if not the current stack"
disable-model-invocation: true
---

# Shipshape

Two parts, in order: **check against delivery**, then **update the paperwork**.
Start part 2 only once part 1 has confirmed that every PR landed.

## Record what is shipping

Do this first, while still on the stack: the sync in part 1 deletes the
shipped branches.

- List the stack's branches with `gt ls -s`, and each branch's PR number and
  title with `gh pr view <branch> --json number,title`.
- If the session is not on the stack, take the PR numbers from the user's
  message, or ask.
- Note every ticket ID in the branch names, PR titles and commit messages.

## Part 1: check against delivery

The merge queue takes a few minutes. Graphite *closes* the PRs on GitHub
rather than merging them, so a PR's state does not tell you whether it landed.
The test is `main`: each PR lands as one squashed commit whose subject ends
`(#NNNN)`.

1. **Move to a dummy branch off `main`.** `main` is usually checked out in
   another worktree, and a branch can only be checked out in one. Take the
   lowest `dummy-branch-N` (N = 1, 2, …) that `git worktree list` does not
   show as checked out. Switch to it if it exists, otherwise create it from
   `origin/main`, then give it `main` as its Graphite parent:

   ```bash
   git fetch origin main
   git switch dummy-branch-N || git switch -c dummy-branch-N origin/main
   gt track -p main
   ```

2. **Check whether the commits landed.** Wait one minute first: run `sleep 60`
   as a background task and check when it completes (foreground sleeps may be
   blocked). Then run this for each PR:

   ```bash
   git fetch origin main && git log origin/main --oneline --grep '(#NNNN)'
   ```

   Repeat at one-minute intervals, up to five checks.

3. **All landed:** run `gt sync -d`. It fast-forwards `main`, deletes every
   local branch whose PR is merged or closed (the shipped stack included)
   without prompting, and restacks the dummy branch. Go to part 2.

4. **Not all landed after five checks:** diagnose, report and stop. A stack
   lands bottom-up, so a partial landing is possible. For each PR that has
   not landed, check `gh pr view <N> --json state,mergeStateStatus,statusCheckRollup`:
   a PR that is open again has left the queue, and failed checks or conflicts
   say why. Report each PR as landed or not, with the likely cause. Leave
   Linear alone, and skip `gt sync -d`: the branches are still needed.

## Part 2: update the paperwork

1. **Find the tickets.** Use the ticket IDs recorded earlier, and the PR links
   Linear shows as attachments. Fetch each ticket with its comments and
   relations. Read the current description: it may have changed since the
   work started.

2. **Decide whole or part.** Compare the ticket's acceptance criteria and
   checklist with what landed. Treat any difference from the current
   description as a deviation to record.

3. **No ticket:** ask the user for permission to create a concise one that
   summarises the work, with status [your "shipped" status]. Propose the
   project in the question: [your project for small improvements] for a small
   improvement, [your project for bug fixes] for a bug fix, or a themed project
   that clearly fits.

4. **Comment on every ticket.** Say what shipped (PR numbers and the commit on
   `main`), each deviation from the spec and why, new findings (surprises in
   the data, reconciliation figures), and anything left open. Keep it short.

5. **Set the status.** Complete: set it to [your "shipped" status]. Partial:
   tick the checkboxes for the parts that shipped (a `patch` edit to the
   description), leave the status, and say in the comment what shipped and
   when.

6. **Propose follow-up tickets** for issues that came up during the work:
   open questions, review comments worth doing later, problems found along the
   way. Ask the user for permission in one question, proposing a status for
   each: [your "ready to build" status] when the ticket says what to build and
   how to check it, [your "backlog" status] when it is a question or needs
   product input. Create the approved ones assigned to the user, in the same
   project as the shipped ticket, and related to it.

## Report

End with: the commits on `main`, the branches deleted, each Linear change with
its link, and any question still waiting on the user.
