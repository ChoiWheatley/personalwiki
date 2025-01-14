---
{"aliases":null,"tags":null,"description":null,"title":"check every element from sequence is same {python} {functools.reduce}","created":"2023-08-13T16:36:38","updated":"2023-08-15T21:02:47","dg-publish":true,"permalink":"/docs/check every element from sequence is same {python} {functools.reduce}/","dgPassFrontmatter":true}
---


## 0번째 아이템을 기준으로 `all`

```python
all(x == items[0] for x in items)
```

## deprecated

항상 작동하지 않는다는 문제 발생

```python
from functools import reduce

seq = [1,1,1,1,1,1,1,1,1,1]
reduce(lambda x, y: x == y, seq)
```
