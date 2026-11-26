# Current status — handover snapshot
Last repository review in ChatGPT: November 2026. Not a live check at package creation. Reinspect repository before acting.

## BF-001
Repository: https://github.com/kissalpar96-cpu/bookflow
Verified at last review: public repository, default main, squash merge enabled, merge commits and rebase merge disabled. Feature branch `chore/BF-001-initialize-repository` was one commit ahead of main, adding 14 .gitkeep files matching planned directories. Main contained README.md, .gitignore, LICENSE. No PR or matching BF-001 GitHub issue was found at that review. Active protect-main ruleset required PRs, zero approvals, resolved conversations, blocked force pushes and deletion; linear history was not enabled. Status checks deferred until CI exists.

## Acceptance criteria
- [x] Repository exists.
- [x] Initial README exists (heading needs correction at last review).
- [x] Java .gitignore exists (needs Maven/local secret patterns).
- [x] Initial directory structure exists on feature branch; not yet verified on main.
- [ ] Branching and commit conventions fully documented in CONTRIBUTING.md.
- [ ] No sensitive information committed (verify diff/history; no full secret audit performed).
- [ ] Successful local clone confirmed by developer.

## Remaining review findings
1. README heading `# # BookFlow` should be `# BookFlow`.
2. CONTRIBUTING.md was missing. Document GitHub Flow, single-issue branches, Conventional Commits, PRs, squash merge and secret handling.
3. Extend .gitignore with target/, .idea/, *.iml, .vscode/, .env, .env.*, !.env.example, *.pem, *.key. Check existing tracked files and avoid ignoring required build wrapper files.
4. Enable Require linear history if following agreed ruleset; verify settings rather than assume.
5. Create/link actual GitHub issue if desired; use real issue number in PR (BF-001 is a task identifier, not necessarily #1).
6. Commit and push changes on feature branch, open PR to main, review before merge. No merge without developer approval.

Useful links:
- https://github.com/kissalpar96-cpu/bookflow/compare/main...chore/BF-001-initialize-repository
- https://github.com/kissalpar96-cpu/bookflow/rules/28090994

## Next task
BF-002: architecture and ADRs. Only after BF-001 acceptance/review. No Spring Boot generation until BF-003/BF-004.
