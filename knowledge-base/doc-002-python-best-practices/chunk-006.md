---
id: chunk-006
source: python-best-practices.md
topic: Async Programming
keywords: [asyncio, async/await, concurrency, httpx, TaskGroup, event loop]
summary: "Use asyncio with async/await for I/O-bound concurrency, prefer httpx and async DB drivers, use TaskGroup for structured concurrency, and offload CPU-bound work to threads or processes."
---

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
