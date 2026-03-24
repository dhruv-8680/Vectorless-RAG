# Python Best Practices for Production Code

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

## Type Hints and Static Analysis

Type hints dramatically improve code quality by catching bugs before runtime and serving as living documentation. Since Python 3.10+, you can use the modern syntax:

```python
def process_items(items: list[str], max_count: int = 10) -> dict[str, int]:
    ...
```

Use **mypy** in strict mode for type checking. Key settings in `pyproject.toml`:

```toml
[tool.mypy]
python_version = "3.11"
strict = true
warn_return_any = true
disallow_untyped_defs = true
```

Important type hint patterns:
- Use `Optional[X]` or `X | None` for values that may be None
- Use `TypeVar` for generic functions that preserve input types
- Use `Protocol` for structural subtyping (duck typing with type safety)
- Use `TypedDict` for dictionaries with known key schemas
- Use `Literal["a", "b"]` to restrict string values to specific options

For complex types, define type aliases at the module level:

```python
type UserID = int
type UserMap = dict[UserID, "User"]
```

## Testing Strategy

A good test suite is your safety net for refactoring and adding features. Structure tests in a hierarchy:

**Unit tests** form the base — they test individual functions and classes in isolation. Use **pytest** as your testing framework. Key practices:
- One assertion per test when practical (makes failures clear)
- Use `pytest.fixture` for setup/teardown
- Use `pytest.mark.parametrize` for testing multiple inputs
- Name tests descriptively: `test_parse_date_returns_none_for_invalid_format`

**Integration tests** verify that components work together correctly. These might involve real database connections, file system operations, or HTTP calls to staging APIs. Keep them separate from unit tests using pytest markers:

```python
@pytest.mark.integration
def test_user_creation_persists_to_database(db_session):
    user = create_user(db_session, name="Alice")
    fetched = get_user(db_session, user.id)
    assert fetched.name == "Alice"
```

**Property-based testing** with **Hypothesis** finds edge cases you wouldn't think of:

```python
from hypothesis import given, strategies as st

@given(st.lists(st.integers()))
def test_sort_is_idempotent(xs):
    assert sorted(sorted(xs)) == sorted(xs)
```

Aim for meaningful coverage, not 100% line coverage. Test behavior, not implementation. If a refactor breaks your tests but not your functionality, your tests are too tightly coupled.

## Error Handling

Python's exception system is powerful but easily misused. Follow these principles:

**Be specific with exceptions**: Catch the narrowest exception type possible. Never use bare `except:` or `except Exception:` unless you're at the top-level error boundary.

```python
# Bad
try:
    value = data[key]
except:
    value = default

# Good
try:
    value = data[key]
except KeyError:
    value = default
```

**Create custom exception hierarchies** for your application:

```python
class AppError(Exception):
    """Base exception for the application."""

class ValidationError(AppError):
    """Raised when input validation fails."""

class NotFoundError(AppError):
    """Raised when a requested resource doesn't exist."""
```

**Use context managers** for resource cleanup instead of try/finally:

```python
from contextlib import contextmanager

@contextmanager
def database_transaction(connection):
    try:
        yield connection
        connection.commit()
    except Exception:
        connection.rollback()
        raise
```

**Log exceptions properly**: Use `logger.exception()` inside except blocks — it automatically includes the traceback. Don't silently swallow exceptions; at minimum, log them.

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

## Async Programming

Python's `asyncio` enables concurrent I/O operations without threads. Use it when your application is I/O-bound (HTTP requests, database queries, file operations).

Basic async pattern:

```python
import asyncio
import httpx

async def fetch_urls(urls: list[str]) -> list[str]:
    async with httpx.AsyncClient() as client:
        tasks = [client.get(url) for url in urls]
        responses = await asyncio.gather(*tasks)
        return [r.text for r in responses]
```

Key principles:
- Use `async/await` throughout — don't mix sync and async code without proper bridges
- Use `asyncio.gather()` for running multiple coroutines concurrently
- Use `asyncio.TaskGroup` (Python 3.11+) for structured concurrency with better error handling
- Use `httpx` instead of `requests` for async HTTP calls
- Use async database drivers (asyncpg, motor) for async DB operations

**Common pitfalls to avoid:**
- Running CPU-bound work in async functions (blocks the event loop)
- Not awaiting coroutines (they won't execute)
- Using `asyncio.sleep()` as a substitute for proper synchronization
- Creating too many concurrent tasks without limiting with semaphores

For CPU-bound work inside async applications, use `asyncio.to_thread()` or `ProcessPoolExecutor` to offload to separate threads/processes.

## Configuration Management

Never hardcode configuration values. Use a layered configuration approach:

1. **Default values** in code
2. **Configuration files** (TOML or YAML) for environment-specific settings
3. **Environment variables** for secrets and deployment-specific overrides

Use **Pydantic Settings** for configuration management:

```python
from pydantic_settings import BaseSettings

class Settings(BaseSettings):
    database_url: str
    api_key: str
    debug: bool = False
    max_retries: int = 3

    model_config = ConfigDict(env_prefix="APP_")

settings = Settings()
```

This gives you type validation, environment variable loading, and sensible defaults all in one place. Never commit secrets to version control — use `.env` files locally and proper secret management (AWS Secrets Manager, Vault) in production.
