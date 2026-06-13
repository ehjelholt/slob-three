# Contributing

## Commit Messages

This project follows **Conventional Commits** to maintain a clean, readable history and enable automated changelog generation.

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type

Required. **Must be lowercase**. One of:

- **feat** – A new feature
- **fix** – A bug fix
- **test** – Add or update tests
- **style** – Code style changes (formatting, missing semicolons, etc.) that don't affect logic
- **refactor** – Code refactoring without feature changes
- **perf** – Performance improvements
- **chore** – Dependency updates, tooling, build config, etc.
- **docs** – Documentation changes
- **ci** – CI/CD configuration

### Scope

Optional. Encapsulates the area of the codebase affected, e.g. `(ui)`, `(storage)`, `(server)`, `(types)`. Use lowercase with hyphens if needed.

### Subject

- **Must capitalize first letter of subject** (after the colon, leave the type and scope lowercase)
- Imperative mood ("Add feature" not "Added feature")
- No period at the end
- Keep to 50 characters or fewer

### Body

Optional. Provide context and explain _why_ the change was made, not what (the diff shows that).

### Footer

Optional. Reference issues: `Closes #123` or note breaking changes: `BREAKING CHANGE: description`.

### Example

```
feat(storage): Persist items to localStorage on save

Implement a localStorage adapter to automatically save items when the
user adds, edits, or deletes an entry. Load persisted data on app startup
to restore the user's previous state.

Closes #42
```

### Git Hooks

This project uses **commitlint** to enforce Conventional Commits. Commit messages that don't conform will be rejected at commit time.

To bypass (not recommended):

```bash
git commit --no-verify
```

## Code Style

- **Language:** TypeScript
- **Formatter:** Prettier (run `npm run format`)
- **Linter:** ESLint (run `npm run lint`)

Format and lint before committing when possible.
