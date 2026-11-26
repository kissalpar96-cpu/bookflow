# Contributing to BookFlow

## GitHub Flow

1. Pick one issue and agree on its acceptance criteria before starting work.
2. Create a branch from an up-to-date `main`. Include the task ID and a short description, such as `chore/BF-001-initialize-repository` or `feature/BF-101-create-organization`.
3. Keep changes focused on that issue. Run the checks relevant to your changes and push your branch.
4. Open a pull request targeting `main`. Link the GitHub issue using its actual number, summarize the changes, and record the checks you ran. `BF-001` is a task ID. A reference such as `Closes #42` uses the GitHub issue number.
5. Resolve review conversations and wait for any required checks to pass. Squash merge after review and approval from the maintainer. All changes to `main` go through pull requests.

## Commit messages

Use Conventional Commits. Write `type: summary` or `type(scope): summary`. Prefer a scope that identifies the affected service or area. Write a short, imperative summary in English.

```text
chore(repo): document the development workflow
feat(booking): implement appointment creation
fix(booking): reject overlapping appointments
```

Use the same format for the final squash commit message.

## Secrets and local configuration

- Supply credentials and tokens through environment variables or an approved secret store. Keep local `.env` files and private keys out of Git.
- Use placeholders in `.env.example` and other committed examples.
- Review staged changes before committing. If a secret is committed, revoke or rotate it promptly and notify the maintainer.
