## Language Rules

- **AGENTS.md**: Write in English.
- **documentation**: Write in Japanese.
- **User interaction**: Respond in Japanese.
- **Code comments**: Write in Japanese.
- **Agent prompt**: Write in Japanese.

## Accuracy and Verification

- Prioritize accurate, verifiable answers over agreeing with the user.
- Do not flatter, appease, or agree for the sake of agreement. Be respectful, direct, and evidence-based.
- Do not state guesses or assumptions as if they were facts.
- Distinguish between facts, inferences, and assumptions.
- Make uncertainty explicit when the supporting evidence is weak.
- When a user's premise appears to be wrong, point it out with the reasoning behind it.
- If you don't know something, say so.
- Verify to the extent possible before claiming success, completion, or certainty.

## Python / uv

This project uses [uv](https://docs.astral.sh/uv/) for Python package management. Python 3.14+.

```bash
uv sync                   # Install dependencies from pyproject.toml / uv.lock
uv run python <script>    # Run a script in the managed environment
uv add <package>          # Add a dependency
uv add --group dev <pkg>  # Add a dev dependency
```

## Commit Messages

- Write in English, 1–2 concise sentences focusing on "why" not "what".
- Keep commits focused by coherent feature or fix. When changes span multiple files, include only files that belong to the same functional unit in a commit.
- Split unrelated file changes into separate commits, even if they were made during the same working session.
- When AI tools (e.g., Claude Code, Codex) create commits, include a `Co-Authored-By` trailer.

## Pull Requests

- When creating a pull request, create it as a draft, follow `.github/pull_request_template.md`, and write the title and body in Japanese.

## Code Quality

- Write simple, direct code. Avoid redundant code, overly broad tests, premature abstractions, and unnecessary helper functions.
- Run `task fmt` before committing. (formatting + linting)
- Run `task ty` to check types.
- Run `task test` to run the test suite.
- Always run `task pre-commit` before creating a commit.

## Code Comment Style

- Keep comments simple and plain. No decorative banners (`# === ... ===`, `# --- ... ---`, `# *** ... ***`, etc.).
- Do not comment what is obvious from reading the code. Only add comments when the reason behind the code is non-obvious.
- Use `# NOTE:` to explain _why_ a non-obvious implementation choice was made.
- Use `# TODO:` for work that remains to be done.
- Do not pad comments with extra lines. Keep them as few lines as the content needs.
- Do not break lines at arbitrary or mechanical points (e.g. hard-wrapping at a fixed column width), in comments and documents alike. A somewhat long line is fine; break only where the meaning naturally pauses, such as the end of a sentence or clause boundaries (commas, periods, or their Japanese equivalents `、` and `。`).
