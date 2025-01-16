---
{"dg-publish":true,"permalink":"/docs/check every element from sequence is same {python} {functools.reduce}/","title":"check every element from sequence is same {python} {functools.reduce}"}
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
