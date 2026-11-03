# Contributing to Oxyde

## Branches

Two long-lived branches:

| Branch | Role | Receives |
|---|---|---|
| `main` | Production. Always releasable; releases are tagged here (`v0.1.0`). | Pull requests from `develop` or `hotfix/*`, as merge commits |
| `develop` | Development. Everything lands here first. | Pull requests from short-lived branches, squashed |

Neither accepts direct pushes, force pushes or deletion.

Everything else is short-lived and branches from `develop`:

```
feat/<short-name>      a new capability
fix/<short-name>       a bug fix
docs/<short-name>      documentation only
perf/<short-name>      performance work
refactor/<short-name>  no behaviour change
chore/<short-name>     tooling, dependencies, CI
```

An urgent production fix branches from `main` as `hotfix/<short-name>`, merges
into `main`, then `main` is merged back into `develop`.

```
main     ─────●──────────────────────●────────▶  (tags: v0.1.0, v0.2.0)
               \                    /
develop  ───●───●────●────●────●───●──────────▶
                 \        \    /
feat/…            ●────────●──
```

## Making a change

1. Branch from `develop`.
2. Keep the change focused: one concern per pull request.
3. Open a pull request against `develop`. GitHub proposes `main` by default,
   so check the base branch.

## Releasing

1. Open a pull request from `develop` to `main`, and merge it with a merge
   commit. Squashing would make the two branches diverge.
2. Tag the merge commit on `main`: `git tag v0.1.0 && git push origin v0.1.0`.

## Commit messages

[Conventional Commits](https://www.conventionalcommits.org/):

```
feat(parser): accept nested blocks
fix(cli): report the missing path
docs(readme): explain the setup
```
