# Contributing to WorkStream KB

Thank you for your interest in contributing! This guide will help you get started.

## Getting Started

1. **Fork** this repository
2. **Clone** your fork:
   ```bash
   git clone https://github.com/<your-username>/workstream-kb.git
   cd workstream-kb/scripts && npm install
   ```
3. Create a **feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
4. Make your changes, commit, and push to your fork
5. Open a **Pull Request** against `main`

## Branch Naming

| Prefix | Use |
|--------|-----|
| `feature/` | New features |
| `fix/` | Bug fixes |
| `refactor/` | Code refactoring |
| `docs/` | Documentation changes |

## Code Style

- **ES modules** (`import`/`export`), Node.js 20+
- **camelCase** for variables/functions, **PascalCase** for components
- All config via `scripts/lib/config.mjs` — no hardcoded values
- Atomic file writes: write to temp file, then `renameSync`
- Korean for user-facing text, English for code/comments

## Pull Request Guidelines

- Keep PRs focused on a **single purpose**
- Include a clear description of **what** and **why**
- Reference related issues (e.g., `Closes #123`)
- Ensure no sensitive data (tokens, credentials) is committed
- Test your changes manually before submitting:
  ```bash
  node scripts/fetcher.mjs    # If touching fetcher
  node scripts/processor.mjs  # If touching processor
  ```

## Project Architecture

```
Fetcher (Layer 1) → inbox/*.json → Processor (Layer 2) → daily/{date}.md
       ↓                                    ↓
  MS Graph API                        Claude CLI (1 call)
  No AI cost                          ~35K tokens/day
```

- **Fetcher** (`scripts/fetcher.mjs`): Collects emails and Teams messages via MS Graph API
- **Processor** (`scripts/processor.mjs`): Groups messages, filters noise, calls Claude CLI once to generate daily report
- **Prompt** (`scripts/prompts/daily-report.md`): Controls how Claude generates the report

## Reporting Issues

- Use the [issue templates](.github/ISSUE_TEMPLATE/) when available
- Include steps to reproduce for bug reports
- For feature requests, describe the use case and expected behavior

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
