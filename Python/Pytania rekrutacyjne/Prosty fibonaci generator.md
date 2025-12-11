```python
from typing import Iterator


def fibonacci_generator(iteration: int) -> Iterator:
    a, b = 0, 1

    for _ in range(iteration):
        yield a
        a, b = b, a + b
```