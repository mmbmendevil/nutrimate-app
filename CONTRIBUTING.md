# Contributing

Thank you for your interest in improving NutriMateApp. This project is maintained as an Android academic and portfolio project, so contributions should preserve the existing app behavior unless a change is clearly requested and reviewed.

## Development Principles

- Keep the current package name, namespace, and application ID unchanged.
- Do not restructure folders without a clear reason.
- Keep changes focused and easy to review.
- Prefer small pull requests over broad rewrites.
- Document user-visible or setup-related changes.

## Branch Naming

Use short, descriptive branch names:

- `feature/add-meal-history`
- `fix/onboarding-validation`
- `docs/update-setup-guide`
- `chore/gradle-cleanup`
- `test/add-result-screen-tests`

## Commit Messages

Use concise conventional-style commit messages:

```text
docs: add setup guide
fix: handle empty onboarding values
feature: add persistent meal history
chore: update gitignore
test: add profile calculation tests
```

Recommended commit types:

- `docs` for documentation changes.
- `fix` for bug fixes.
- `feature` for new app functionality.
- `chore` for maintenance tasks.
- `test` for test additions or updates.
- `style` for formatting-only changes.

## Pull Request Guidelines

Each pull request should include:

- A clear summary of what changed.
- The reason for the change.
- Screens or behavior affected, if applicable.
- Testing performed.
- Any known limitations or follow-up work.

Before opening a pull request:

- Run a Gradle sync in Android Studio.
- Build the debug app.
- Confirm the app launches.
- Check that no generated build output is committed.
- Keep unrelated changes out of the pull request.

## Coding Style

- Follow standard Java and Android naming conventions.
- Use clear Activity, method, and variable names.
- Keep UI text in resources when practical.
- Keep layout IDs descriptive and consistent.
- Avoid adding logic directly to unrelated screens.
- Keep comments useful and brief.

## Documentation Style

- Keep Markdown headings consistent.
- Use commands that work for the current Gradle Wrapper.
- Do not document features that are not implemented.
- Update `README.md`, `SETUP_GUIDE.md`, or `PROJECT_STRUCTURE.md` when project setup or behavior changes.

## Testing Expectations

For code changes, verify at least:

```bash
gradlew.bat assembleDebug
```

On macOS/Linux:

```bash
./gradlew assembleDebug
```

When adding business logic, add or update tests where practical. When changing UI navigation, manually verify the affected screens on an emulator or physical device.
