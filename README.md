# Generic Python Project Template

- UV based
- pre-commit hooks with Conventional Commits to regulate commit messages.
- Ruff for linting
- MyPy for type checking
- uses a custom Python script to check for secrets

## Setup

`git clone https://github.com/Python-Test-Engineer/gha-python.git`

`uv sync` - installs dependencies

`uv run pytest -vs` - runs pytest to check all wired OK. You can remove files from `src` and `tests` to add your own files.

`uv run pre-commit install --hook-type commit-msg` sets up precommit and conventional commits

Test:

`git add .`

`git commit -m "will not work"` - this will fail

`git commit -m "docs: update README with setup instructions"` - this will pass as if follows conventional commits.


# Conventional Commits Guide

Conventional Commits is a specification for adding human and machine-readable meaning to commit messages. It provides a simple set of rules for creating an explicit commit history.

TIPS:

feat/fix or breaking changes will create Semantic Versioning bumps.

To avoid this use 'docs/chore/perf/style/test/refactor' prefixes as these will idicate what you are doing without affecting versioning which can be saved for deployment push.

## Basic Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

## Types

**feat**: A new feature for the user
```
feat: add user authentication
feat(auth): implement password reset
```

**fix**: A bug fix
```
fix: resolve login validation error
fix(api): handle null response in user endpoint
```

**docs**: Documentation only changes
```
docs: update README installation steps
docs(api): add authentication examples
```

**style**: Changes that don't affect code meaning (white-space, formatting, etc.)
```
style: fix indentation in components
style(css): remove unused imports
```

**refactor**: Code change that neither fixes a bug nor adds a feature
```
refactor: simplify user validation logic
refactor(utils): extract common date formatting
```

**perf**: A code change that improves performance
```
perf: optimize database queries
perf(images): implement lazy loading
```

**test**: Adding missing tests or correcting existing tests
```
test: add unit tests for user service
test(auth): cover edge cases in login flow
```

**build**: Changes that affect the build system or external dependencies
```
build: update webpack configuration
build(deps): bump lodash from 4.17.20 to 4.17.21
```

**ci**: Changes to CI configuration files and scripts
```
ci: add automated testing workflow
ci(github): update deployment pipeline
```

**chore**: Other changes that don't modify src or test files
```
chore: update .gitignore
chore(release): bump version to 1.2.0
```

## Breaking Changes

Add `!` after the type/scope to indicate breaking changes:
```
feat!: remove deprecated API endpoints
feat(auth)!: change password requirements
```

Or use the footer:
```
feat: add new authentication method

BREAKING CHANGE: old auth tokens are no longer valid
```

## Examples

**Simple feature:**
```
feat: add dark mode toggle
```

**Bug fix with scope:**
```
fix(checkout): prevent duplicate order submissions
```

**Documentation update:**
```
docs: add contributing guidelines
```

**Breaking change:**
```
feat!: upgrade to Node.js 18

BREAKING CHANGE: Node.js 16 is no longer supported
```

**With body and footer:**
```
feat(lang): add French language support

Add complete French translations for all user-facing text
including error messages and form labels.

Closes #123
```

## Benefits

- Automatically generating changelogs
- Automatically determining semantic version bumps
- Communicating changes to teammates and stakeholders
- Triggering build and publish processes
- Making it easier to explore a more structured commit history

## Tips

- Use the imperative mood ("add" not "added" or "adds")
- Keep the description under 50 characters when possible
- Use the body to explain what and why vs. how
- Reference issues and pull requests in the footer