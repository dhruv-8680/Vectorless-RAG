---
id: chunk-007
source: python-best-practices.md
topic: Configuration Management
keywords: [Pydantic Settings, environment variables, secrets, configuration, dotenv]
summary: "Use a layered configuration approach with Pydantic Settings to combine defaults, config files, and environment variables with type validation, and never commit secrets to version control."
---

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
