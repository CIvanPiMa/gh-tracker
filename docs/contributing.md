# Contributing Guide

Contributions of all kinds are welcome — data fixes, bug reports, feature requests, translations, and code improvements.

---

## Types of Contributions

| Type | How |
|---|---|
| **Bug reports** | [File an issue](https://github.com/Lurkars/gloomhavensecretariat/issues/new/choose) with steps to reproduce |
| **Feature requests** | [Start a discussion](https://github.com/Lurkars/gloomhavensecretariat/discussions/new/choose) |
| **Data fixes** | Edit JSON files in `data/` and submit a PR |
| **Translations** | Use [Weblate](https://i18n.gloomhaven-secretariat.de/) |
| **Code** | Fork → branch → PR |

---

## Development Setup

See [docs/installation.md](./installation.md) for prerequisites and full setup. The short version:

```bash
git clone https://github.com/CIvanPiMa/gh-tracker.git
cd gh-tracker
npm install
npm run start   # http://localhost:4200
```

---

## Code Style and Linting

The project uses ESLint and Prettier.

```bash
# Lint TypeScript and HTML
npm run lint

# Auto-fix lint issues
npm run lint:fix

# Format all source files
npm run format

# Check formatting without writing
npm run format:check
```

Run lint and format before committing code changes. The pre-commit hook does not enforce these automatically.

---

## Working with Game Data

All game data lives in `data/`, with one subfolder per edition (e.g., `data/gh/`, `data/fh/`). Each subfolder contains JSON files for characters, monsters, scenarios, labels, and more.

The build script (`scripts/build-data.js`) compiles each edition folder into a single `src/assets/data/{edition}.json` file. This runs automatically via `npm run start` and `npm run build`.

### Making data changes

1. Edit the relevant JSON file in `data/`.
2. The dev server (`npm run start`) picks up changes automatically via nodemon.
3. Validate your changes by loading the affected scenario or character in the app.
4. For schema reference, see `data/schema.json` and [docs/data-format.md](./data-format.md).

### Pre-commit hook warning

All files in `data/` are automatically formatted and staged on every commit via the pre-commit hook (`scripts/pre-commit.mjs`).

> If you have local data changes you do NOT want committed, use `--no-verify`:
>
> ```bash
> git commit --no-verify -m "your message"
> git push --no-verify
> ```

For full data format documentation, see [docs/data-format.md](./data-format.md).

---

## Translations

Translations are managed via [Weblate](https://i18n.gloomhaven-secretariat.de/). Log in with your GitHub account and contribute to any supported language.

Label files (e.g., `data/gh/label/en.json`) map internal keys to display strings for each language. Weblate handles the sync back to the repository.

<img src="https://i18n.gloomhaven-secretariat.de/widget/gloomhavensecretariat/multi-auto.svg" alt="Translation status" />

---

## Submitting Pull Requests

1. Fork the repository and create a feature branch:
   ```bash
   git checkout -b fix/bandit-guard-stats
   ```
2. Make your changes. For data changes, stick to the `data/` folder. For code changes, follow the existing patterns in `src/`.
3. Run `npm run lint` and `npm run format:check` to ensure code quality.
4. Commit with a clear message:
   ```bash
   git commit -m "fix: correct bandit guard elite HP at level 3"
   ```
5. Push and open a PR against the upstream repository. Describe what you changed and why.

---

## Issue Reporting Guidelines

When filing a bug, include:

- The **edition** and **scenario** where the issue occurred
- Steps to **reproduce** the problem
- **Expected** vs. **actual** behavior
- Browser/OS and app version (check Settings → About)
- A screenshot or screen recording if helpful

For data errors (wrong monster stats, missing scenario rule, etc.), also include the rulebook page or BGG reference where the correct data can be verified.

---

## Code of Conduct

Be respectful and constructive. This is a community project maintained by volunteers. Feedback, questions, and disagreements are welcome — personal attacks are not.

See the [Contributor Covenant](https://www.contributor-covenant.org/) for general guidance.
