# Git

This document contains a curated list of useful Git commands and workflows.

## Commit

This section covers commands and techniques related to managing and modifying Git commits.

### Reset author

You can update the author information of the most recent commit without modifying the commit message.

```bash
git commit --amend --reset-author --no-edit
```

## Push

This section covers Git push commands and best practices for pushing code to remote repositories.

### Safe force pushing with `--force-with-lease`

The `--force-with-lease` option is a safer way to force push changes to a remote repository compared to the traditional force push.

#### Traditional force push: `git push --force` (dangerous)

The standard force push overrides the remote branch unconditionally.

When you use `git push --force`, you instruct the remote repository to overwrite its history with your local history, regardless of any updates on the remote side.

* **Risk:** If a collaborator pushes new commits to the remote branch after your last fetch or pull, a standard force push (`--force`) will overwrite and delete their work without warning.

#### Safe force push: `git push --force-with-lease` (recommended)

The `--force-with-lease` option adds a verification step before updating the remote repository.

This option checks whether your local representation of the remote branch matches the actual state of the remote branch.

* **Scenario A (Push allowed):** If no one has pushed new commits to the remote branch since your last fetch, Git assumes your changes are up to date and allows the force push to proceed.
* **Scenario B (Push rejected):** If another collaborator has pushed new commits, the actual state of the remote branch differs from your local representation. Git rejects the push and displays an error, preventing you from accidentally overwriting their work.

#### The house metaphor

To understand the difference, consider a metaphor about entering a house.

* **`git push --force`:** You break in and replace everything in the house with your own belongings, without checking if someone else has moved in.
* **`git push --force-with-lease`:** You check the lock and the interior before entering. If the lock or the layout changed since you last visited, you stop immediately to avoid causing damage.

#### Summary

Using `--force-with-lease` ensures safe history rewriting while protecting collaborative work.

This option lets you rewrite history safely (for example, after using `git commit --amend` or `git rebase` locally) while ensuring you do not overwrite changes from other team members. We recommend making `--force-with-lease` your default tool for force pushing in collaborative projects.
