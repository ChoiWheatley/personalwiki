---
{"dg-publish":true,"permalink":"/docs/dataclass ValueError mutable default class list is not allowed, use default_factory {python}/","title":"dataclass ValueError mutable default class list is not allowed, use default_factory {python}"}
---

원인 코드

```python
@dataclass
class Node:
    idx: int
    children: List[Self] = []
    parent: Self | None = None
```

에러메시지

```
ValueError: mutable default <class 'list'> for field children is not allowed: use default_factory
```

[해결방법 {sof}](https://stackoverflow.com/a/63231305/21369350)

```python
from dataclasses import dataclass, field
from typing import Dict

@dataclass
class Test:
    foo: Dict[str, int] = field(default_factory=dict)
    bar: Dict[str, float] = field(default_factory=lambda: {'blah': 2.0})
```
