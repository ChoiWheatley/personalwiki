---
{"dg-publish":true,"permalink":"/docs/deep copy and shallow copy - python/","title":"deep copy and shallow copy - python"}
---


# Deep Copy & Shallow Copy

```python
# 얕은복사 => 0-depth value copy
l = [[1,2,3],[4,5,6]]
ll = l[:]
assert id(l) != id(ll)
assert id(l[0]) == id(ll[0])

# 깊은복사 => N-depth recursive value copy
from copy import deepcopy
l = [[1,2,3],[4,5,6]]
ll = deepcopy(l)
assert id(l) != id(ll)
assert id(l[0]) != id(ll[0])
```
