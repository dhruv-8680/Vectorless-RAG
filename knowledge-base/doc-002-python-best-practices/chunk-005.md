---
id: chunk-005
source: python-best-practices.md
topic: Dependency Management
keywords: [uv, pyproject.toml, dependency pinning, virtualenv, pip]
summary: "Use uv for fast dependency management, pin exact versions in uv.lock for applications, use compatible release specifiers for libraries, and keep dev dependencies separate."
---

## Dependency Management

Use **uv** for dependency management — it's the modern replacement for pip, pip-tools, and virtualenvs. It's written in Rust and is extremely fast.

Project setup with uv:

```bash
uv init my-project
cd my-project
uv add requests pydantic
uv add --dev pytest mypy ruff
```

Key practices:
- Pin exact versions in `uv.lock` (generated automatically) for reproducibility
- Use `pyproject.toml` as the single source of truth for project metadata and dependencies
- Separate dev dependencies from production dependencies
- Regularly update dependencies: `uv lock --upgrade`
- Audit dependencies for known vulnerabilities

For applications (not libraries), pin exact versions. For libraries, use compatible release specifiers: `requests >= 2.28, < 3`.
