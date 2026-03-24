---
id: chunk-004
source: python-best-practices.md
topic: Error Handling
keywords: [exceptions, error handling, context managers, custom exceptions, logging]
summary: "Catch specific exception types, build custom exception hierarchies, use context managers for resource cleanup, and always log exceptions rather than swallowing them."
---

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
