---
{"dg-publish":true,"permalink":"/docs/counter가 뭐지 - python/","title":"counter가 뭐지 - python"}
---


```python
from collections import Counter

def solution(array, n):
    value = Counter(array).get(n)
    return 0 if value == None else value
```
