---
id: chunk-003
source: python-best-practices.md
topic: Testing Strategy
keywords: [pytest, unit tests, integration tests, Hypothesis, property-based testing, parametrize]
summary: "Structure tests as unit, integration, and property-based layers using pytest and Hypothesis, focusing on testing behavior rather than implementation for meaningful coverage."
---

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
