---
{"dg-publish":true,"permalink":"/docs/Custom Comparable type {python} using `__lt__`/","title":"Custom Comparable type {python} using `__lt__`"}
---

- [sof](https://stackoverflow.com/questions/37669222/how-can-i-hint-that-a-type-is-comparable-with-typing)
- [[docs/dataclasses - python -- custom comparator\|dataclasses - python -- custom comparator]]도 참고해 보세요

```python
from abc import ABCMeta, abstractmethod
from typing import Any, TypeVar

class Comparable(metaclass=ABCMeta):
    @abstractmethod
    def __lt__(self, other: Any) -> bool: ...

CT = TypeVar('CT', bound=Comparable)
```
