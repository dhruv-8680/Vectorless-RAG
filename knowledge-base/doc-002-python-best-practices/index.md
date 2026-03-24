# Python Best Practices for Production Code — Index

## Code Style and Formatting
- **chunk-001.md** | Keywords: PEP 8, Black, Ruff, isort, naming conventions, code formatting | "Use Black for formatting, Ruff for linting, and isort for imports, following PEP 8 naming conventions like snake_case for functions and PascalCase for classes."

## Type Hints and Static Analysis
- **chunk-002.md** | Keywords: type hints, mypy, static analysis, TypeVar, Protocol, TypedDict | "Use modern Python 3.10+ type hint syntax and run mypy in strict mode, leveraging patterns like Protocol for duck typing and TypedDict for structured dictionaries."

## Testing Strategy
- **chunk-003.md** | Keywords: pytest, unit tests, integration tests, Hypothesis, property-based testing, parametrize | "Structure tests as unit, integration, and property-based layers using pytest and Hypothesis, focusing on testing behavior rather than implementation for meaningful coverage."

## Error Handling
- **chunk-004.md** | Keywords: exceptions, error handling, context managers, custom exceptions, logging | "Catch specific exception types, build custom exception hierarchies, use context managers for resource cleanup, and always log exceptions rather than swallowing them."

## Dependency Management
- **chunk-005.md** | Keywords: uv, pyproject.toml, dependency pinning, virtualenv, pip | "Use uv for fast dependency management, pin exact versions in uv.lock for applications, use compatible release specifiers for libraries, and keep dev dependencies separate."

## Async Programming
- **chunk-006.md** | Keywords: asyncio, async/await, concurrency, httpx, TaskGroup, event loop | "Use asyncio with async/await for I/O-bound concurrency, prefer httpx and async DB drivers, use TaskGroup for structured concurrency, and offload CPU-bound work to threads or processes."

## Configuration Management
- **chunk-007.md** | Keywords: Pydantic Settings, environment variables, secrets, configuration, dotenv | "Use a layered configuration approach with Pydantic Settings to combine defaults, config files, and environment variables with type validation, and never commit secrets to version control."
