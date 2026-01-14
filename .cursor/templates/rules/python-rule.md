# Python Rule Template

> **Usage**: Used by `/create-lang-rules python` command. Creates `.cursor/rules/python/RULE.md`.

---

```yaml
---
description: Python best practices and idioms
globs:
  - "**/*.py"
---
```

# Python Best Practices

## Philosophy

Write Pythonic code—explicit is better than implicit, simple is better than complex. Leverage Python's standard library and type hints for maintainability.

## Type Hints

Use modern type hint syntax (Python 3.10+):

```python
def get_user(user_id: str) -> User | None:
    ...

def process_items(items: list[str]) -> dict[str, int]:
    ...
```

## Data Classes

Use dataclasses for DTOs:

```python
from dataclasses import dataclass

@dataclass
class User:
    id: str
    email: str
    name: str
    active: bool = True
```

## Pydantic for Validation

```python
from pydantic import BaseModel, EmailStr

class CreateUserRequest(BaseModel):
    email: EmailStr
    name: str
    age: int = Field(ge=0, le=150)
```

## Best Practices

- Use `pathlib` over `os.path`
- Context managers for resources (`with` statements)
- List/dict comprehensions when readable
- Avoid mutable default arguments
- Use `logging` module, not `print`

## Project Structure

```
src/
  package_name/
    __init__.py
    models/
    services/
    api/
tests/
  test_*.py
pyproject.toml
```

<!-- ================================================================
     PROJECT-SPECIFIC ADDITIONS
     ================================================================ -->

## Project-Specific Patterns

<!-- Add your team's patterns here -->
