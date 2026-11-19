# Contributing

## Setup

1. Clone the repo.
2. Enable the Git hooks (required once per clone):

   ```sh
   git config core.hooksPath .githooks
   ```

3. Install the tools the hooks and CI use: `pnpm` and `terraform`.

## Workflow

1. Branch from `main`: `git switch -c <type>/<short-description>`.
2. Make your change. Keep PRs small and focused.
3. Commit using [Conventional Commits](https://www.conventionalcommits.org). release-please builds the changelog and version bumps from these messages.
4. Push and open a pull request. Fill in the PR template.
5. Wait for CI to pass and for review before merging.

## Commit messages

Format: `type(scope): summary`, for example `fix(api): handle empty request body`.

| Type | Use for | In changelog |
| --- | --- | --- |
| `feat` | New functionality | Features |
| `fix` | Bug fixes | Fixes |
| `perf` | Performance improvements | Performance |
| `revert` | Reverting a change | Reverts |
| `deps` | Dependency updates | Dependencies |
| `refactor`, `docs`, `test`, `ci`, `chore` | Everything else | Hidden |

Mark breaking changes with `!` after the type (`feat!: ...`) or a `BREAKING CHANGE:` footer.

## Pre-commit checks

The hook runs Terraform `init -backend=false`, `validate` and `fmt -check` on changed Terraform, and `pnpm run lint`, `test` and `format` on changed apps. Fix failures rather than bypassing with `--no-verify`; CI runs the same checks.

## Security

Do not report vulnerabilities in public issues. See [SECURITY.md](SECURITY.md).

## Conduct

By participating you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).
