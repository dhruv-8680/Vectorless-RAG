---
id: chunk-001
source: python-best-practices.md
topic: Code Style and Formatting
keywords: [PEP 8, Black, Ruff, isort, naming conventions, code formatting]
summary: "Use Black for formatting, Ruff for linting, and isort for imports, following PEP 8 naming conventions like snake_case for functions and PascalCase for classes."
---

## Code Style and Formatting

Consistent code style makes codebases maintainable and readable. Python's PEP 8 is the de facto style guide, and modern tools enforce it automatically.

Use **Black** for code formatting — it's opinionated and eliminates style debates. Configure it in `pyproject.toml` with a line length of 88 (Black's default) or 120 if your team prefers longer lines. Pair it with **isort** for import ordering, configured to be compatible with Black.

Use **Ruff** as your linter — it's written in Rust and replaces flake8, pylint, and many other tools. It's orders of magnitude faster and supports auto-fixing. A minimal Ruff configuration:

```toml
[tool.ruff]
target-version = "py311"
line-length = 88
select = ["E", "F", "I", "N", "W", "UP", "B", "SIM"]
```

Naming conventions to follow:
- `snake_case` for functions, methods, variables, and modules
- `PascalCase` for classes
- `UPPER_SNAKE_CASE` for constants
- Prefix private attributes with a single underscore: `_internal_state`
- Avoid double underscore name mangling unless absolutely necessary
