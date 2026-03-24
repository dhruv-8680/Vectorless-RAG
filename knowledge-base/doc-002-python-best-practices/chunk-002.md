---
id: chunk-002
source: python-best-practices.md
topic: Type Hints and Static Analysis
keywords: [type hints, mypy, static analysis, TypeVar, Protocol, TypedDict]
summary: "Use modern Python 3.10+ type hint syntax and run mypy in strict mode, leveraging patterns like Protocol for duck typing and TypedDict for structured dictionaries."
---

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
